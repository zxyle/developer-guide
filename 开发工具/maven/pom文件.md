
## 最基本配置
```xml
<properties>
    <java.version>8</java.version>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    <maven.compiler.source>${java.version}</maven.compiler.source>
    <maven.compiler.target>${java.version}</maven.compiler.target>
    <maven.compiler.compilerVersion>${java.version}</maven.compiler.compilerVersion>
</properties>
```





## 配置mirror

```xml
<repositories>
  <repository>
    <id>nexus-163</id>
    <name>Nexus 163</name>
    <url>https://mirrors.163.com/maven/repository/maven-public/</url>
    <layout>default</layout>
    <snapshots>
      <enabled>false</enabled>
    </snapshots>
    <releases>
      <enabled>true</enabled>
    </releases>
  </repository>
</repositories>
<pluginRepositories>
  <pluginRepository>
    <id>nexus-163</id>
    <name>Nexus 163</name>
    <url>https://mirrors.163.com/maven/repository/maven-public/</url>
    <snapshots>
      <enabled>false</enabled>
    </snapshots>
    <releases>
      <enabled>true</enabled>
    </releases>
  </pluginRepository>
</pluginRepositories>
```

