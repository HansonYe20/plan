# [mongoDB](https://docs.mongodb.com/guides/)
## 简介
文档数据库

## 相关概念
  - BSON
    * 是一种计算机数据交换格式，主要被用作MongoDB数据库中的数据存储和网络传输格式。它是一种二进制表示形式，能用来表示简单数据结构、关联数组（MongoDB中称为“对象”或“文档”）以及MongoDB中的各种数据类型。BSON之名缘于JSON，含义为Binary JSON（二进制JSON）
    * 与JSON相比，BSON着眼于提高存储和扫描效率。BSON文档中的大型元素以长度字段为前缀以便于扫描。在某些情况下，由于长度前缀和显式数组索引的存在，BSON使用的空间会多于JSON
  - MongoLab: MongoDB托管服务, 还包括MongoHQ服务
  - ODM: 对象文档映射
  - Mongoose: 有官方支持的 MongoDB ODM 是 Mongoose

## 安装
主要是为了搭配node, express使用, 这里选择安装旧版本, 毕竟社区资源比较丰富(捂脸)

### 1.官网下载安装, [点击下载][download]

### 2.使用homebrew下载安装, MacOS
#### (1)安装过程中出现的问题:
+ Updating Homebrew...
  - ctrl + c 一次, 然后就开始安装目标软件, 治标不治本
  + 更改homebrew镜像源, 比如阿里巴巴, [参考链接][homebrewMirror]
    - 替换成阿里巴巴的 brew.git 仓库地址: 
      > cd "$(brew --repo)"

      > git remote set-url origin https://mirrors.aliyun.com/homebrew/brew.git 
  + 关闭homebrew自动更新
    - code ~/.bash_profile
    - ```export HOMEBREW_NO_AUTO_UPDATE=true```
+ 直接brew search mongodb, 无法找到低版本
  - ```brew tap mongodb/brew```
+ 或者安装的高版本, 在usr/local/Cellar下找不到安装文件, 在usr/local/etc下没有mongod.conf文件, 会产生其他问题, 比如connect faild...
+ brew / brew cask 安装对比
+ 修改.bash_profile文件不生效:
  - 命令行执行```source ~/.bash_profile```

#### (2)最终安装过程如下, [安装指导](https://docs.mongodb.com/v3.6/tutorial/install-mongodb-on-os-x/):
感觉翻译很怪, 贴原文了...
1. brew tap mongodb/brew
    > If you have previously tapped the official MongoDB formula repository, you can go directly to the Install MongoDB step.

    > If you have not previously tapped the official MongoDB formula repository, tap the official MongoDB formula repository to add to the formula list. From a terminal, issue the following:
2. brew install mongodb-community@3.6
+ 同时会生成如下文件(夹):
  - the configuration file (/usr/local/etc/mongod.conf)
  - the log directory path (/usr/local/var/log/mongodb)
  - the data directory path (/usr/local/var/mongodb)

## 启动
1. brew services start mongodb-community@3.6
2. mongo
* 不出意外, 会遇到的问题:
  - command not found: mongo
  - 解决: 在~/.bash_profile文件中加入:
    - ```export PATH="/usr/local/Cellar/mongodb-community@3.6/3.6.14/bin:${PATH}"```

## 工具
- 命令行工具Mongo shell
+ GUI工具
  + 官方推荐[Compass][Compass]
    提供了四种版本, [Compass下载地址][compassdownload]
    - Compass Community 开发版本
    - Compass 全功能(**本文档下载的是该文档**)
    - Compass Readonly 只读
    - Compass Isolated 更安全环境下使用
    1. 下完直接安装即可, 按照引导页面, 非空选项配置主机:localhost, 默认端口: 27017即可
    2. 点击连接即可出现如下页面, 其中inventory的数据是之前测试插入的数据
      ![compassIndexImg][compassIndexImg]
  - RoboMongo/robo 3t
  - others...

## 操作
  - 如果使用compass, 看官方文档吧,
    - filter: 输入 { name: "123" }, 而不是像mysql形式的 name="123"
  + Mongo shell
    启动服务后, 打开mongo shell, 开始正式操作数据库
    * 本地连接:
      - mongo:
        connect to a MongoDB instance running on your localhost with default port 27017
      - mongo --port 28015:
        修改端口
    * 远程连接:
      - mongo "mongodb://mongodb0.example.com:28015"
      - mongo --host mongodb0.example.com:28015
    * 常规操作:
      - db
      - use <database>
      - create database: use <new databaseName>
      - db.mytable.insertOne( { x: any } )
      - db.getCollection("mytable").find()
      - CRUD 自行看官网
    * 多行操作, 括号必须成对, `()[]{}`, 竟然还可以写代码...
  + mongoose 由于实际需要, 包括实际上的问题(解决事务, 联表查询, 导出连接实例等), 都有成熟的解决方案, 所以使用了这个第三方库
    - [中文文档地址][mongooseDoc]
    - 相关概念
      - schema
        - 在 mongoose 中，所有的东西都来源于一个 schema，每个schema 映射了一个 MongoDB 的集合，它定义了这个集合中的文档的骨架;
        - model 是我们构造 document 的 Class
      - model: 一个文件的构造器，通过编译schema得到，一个model的实例就是一个文件，model负责从 MongoDB 数据库中创建和读取文档。
    - 事务(transactions):
      - [参考链接][mongooseTransactions]
      - To use transactions with Mongoose, you need mongoose >= *5.2.0*.

## 部署
  *******[TODO]*******




[Compass]: https://docs.mongodb.com/compass/current/#compass-index 'Compass官网资料'
[download]: https://www.mongodb.com/download-center/community '下载地址'
[compassdownload]: https://www.mongodb.com/download-center/compass?jmp=docs 'Compass下载地址'
[compassIndexImg]: ./mongo-compass.png 'compassGUI首页'
[homebrewMirror]: https://www.cnblogs.com/testlife007/p/10923243.html '镜像更换'
[mongooseDoc]: https://mongoosedoc.top/docs/index.html 'mongoose中文文档'
[mongooseTransactions]: http://thecodebarbarian.com/a-node-js-perspective-on-mongodb-4-transactions.html 'mongooseTransactions'