# 安装&卸载

- 安装

```shell
/bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master/Homebrew.sh)"

source ~/.zprofile
```

- 卸载

```shell
/bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master/HomebrewUninstall.sh)"
```

# 基本命令

```shell
# 查看brew的版本
brew -v

# 更新homebrew
brew update

# 查看命令帮助
brew -help

# 更新单个软件
brew upgrade [包名]

# 更新所有软件
brew upgrade 

# 安装软件
brew install [包名]@版本

# 卸载
brew uninstall [包名]

# 清理所有包的旧版本
brew cleanup 

# 查看包信息
brew info [包名]

# 查看安装列表
brew list

# 查询可用包
brew search [包名]
```

# 安装记录

- tree

```shell
brew install --Formulae tree
```
