

## 图形验证码

- https://code.google.com/archive/p/kaptcha/downloads
- https://code.google.com/archive/p/patchca/



## 安装到本地仓库

```bash
mvn install:install-file -DgroupId=com.google.code -DartifactId=kaptcha -Dversion=2.3.2 -Dfile=kaptcha-2.3.2.jar -Dpackaging=jar -DgeneratePom=true

mvn install:install-file -DgroupId=org.patchca -DartifactId=patchca -Dversion=0.5.0 -Dfile=patchca-0.5.0.jar -Dpackaging=jar -DgeneratePom=true
```

