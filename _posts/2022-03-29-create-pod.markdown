---
layout: post
title:  "建一個pod"
date:   2022-03-29
categories: podman
tags: [podman, services]
---

充個版面。


* 建一個ｄｂ
1. podman pod create --name db0 --publish 8080:8080 --publish 3306:3306
3. podman images
2. podman run --name mariadb  --pod db0 -e MYSQL_ROOT_PASSWORD='xxxxxxxxx' 6e0162b44a5f
3. podman run --name adminer --pod db0  33287ce4d5c5


* 建一個consul
1. podman pull consul
2. podman pod create --name reg-service --publish 8500:8500
3. podman images
4. podman run --name consul --pod reg-service <<consul_image_id>>
