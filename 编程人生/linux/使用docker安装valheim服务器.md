# 使用docker安装vaiheim服务器

## 前言

vaiheim是一款多人在线生存游戏

## 步骤

### 创建目录

```shell
mkdir /home/vaiheim-server/config/worlds /home/vaiheim-server/data
```

### [可选]复制已有存档

复制已有存档到`/worlds`文件夹下（如果之前游戏内开过房间，想要迁移到专用服务器上，那么这一步就需要做）

存档一般放在“C:\Users\用户名\AppData\LocalLow\IronGate\Valheim\worlds”，直接用上传到服务器的“home/valheim-server/config/worlds”文件夹下就可以了。

### 运行

```shell
docker run -d \
--name valheim-server \
--cap-add=sys_nice \
--stop-timeout 120 \
-p 2456-2457:2456-2457/udp \
-v /home/valheim-server/config:/config \
-v /home/valheim-server/data:/opt/valheim \
-e SERVER_NAME="Server Name" \
-e WORLD_NAME="这里是存档名（如果上面用了之前的存档，就是“.db”或“.fwl”之前的名字）" \
-e SERVER_PASS="这里填写密码（至少5个字符，不然会报错）" \
lloesche/valheim-server
```

## 注意事项

更多镜像资料请移步

https://github.com/lloesche/valheim-server-docker#environment-variables