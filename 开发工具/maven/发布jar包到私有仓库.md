## 打开网址

https://packages.aliyun.com/maven



## 修改.m2/settings.xml文件

在servers标签中添加

```xml
<server>
    <id>rdc-releases</id>
    <username>614c0cb18c92f81097fe26dc</username>
    <password>UwuS3Wn9xCtx</password>
</server>
<server>
    <id>rdc-snapshots</id>
    <username>614c0cb18c92f81097fe26dc</username>
    <password>UwuS3Wn9xCtx</password>
</server>
```



在mirrors标签中添加:

```xml
<mirror>
    <id>mirror</id>
    <mirrorOf>central,jcenter,!rdc-releases,!rdc-snapshots</mirrorOf>
    <name>mirror</name>
    <url>https://maven.aliyun.com/nexus/content/groups/public</url>
</mirror>
```



在profiles标签中添加:

```xml
<profile>
    <id>rdc</id>
    <properties>
        <altReleaseDeploymentRepository>
            rdc-releases::default::https://packages.aliyun.com/maven/repository/2206926-release-1bcXWd/
        </altReleaseDeploymentRepository>
        <altSnapshotDeploymentRepository>
            rdc-snapshots::default::https://packages.aliyun.com/maven/repository/2206926-snapshot-jgDuLy/
        </altSnapshotDeploymentRepository>
    </properties>
    <repositories>
        <repository>
            <id>rdc-releases</id>
            <url>https://packages.aliyun.com/maven/repository/2206926-release-1bcXWd/</url>
            <releases>
                <enabled>true</enabled>
            </releases>
            <snapshots>
                <enabled>false</enabled>
            </snapshots>
        </repository>
        <repository>
            <id>rdc-snapshots</id>
            <url>https://packages.aliyun.com/maven/repository/2206926-snapshot-jgDuLy/</url>
            <releases>
                <enabled>false</enabled>
            </releases>
            <snapshots>
                <enabled>true</enabled>
            </snapshots>
        </repository>
    </repositories>
</profile>
```



激活:

```xml
<activeProfiles>
    <activeProfile>rdc</activeProfile>
</activeProfiles>
```





## 修改maven工程pom文件

```xml
<build>
    <plugins><!-- 要生成Javadoc和Source jar文件，您必须配置javadoc和源Maven插件 -->
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
            <configuration>
                <source>8</source>
            </configuration>
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
    </plugins>
</build>
```



## 发布

```shell
mvn clean install org.apache.maven.plugins:maven-deploy-plugin:2.8:deploy -DskipTests
```

