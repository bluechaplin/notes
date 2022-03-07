# windows安装mongodb

## 一、前言

mongodb是一款免费且简单易用的非关系型数据库，广泛应用于分布式存储

## 二、安装

建议查看官网的安装指引

[Install MongoDB](https://docs.mongodb.com/guides/server/install/)

### 2.1、下载和安装

下载地址

[Try MongoDB Products | MongoDB](https://www.mongodb.com/try/download/community)

![image-20211215113542226](https://raw.githubusercontent.com/bluechaplin/image-repository/master/Dec.2021/202112151135382.png)

下载可执行文件后直接点击安装

### 2.2、配置和启动

- 选择一个数据存储位置

  eg:

  ```
  E:\db\mongodb\data
  ```

  有两种方式可以指定这个数据存储位置

  第一种是通过`mongod.exe`启动时添加启动参数

  eg: 

  ```powershell
  mongod.exe --dbpath E:\db\mongodb\data
  ```

  第二种是通过配置文件来进行配置

  ps: 官方配置文件说明

  [Configuration File Options — MongoDB Manual](https://docs.mongodb.com/manual/reference/configuration-options/)

  ![image-20211215114433165](https://raw.githubusercontent.com/bluechaplin/image-repository/master/Dec.2021/202112151144218.png)

- 启动

  ```powershell
  mongod.exe
  ```

- 连接

  ```powershell
  mongo.exe
  ```

### 2.3、mongodb配置为windows服务

1. 以管理员身份打开命令行

2. 执行服务安装命令

   ```powershell
   mongo.exe --install --serviceName "mongodb"......
   ```

3. 启动服务

   ```powershell
   net start mongodb
   ```

   
