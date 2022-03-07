# 腾讯云centos8.2安装docker

### 执行以下命令，添加 Docker 软件源。

```shell
dnf config-manager --add-repo=http://mirrors.tencent.com/docker-ce/linux/centos/docker-ce.repo
```

### 执行以下命令，查看已添加的 Docker 软件源。

```shell
dnf list docker-ce
```

### 执行以下命令，安装 Docker。

```shell
dnf install -y docker-ce --nobest
```

### 执行以下命令，运行 Docker。

```shell
systemctl start docker
```

### 执行以下命令，检查安装结果。

```shell
docker info
```