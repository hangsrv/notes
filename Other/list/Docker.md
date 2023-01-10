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
# 基础镜像使用
FROM ubuntu:16.04
# 作者
MAINTAINER hang
# 配置环境变量
ENV JAVA_DIR=/usr/local
# jar包
COPY ./jdk-8u202.tar.gz $JAVA_DIR/
# 安装JDK
RUN cd $JAVA_DIR \
  && tar -zxvf ./jdk-8u202.tar.gz \
  && mv ./jdk1.8.0_202 ./java8
# 配置环境变量
ENV JAVA_HOME=$JAVA_DIR/java8
ENV PATH=$PATH:$JAVA_HOME/bin
# 拷贝项目
COPY ./health_backend/target/health_backend-1.0-SNAPSHOT.jar /tmp/health_backend.jar
COPY ./health_service_provider/target/health_service_provider-1.0-SNAPSHOT.jar /tmp/health_service_provider.jar
COPY ./health_mobile/target/health_mobile-1.0-SNAPSHOT.jar /tmp/health_mobile.jar
COPY ./start.sh /tmp/start.sh
# 赋予文件权限并运行start.sh脚本
RUN chmod +x /tmp/start.sh
ENTRYPOINT ["sh","/tmp/start.sh"]
# 暴露端口
EXPOSE 80
EXPOSE 81
EXPOSE 82
```

```shell
#!/bin/sh
nohup java -jar /tmp/health_backend.jar  > /tmp/health_backend.log &
nohup java -jar /tmp/health_service_provider.jar  > /tmp/health_service_provider.log &
nohup java -jar /tmp/health_mobile.jar  > /tmp/health_mobile.log
```

# docker-compose

```yaml
version: '3'
services:
  health-redis:
    image: redis
    container_name: health-redis
    network_mode: bridge
    hostname: health-redis
    ports:
      - 6379:6379
  health-mysql:
    image: mysql
    container_name: health-mysql
    network_mode: bridge
    volumes:
      - ./health.sql:/docker-entrypoint-initdb.d/init.sql
    ports:
      - 3306:3306
    environment:
      - "MYSQL_ROOT_PASSWORD=123456"
  health-zookeeper:
    image: zookeeper
    container_name: health-zookeeper
    network_mode: bridge
    ports:
      - 2181:2181
  health-web:
    network_mode: bridge
    container_name: health-web
    build: .
    ports:
      - 80:80
      - 82:82
    depends_on:
      - health-redis
      - health-mysql
      - health-zookeeper
```
