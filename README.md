# notes

个人笔记归档迁移

doing
* Netty
  + 学习：https://dongzl.github.io/netty-handbook/#/
* 数据结构与算法
  + 学习：https://sp18.datastructur.es/
  + 练习：https://github.com/PKUFlyingPig/CS61B
* 操作系统
  + 学习：https://mit-public-courses-cn-translatio.gitbook.io/mit6-s081/

todo基础
* 计算机网络
* 数据库
* 分布式系统：https://mit-public-courses-cn-translatio.gitbook.io/mit6-824/

todo自学
* Spring
* MyBatis
* SpringBoot
* SpringCloud
* Kafka
* ElasticSearch
* MySQL
* Redis

server、client
router
client status

1. TCP or UDP
2. 黏包 和 粘包问题
3. 消息ID redis自增（uid、gid）
4. 序列化协议：JSON、protobuf
5. 心跳保活：NAT超时、网络状态切换、DHCP租期到期  启动一个定时任务 定时发送消息 定时器重置 消息发送失败
6. 好友状态：正向好友信息 反向好友信息 server主动通知client 群聊采用pull的模式
7. 消息传递：写扩散 读扩散 群聊消息合并推送 bitmap实现消息已读 定时批量ack消息
