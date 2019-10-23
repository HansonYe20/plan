# mongoDB
## 简介
文档数据库

## 安装
主要是为了搭配node, express使用, 这里选择安装旧版本, 毕竟社区资源比较丰富(捂脸)

### 1.官网下载安装, [点击下载](https://www.mongodb.com/download-center/community)

### 2.使用homebrew下载安装, MacOS
#### (1)安装过程中出现的问题:
+ Updating Homebrew...
  - ctrl + c 一次, 然后就开始安装目标软件, 治标不治本
  - 更改homebrew镜像源, 比如阿里巴巴
  - 关闭homebrew自动更新
    - code ~/.bash_profile
    - ```export HOMEBREW_NO_AUTO_UPDATE=true```
+ 直接brew search mongodb, 无法找到低版本
  - ```brew tap mongodb/brew```
+ 或者安装的高版本, 在usr/local/Cellar下找不到安装文件, 在usr/local/etc下没有mongod.conf文件, 会产生其他问题, 比如connect faild...
+ brew / brew cask 安装对比
+ 修改.bash_profile文件不生效:
  - 命令行执行```source ~/.bash_profile```
#### (2)最终安装过程如下, [安装指导](https://docs.mongodb.com/v3.6/tutorial/install-mongodb-on-os-x/):

1. brew tap mongodb/brew
    > If you have previously tapped the official MongoDB formula repository, you can go directly to the Install MongoDB step.

    > If you have not previously tapped the official MongoDB formula repository, tap the official MongoDB formula repository to add to the formula list. From a terminal, issue the following:
2. brew install mongodb-community@3.6
+ 同时会生成如下文件(夹):
  - the configuration file (/usr/local/etc/mongod.conf)
  - the log directory path (/usr/local/var/log/mongodb)
  - the data directory path (/usr/local/var/mongodb)

## 运行
1. brew services start mongodb-community@3.6
2. mongo
* 不出意外, 会遇到的问题:
  - command not found: mongo
  - 解决: 在~/.bash_profile文件中加入:
    - ```export PATH="/usr/local/Cellar/mongodb-community@3.6/3.6.14/bin:${PATH}"```

## 相关概念
- MongoLab: MongoDB托管服务, 还包括MongoHQ服务
- ODM: 对象文档映射
- Mongoose: 有官方支持的 MongoDB ODM 是 Mongoose