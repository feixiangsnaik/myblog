---
title: docker
date: 2021-12-25 11:39:29
tags:
---
## 常规操作
mac 安装：   brew install --cask docker 
https://stackoverflow.com/questions/40523307/brew-install-docker-does-not-include-docker-engine
docker版本查看   docker -v
## 安装centos和宝塔

1.docker pull centos
2.docker run -i -t -d --name baota -p 20:20 -p 21:21 -p 80:80 -p 443:443 -p 888:888 -p 8888:8888 --privileged=true -v /home/www:/www centos     如果目录不能访问就换个目录比如（docker run -i -t -d --name baota -p 20:20 -p 21:21 -p 80:80 -p 443:443 -p 888:888 -p 8888:8888 --privileged=true -v /Users/zhangshuai/Desktop/installedsoftware/www:/www centos:7 /usr/sbin/init）
3.docker exec -it baota /bin/bash
## 宝塔安装
4.yum install -y wget && wget -O install.sh http://download.bt.cn/install/install.sh && sh install.sh
docker->preferences->resource->file sharing

## 删除所有已退出的容器
docker rm $(docker ps -q -f status=exited)

删除所有已停止的容器
docker rm $(docker ps -a -q)

## 删除所有正在运行和已停止的容器
    docker stop $(docker ps -a -q)
    docker rm $(docker ps -a -q)

## 删除所有容器，没有任何标准
docker container rm $(docker container ps -aq)

但是，在1.13及更高版本中，对于完整的系统和清理，我们可以直接使用以下命令，
docker system prune