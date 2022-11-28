# 目录相关

```shell
# 查看
ls -l
ls -a
# 切换
cd
# 打印
pwd
# 创建删除目录
mkdir
# 创建文件
touch
# 生效文件
source
# 复制文件或目录
cp
# 移动 and 改名
mv
# 强制删除
rm -rf
```

# 解压

```shell
# 解压
tar -zxvf rumenz.tar.gz
# 压缩
tar -zcvf rumenz.tar.gz rumenz.txt
```

# 进程

```shell
# 查看端口
lsof -i:端口号
# 知道端口 
ps -elf | grep 端口号  
ps -aux | grep 端口号
netstat -nltp|grep 端口号
# 查看进程运行情况
top
# 查看进程中所有线程运行情况
top -pid 进程号
# 杀死进程
Kill -9 进程号
```

# 日志

```shell
# 实时查看日志
tail -f test.log
# 实时查看异常日志
tail -f test.log | grep 'exception'
# 过滤
cat test.log | grep "http" | grep -v "ignore"
```

# 服务

```shell
# 开启服务
systemctl start 服务名
# 关闭服务
systemctl stop 服务名 
# 重启服务
systemctl restart 服务名 
# 查看服务状态
systemctl status 服务名 
```

# vim

```shell
# esc 命令模式
dd 删除当前行
yy 复制当前行
p 粘贴
# ： 底行模式
:q 退出
:wq 保存退出
:wq! 强制保存退出
:set number 显示行号
/<name> 搜索
```