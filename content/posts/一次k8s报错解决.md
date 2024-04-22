+++
title = '一次k8s报错解决'
date = 2024-04-22T14:58:37+08:00
draft = false
tags = ['Linux']
comments = true
+++

## 问题 failed to create fsnotify watcher: too many open files

> 解决方案:


`sudo sysctl fs.inotify.max_user_instances=81920`

> 下面是持久化更改

`echo fs.inotify.max_user_instances=81920 >> /etc/sysctl.conf &&  sysctl -p`

