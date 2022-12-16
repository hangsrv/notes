# 常用命令

```shell
# 镜像相关
docker images
docker rmi -f <name>

# 容器相关
docker ps -a
docker rm -f <name>

# 创建运行容器
docker run -it --name <name> -p <port>:<docker port> -v <file>:<docker file> <image> /bin/bash
docker run -id --name <name> -p <port>:<docker port> -v <file>:<docker file> <image> 
docker exec -it <name> /bin/bash
docker stop <name>

# 网络相关 host bridge none
docker network ls
docker network inspect <name>
docker network rm <name>
docker network create <name>

# 容器打包镜像
docker commit A B
```

# dockerfile

## 基本指令

FROM：指定基础镜像

ENV：设置环境变量

COPY：拷贝本地文件到容器

RUN：执行Linux的shell命令

EXPOSE：指定容器运行时暴露的端口

ENTRYPOINT：镜像中应用的启动命令，运行时调用

## 使用案例

```shell
# 指定基础镜像
FROM ubuntu:16.04
# 配置环境变量
ENV JAVA_DIR=/usr/local
# 拷贝文件
COPY ./jdk8.tar.gz $JAVA_DIR/
COPY ./demo.jar /tmp/app.jar
# 安装JDK
RUN cd $JAVA_DIR \
  && tar -xf ./jdk8.tar.gz \
  && mv ./jdk1.8.0_144 ./java8
# 配置环境变量
ENV JAVA_HOME=$JAVA_DIR/java8
ENV PATH=$PATH:JAVA_HOME/bin
# 暴露端口
EXPOSE 8080
# 启动
ENTRYPOINT java -jar /tmp/app.jar
```

# docker-compose

```yaml
version: '3'
services:

  redis:
    container_name: redis
    image: redis
    ports:
      - 6379:6379
  mysql:
    container_name: mysql
    image: mysql
    ports:
      - 3306:3306
    environment:
      - "MYSQL_ROOT_PASSWORD=123456"
  rabbitmq:
    container_name: rabbitmq
    image: rabbitmq:management
    ports:
      - 5672:5672
      - 15672:15672
    environment:
      RABBITMQ_DEFAULT_USER: rabbit
      RABBITMQ_DEFAULT_PASS: 123456
```
