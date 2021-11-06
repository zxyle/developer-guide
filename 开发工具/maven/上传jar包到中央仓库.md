
## 注册账号
网址: https://issues.sonatype.org/login.jsp

## 配置GPG
参考该目录下 另外一篇笔记

## 创建工单
- 打开  https://issues.sonatype.org/secure/Dashboard.jspa
- 点击导航栏 **新建**
- 项目选择 **Community Support - Open...**
- 问题类型 选择**新建项目**
- 概要填写 **Create and upload new project**
- Group Id填写域名反写 或者 `io.github.username`
- Project URL 填写 `https://github.com/zxyle/fullstack`
- SCM url 填写 `https://github.com/zxyle/fullstack.git`

## 验证域名或仓库
- 根据要求创建对应的github仓库
- 或者验证域名

## 配置maven settings.xml
```xml
<servers>
    <server>
        <id>sonatype-nexus-snapshots</id>
        <username>上述账号名</username>
        <password>上述密码</password>
    </server>

    <server>
        <id>sonatype-nexus-staging</id>
        <username>上述账号名</username>
        <password>上述密码</password>
    </server>
</servers>
```

## 配置pom文件
version标签下增加
```xml
<name>fullstack</name>
<description>fullstack toolkit</description>
<url>https://github.com/zxyle/fullstack</url>
```

dependencies标签下增加
```xml
<!-- 许可证信息 -->
<licenses>
    <!-- Apache许可证 -->
    <license>
        <name>The Apache Software License, Version 2.0</name>
        <url>https://www.apache.org/licenses/LICENSE-2.0.txt</url>
    </license>
    <!-- MIT许可证 -->
    <!--	<license>
            <name>MIT License</name>
            <url>https://www.opensource.org/licenses/mit-license.php</url>
        </license>-->
</licenses>
<!-- SCM信息 -> git在github上托管 -->
<scm>
    <connection>scm:git:git://github.com/zxyle/OSSRH-73432.git</connection>
    <developerConnection>scm:git:ssh://github.com/zxyle/OSSRH-73432.git</developerConnection>
    <url>https://github.com/zxyle/OSSRH-73432/tree/master</url>
</scm>
<!-- 开发者信息 -->
<developers>
    <developer>
        <name>zhengxiang</name>
        <email>zxyful@gmail.com</email>
        <url>https://github.com/zxyle</url>
    </developer>
</developers>

<!-- 使用个人资料：由于生成javadoc和源jar以及使用GPG签署组件是一个相当耗时的过程，因此这些执行通常与正常的构建配置隔离并移动到配置文件中。然后，在通过激活配置文件执行部署时，将使用此配置文件。 -->
<profiles>
    <profile>
        <id>ossrh</id>
        <activation>
            <activeByDefault>true</activeByDefault>
        </activation>
        <build>
            <plugins>
                <!-- 要生成Javadoc和Source jar文件，您必须配置javadoc和源Maven插件 -->
                <plugin>
                    <groupId>org.apache.maven.plugins</groupId>
                    <artifactId>maven-source-plugin</artifactId>
                    <version>2.2.1</version>
                    <executions>
                        <execution>
                            <id>attach-sources</id>
                            <goals>
                                <goal>jar-no-fork</goal>
                            </goals>
                        </execution>
                    </executions>
                </plugin>
                <plugin>
                    <groupId>org.apache.maven.plugins</groupId>
                    <artifactId>maven-javadoc-plugin</artifactId>
                    <version>2.9.1</version>
                    <executions>
                        <execution>
                            <id>attach-javadocs</id>
                            <goals>
                                <goal>jar</goal>
                            </goals>
                        </execution>
                    </executions>
                </plugin>
                <!--  必须配置GPG插件用于使用以下配置对组件进行签名 -->
                <plugin>
                    <groupId>org.apache.maven.plugins</groupId>
                    <artifactId>maven-gpg-plugin</artifactId>
                    <version>1.5</version>
                    <executions>
                        <execution>
                            <id>sign-artifacts</id>
                            <phase>verify</phase>
                            <goals>
                                <goal>sign</goal>
                            </goals>
                        </execution>
                    </executions>
                </plugin>
            </plugins>
        </build>
        <!-- 【注】snapshotRepository 与 repository 中的 id 一定要与 setting.xml 中 server 的 id 保持一致！ -->
        <distributionManagement>
            <snapshotRepository>
                <id>sonatype-nexus-snapshots</id>
                <url>https://s01.oss.sonatype.org/content/repositories/snapshots</url>
            </snapshotRepository>
            <repository>
                <id>sonatype-nexus-staging</id>
                <url>https://s01.oss.sonatype.org/service/local/staging/deploy/maven2/</url>
            </repository>
        </distributionManagement>
    </profile>
</profiles>
```


## 上传
```
mvn clean deploy -P sonatype-oss-release
```

## 发布
- 打开 https://s01.oss.sonatype.org/
- 使用上述账号密码登录
- 点击左侧 **Staging Repositories**
- 选择点击 **Clone**
- 稍后 再次点击**Release**
- 如果上传错误，就点击**Drop**，然后重新上传

## 验证和查看
- https://search.maven.org/
- https://repo1.maven.org/maven2/
- https://mvnrepository.com/

> 通常需要等待2~3小时

## 参考文档
- https://central.sonatype.org/publish/publish-maven/
- https://docs.github.com/cn/actions/guides/publishing-java-packages-with-maven