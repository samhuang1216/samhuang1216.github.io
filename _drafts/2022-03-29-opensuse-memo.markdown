---
layout: post
title:  "opensuse memo"
date:   2022-03-29
categories: opensuse
tags: [linux, opensuse]
---


### 沒設都會出問題

    hostnamectl
    hostnamectl set-hostname suselaptop

## autostart podman and spring-boot project on login



```console
### login script


#!/bin/sh
# Output the following line:

podman pod start db0
podman pod start reg-service


cd /run/media/aesired/sata2/_codes/myspace/configServer/
nohup mvn spring-boot:run >/dev/null &

sleep 15

cd /run/media/aesired/sata2/_codes/myspace/gateway/
nohup mvn spring-boot:run  >/dev/null &
```

### logout script

``` she
#!/bin/sh
# Output the following line:

pidof java |xargs kill -9

podman pod stop -a


```

### crontab setting

``` she
crontab -e

#add line
@reboot sh /home/aesired/opensuse_init_podman_config_gateway.sh 
```

### logout script setting using GUI

#### autostart
