# windows上安装rocket mq

## 前言

rocket mq是apache下的一个消息队列

## 安装

1. 从官网下载压缩包

   [Apache Downloads](https://www.apache.org/dyn/closer.cgi?path=rocketmq/4.9.2/rocketmq-all-4.9.2-bin-release.zip)

   ![image-20211215141818023](https://raw.githubusercontent.com/bluechaplin/image-repository/master/Dec.2021/202112151418141.png)

2. 解压文件

3. 配置环境变量

   ROCKETMQ_HOME

   ![image-20211215142253077](https://raw.githubusercontent.com/bluechaplin/image-repository/master/Dec.2021/202112151422125.png)

4. 启动namesrv

   ```powershell
   start mqnamesrv.cmd
   ```

5. 启动broker

   ```powershell
   start mqbroker.cmd -n 127.0.0.1:9876 autoCreateTopicEnable=true
   ```

   

