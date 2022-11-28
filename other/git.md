# 基本配置

## ssh免密

```shell
# 配置基本信息
git config --global user.name "hang"
git config --global user.email "1040487567@qq.com"

# 配置ssh免密登陆 进入gitee/github将公钥复制进去
ssh-keygen -t rsa -C "1040487567@qq.com"
cat ~/.ssh/id_rsa.pub

# 测试是否成功
ssh -T git@gitee.com
ssh -T git@github.com
```

## token

- github：Settings——》Developer settings——》Personal access tokens
- remote.origin.url=https://<TOKEN>@github.com/<USER>/<REPOSITORIES>

# 忽略文件

- .gitconfig

```shell
[core]
    excludesfile = ~/.gitignore
```

- .gitignore

```text
# Compiled class file
*.class

# Eclipse
.project
.classpath
.settings/

# Intellij
*.ipr
*.iml
*.iws
.idea/

# Maven
target/

# Gradle
build
.gradle

# Log file
*.log
log/

# out
**/out/

# Mac
.DS_Store

# others
*.jar
*.war
*.zip
*.tar
*.tar.gz
*.pid
*.orig
temp/
```

# 基本使用

```shell
# 初始化操作
git init
git init [仓库名称]

# 添加指定文件到暂存区
git add [文件1] [文件2] ...
git add [目录名]
git add .

# 删除暂存区文件
git rm [文件1] [文件2] ...
git rm --cached [文件1] [文件2] ...

# 查看暂存区状态
git status

# 提交暂存区到本地仓库
git commit -m [备注信息]
git commit --amend -m [备注信息]

# 查看历史版本
git log --oneline

# 拉取项目
git clone [远程仓库项目地址]
git clone https://<TOKEN>@github.com/<user_name>/<repo_name>.git

# 远程库操作
git remote show [远程地址别名]
git remote add [远程地址别名] [远程地址]
git remote remove [远程地址别名] 
git push [远程地址别名] [本地分支名]
git pull [远程地址别名] [本地分支名]

# 比较文件差异
git diff --cached

# 重置版本
git reset --soft [commithash]
git reset --hard [commithash]

# 分支操作
git branch [分支名]
git branch -a
git branch -d [分支名]

# 切换到指定的分支
git checkout [分支名]

# 合并分支：推荐使用rebase
git merge [要合并分支名]
git rebase [要合并分支名]

```