---
layout: post
title:  "pod as service"
date:   2022-03-29
categories: podman
tags: [podman, system]
---
podname是db0, 系統是opensuse
預設系統為某使用者登入後啟動。

1. podman generate systemd --files --name db0 
2. cd ~
3.  cd .config/
4.  mkdir -p systemd/user
5.  cp *.service ~/.config/systemd/user/
6.  systemctl enable --user pod-db0.service 
7.  systemctl is-enabled --user pod-db0.service 
8.  podman pod stop db0
9.  podman ps -a
10.  systemctl start --user pod-db0.service 
11.  podman ps -a
12.  systemctl status --user pod-db0.service 
