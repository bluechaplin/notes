

# zookeeper安装

## 一、下载

https://zookeeper.apache.org/releases.html#download

![image-20211231113157792](https://raw.githubusercontent.com/bluechaplin/image-repository/master/Dec.2021/202112311131995.png)

## 二、配置

### 1、解压

### 2、配置

- 需要将`/conf`文件夹下的`zoo.*.cfg`重新命名为`zoo.cfg`

- 在合适的地方建立`/data`和`/log`文件夹用于存放zk数据以及日志

- 配置`dataDir`为上面的`data`目录

- 添加`dataLogDir`（默认一般没有），不配置的话日志会一起放到`data`目录下，配置为上面的`log`目录

  ```properties
  # The number of milliseconds of each tick
  tickTime=2000
  # The number of ticks that the initial 
  # synchronization phase can take
  initLimit=10
  # The number of ticks that can pass between 
  # sending a request and getting an acknowledgement
  syncLimit=5
  # the directory where the snapshot is stored.
  # do not use /tmp for storage, /tmp here is just 
  # example sakes.
  dataDir=E:/tools/apache-zookeeper-3.7.0/data
  dataLogDir=E:/tools/apache-zookeeper-3.7.0/log
  # the port at which the clients will connect
  clientPort=2181
  # the maximum number of client connections.
  # increase this if you need to handle more clients
  #maxClientCnxns=60
  #
  # Be sure to read the maintenance section of the 
  # administrator guide before turning on autopurge.
  #
  # http://zookeeper.apache.org/doc/current/zookeeperAdmin.html#sc_maintenance
  #
  # The number of snapshots to retain in dataDir
  #autopurge.snapRetainCount=3
  # Purge task interval in hours
  # Set to "0" to disable auto purge feature
  #autopurge.purgeInterval=1
  
  ## Metrics Providers
  #
  # https://prometheus.io Metrics Exporter
  #metricsProvider.className=org.apache.zookeeper.metrics.prometheus.PrometheusMetricsProvider
  #metricsProvider.httpPort=7000
  #metricsProvider.exportJvmInfo=true
  ```

## 三、启动

windows

```shell
zkServer.cmd
```

linux

```shell
zkServer.sh
```

## 四、测试

### 1、启动客户端

windows

```
zkCli.cmd
```

linux

```
zkCli.sh
```

### 2、执行相关命令

- 查看目录

  ```
  ls /
  ```

- 新建节点

  ```
  create /zkNode helloworld
  ```

- 更新节点数据

  ```
  set /zkMode helloWorld
  ```

- 删除节点

  ```
  delete /zkMode
  ```

  ![image-20211231114327126](https://raw.githubusercontent.com/bluechaplin/image-repository/master/Dec.2021/202112311143188.png)