# 基本配置

- setting.xml

```text
<mirrors>
    <mirror>
        <id>alimaven</id>
        <mirrorOf>central</mirrorOf>
        <name>aliyun maven</name>
        <url>http://maven.aliyun.com/nexus/content/groups/public/</url>
    </mirror>
</mirrors>

<profiles>
    <profile>
        <id>jdk1.8</id>
        <activation>
            <activeByDefault>true</activeByDefault>
            <jdk>1.8</jdk>
        </activation>
        <properties>
            <maven.compiler.source>1.8</maven.compiler.source>
            <maven.compiler.target>1.8</maven.compiler.target>
            <maven.compiler.compilerVersion>1.8</maven.compiler.compilerVersion>
        </properties>
    </profile>
</profiles>
```

# 常用命令

```shell
# 查看版本
mvn -v
# 清理项目
mvn clean
# 编译
mvn compile
mvn test-compile
# 打包
mvn package
mvn package -Dmaven.test.skip=true
java -jar App.jar
# 安装
mvn install
mvn install -Dmaven.test.skip=true
# 部署
mvn deploy
mvn deploy -Dmaven.test.skip=true
```