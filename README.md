hello spring

## 打包执行
### 打包
mvn package
### 执行
#### 方式1：     
使用`maven-jar-plugin`在MANIFEST.MF中生成主类和classpath清单：      
```xml
<plugin>
  <groupId>org.apache.maven.plugins</groupId>
  <artifactId>maven-jar-plugin</artifactId>
  <version>3.2.2</version>
  <configuration>
    <archive>
      <manifest>
        <addClasspath>true</addClasspath>
        <classpathPrefix>lib/</classpathPrefix>
        <mainClass>com.itranswarp.learnjava.Main</mainClass>
      </manifest>
    </archive>
  </configuration>
</plugin>
```
META_IF/MANIFEST.MF:
```txt
Manifest-Version: 1.0
Created-By: Maven JAR Plugin 3.2.2
Build-Jdk-Spec: 17
Class-Path: lib/spring-context-6.0.0.jar lib/spring-aop-6.0.0.jar lib/sp
 ring-beans-6.0.0.jar lib/spring-core-6.0.0.jar lib/spring-jcl-6.0.0.jar
  lib/spring-expression-6.0.0.jar
Main-Class: com.itranswarp.learnjava.Main
```
执行时：`java -jar spring-ioc-appcontext-1.0-SNAPSHOT.jar`

#### 方式2：
不使用`maven-jar-plugin`, 生成的META_IF/MANIFEST.MF如下：       
```txt
Manifest-Version: 1.0
Created-By: Maven JAR Plugin 3.3.0
Build-Jdk-Spec: 17
```
执行时需要指定classpath：`java -cp target/spring-ioc-appcontext-1.0-SNAPSHOT.jar:target/lib/\* com.itranswarp.learnjava.Main `