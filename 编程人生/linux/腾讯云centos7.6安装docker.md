# 腾讯云centos7.6安装docker

### 依次执行以下命令，添加 yum 源。

```shell
yum update

yum install epel-release -y

yum clean all

yum list
```

### 执行以下命令，安装 Docker。

```shell
yum install docker-io -y
```

### 执行以下命令，运行 Docker。

```shell
systemctl start docker
```

### 执行以下命令，检查安装结果。

```shell
docker info
```