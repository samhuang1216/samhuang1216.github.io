---
layout: post
title:  "找哪些port有在用"
date:   2022-03-25 15:37:21 +0800
categories: commands
tags: [linux, commands]
---


## 查看 Linux TCP Port 被哪隻程式(Process)佔用

查看 Linux TCP Port 被哪隻程式(Process)佔用, 可以用下述的命令:

```shell
- sudo lsof -i
- sudo lsof -i | grep TCP
- sudo lsof -i :80 | grep LISTEN
- sudo netstat -lptu
- sudo netstat -tulpn
- sudo ls -l /proc/$pid/exe
```

## 列出此 TCP Port 目前有哪些 PID

```shell
- sudo fuser 80/tcp # 會把目前使用此 Port 的 PID 全部列出
```