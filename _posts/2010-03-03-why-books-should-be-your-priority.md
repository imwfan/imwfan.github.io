---
date: 2018-11-22 12:26:40
layout: post
title: Why books should be your priority?
subtitle: Lorem ipsum dolor sit amet, consectetur adipisicing elit.
description: Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
image: https://res.cloudinary.com/dm7h7e8xj/image/upload/v1559822138/theme9_v273a9.jpg
optimized_image: https://res.cloudinary.com/dm7h7e8xj/image/upload/c_scale,w_380/v1559822138/theme9_v273a9.jpg
category: life
tags:
  - books
  - read
author: mranderson
paginate: true
---






<!--page-->
## 介绍
Oracle Database 19c ，也就是12.2.0.3，最初在livesql.oracle.com上发布，是Oracle Database 12c和18c系列产品的最终版本，因此也是“长期支持”版本（以前称为“终端版本”）。 “长期支持”意味着Oracle Database 19c提供4年的高级支持（截止到2023年1月底）和至少3年的延长支持（截至2026年1月底）。 这个扩展的支持窗口对我们的很多客户至关重要，因为很多客户制定了相关的升级策略。有关最新的Oracle支持计划，请参阅My Oracle Support上的文档ID 742060.1。截止目前，Oracle Database 19c已经可以在Oracle数据库一体机上使用了。
## 前期准备
### Docker安装

```sh
#升级yum
sudo yum update  

#卸载旧版本
sudo yum remove docker  docker-common docker-selinux docker-engine  

#安装依赖  
sudo yum install -y yum-utils device-mapper-persistent-data lvm2  

#设置源  
sudo yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo   

# 更新yum缓存
yum makecache fast

# 安装Docker
yum -y install docker-ce

# 启动
systemctl start docker

# 查看是否启动成功
docker info

# 开机自启
systemctl enable docker

# Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the d
systemctl restart docker  #重启一下就行

# 在下载镜像前，需要设置一下国内源，用来提高下载速度
sudo vim /etc/docker/daemon.json

# 配置
{  
    "registry-mirrors": ["https://d7grpode.mirror.aliyuncs.com"]  
}

# 重启
sudo systemctl restart docker
```
安装成功界面
![](https://i-blog.csdnimg.cn/blog_migrate/2e1ea0e0a22af71873efaebbd84de94a.png)
## Oracle 19c安装
### 第一步：下载镜像

```sh
# 下载镜像
docker pull registry.cn-hangzhou.aliyuncs.com/zhuyijun/oracle:19c
```
我们来看一下有没有下载成功
![](https://i-blog.csdnimg.cn/blog_migrate/cebb1b52443396c867553a62b49e8114.png)

### 第二步：创建挂载文件

```sh
# 创建文件
mkdir -p /mydata/oracle/oradata

# 授权，不授权会导致后面安装失败
chmod 777 /mydata/oracle/oradata
```

### 第三步：安装Oracle
1、安装oracle，并把配置挂载到本地文件
```sh
docker run -d  \
-p 1524:1521 -p 5502:5500 \
-e ORACLE_SID=ORCLCDB \
-e ORACLE_PDB=ORCLPDB1 \
# 此处是oracle密码
-e ORACLE_PWD=123456 \
-e ORACLE_EDITION=standard \
-e ORACLE_CHARACTERSET=AL32UTF8 \
-v /mydata/oracle/oradata:/opt/oracle/oradata \
--name orcl19c_03 \
registry.cn-hangzhou.aliyuncs.com/zhuyijun/oracle:19c
```
2、查看oracle是否安装成功

```sh
# 查看启动日志
docker logs -ft orcl19c_03
```
显示如下画面，表示安装成功
![](https://i-blog.csdnimg.cn/blog_migrate/9104b72467c24dde152f0091ccab080d.png)
> 注意：
> 如果安装失败 ,执行以下命令
> docker stop orcl19c_03
> docker rm orcl19c_03

### 第四步：连接Oracle

```sh
docker exec -it orcl19c_03 /bin/bash

sqlplus / as sysdba

show pdbs;
```
这样就可以了
![](https://i-blog.csdnimg.cn/blog_migrate/c45c6e9dbff5612642f725062ffcc110.png)
还可以通过访问https://localhost:5502/em
![](https://i-blog.csdnimg.cn/blog_migrate/30ccee176dde258c9fc9f95c493927f4.png)

>username：sys
>password：123456
>Container Name：ORCLPDB1

![](https://i-blog.csdnimg.cn/blog_migrate/6754291333792bbad8876cf99e55d6ef.png)
>注意 ：是https，不是http



<!--page-->

Nullam id dolor id nibh ultricies vehicula ut id elit. Sed posuere consectetur est at lobortis. Nullam quis risus eget urna mollis ornare vel eu leo.










