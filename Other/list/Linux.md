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
# 设置密码
passwd
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
/<name> 搜索  n:查找下一项
```

# ssh

```shell
# 配置密码 passwd
vim /etc/ssh/sshd_config
/etc/init.d/ssh stop
/etc/init.d/ssh start

# 登陆
ssh -p port username@host

# 端口转发
ssh -L localPort:remoteHost:remotePort -p localport username@localHost
```

## 常见工具

* shell

```shell
cat /etc/shells

chsh -s /bin/zsh
```

* python

```shell
python3 -m http.server <port>
python -m SimpleHTTPServer <port>
```

* iterm2

```shell
# 安装 iterm2 & ranger
brew install ranger

# 安装 oh-my-zsh
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
# 终端代码提示
git clone https://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
# 主题
git clone --depth=1 https://gitee.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k

# 修改配置文件
vim ~/.zshrc
ZSH_THEME="powerlevel10k/powerlevel10k"
plugins=(zsh-autosuggestions git)
POWERLEVEL9K_DISABLE_CONFIGURATION_WIZARD=true

alias code="'/Applications/Visual Studio Code.app/Contents/Resources/app/bin/code'"
alias gs="git status "
alias gc="git add . && git commit -am "

# 设置字体
Preferences -> Profiles -> Text -> Use built-in Powerline glyphs

# session bar
Appearance -> General -> Theme -> Minimal
Profiles -> Session -> Status bar enabled

# image
Profiles -> Window -> Backgroud Image
```

* vim

```shell
# 创建
mkdir -p ~/.vim/pack/themes/start
cd ~/.vim/pack/themes/start
# 下载
git clone https://github.com/dracula/vim.git dracula
# 配置
vim ~/.vimrc
packadd! dracula
syntax enable
colorscheme dracula
```

* apt-get

```shell
apt-get update
apt-get install telnet
apt-get install curl
apt-get install net-tools
apt-get install vim
apt-get install inetutils-ping
apt-get install openssh-server
apt-get install openssh-client
apt-get install systemctl
```
