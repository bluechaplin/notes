# Linux上jar包的启动和关闭脚本编写

## 一、startup.sh

```shell
log_name="$(date "+%Y%m%d").log"
echo ${log_name}
nohup java address=8002 -jar test-dev.jar > ${log_name} & echo $! > test-dev.pid
tail -f ${log_name}
```

## 二、shutdown.sh

```shell
kill -9 `cat test-dev.pid.pid`
```

