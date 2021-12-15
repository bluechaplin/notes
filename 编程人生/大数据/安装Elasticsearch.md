# 安装Elasticsearch

## 一、下载es和kibana安装文件

下载地址（官网）：[开源搜索：Elasticsearch、ELK Stack 和 Kibana 的开发者 | Elastic](https://www.elastic.co/cn/)

![image-20211214154512698](https://raw.githubusercontent.com/bluechaplin/image-repository/master/Dec.2021/202112141545833.png)

## 二、安装es

#### 2.1、解压并打开bin目录

![image-20211214175115741](https://raw.githubusercontent.com/bluechaplin/image-repository/master/Dec.2021/202112141751803.png)

#### 2.2、启动server

`windows`上使用`elasticsearch.bat`来启动

启动后访问[localhost:9200](http://localhost:9200/)

![image-20211214175913459](https://raw.githubusercontent.com/bluechaplin/image-repository/master/Dec.2021/202112141759525.png)

## 三、安装kibana

#### 3.1、解压并修改config下的kibana.yml配置

![image-20211214181721749](https://raw.githubusercontent.com/bluechaplin/image-repository/master/Dec.2021/202112141817811.png)

![image-20211214181748049](https://raw.githubusercontent.com/bluechaplin/image-repository/master/Dec.2021/202112141817115.png)

#### 3.2、启动server

windows下到bin目录使用kibana.bat启动服务，等待片刻后访问http://localhost:5601

#### 3.3、操作es

进入[Dev Tools - Elastic](http://localhost:5601/app/dev_tools#/console)

![image-20211214181937278](https://raw.githubusercontent.com/bluechaplin/image-repository/master/Dec.2021/202112141819382.png)
