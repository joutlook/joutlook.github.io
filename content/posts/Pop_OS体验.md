+++
title = 'Pop_OS体验'
date = 2024-04-07T16:51:33+08:00
tags = ['Linux']
comments = true
+++

> 一直寻找好用的 `Linux` 发行版,直到遇到了 `Pop_OS`

添加图片测试
![t](/images/2024-04-08_10-24-50.png)


代码块测试1

```
#!/usr/bin/python
# -*- coding: utf-8 -*-

filecount = 30000
filesize = 1024


import random, time
from os import system
flush = "sudo su -c 'sync ; echo 3 > /proc/sys/vm/drop_caches'"

randfile = open("/dev/urandom", "r")

print "\ncreate test folder:"
starttime = time.time()
system("rm -rf test && mkdir test")
print time.time() - starttime
system(flush)

print "\ncreate files:"
starttime = time.time()
for i in xrange(filecount):
    rand = randfile.read(int(filesize * 0.5 + filesize * random.random()))
    outfile = open("test/" + unicode(i), "w")
    outfile.write(rand)
print time.time() - starttime
system(flush)

print "\nrewrite files:"
starttime = time.time()
for i in xrange(int(filecount / 10)):
    rand = randfile.read(int(filesize * 0.5 + filesize * random.random()))
    outfile = open("test/" + unicode(int(random.random() * filecount)), "w")
    outfile.write(rand)
print time.time() - starttime
system(flush)

print "\nread linear:"
starttime = time.time()
for i in xrange(int(filecount / 10)):
    infile = open("test/" + unicode(i), "r")
    outfile.write(infile.read());
print time.time() - starttime
system(flush)

print "\nread random:"
starttime = time.time()
outfile = open("/dev/null", "w")
for i in xrange(int(filecount / 10)):
    infile = open("test/" + unicode(int(random.random() * filecount)), "r")
    outfile.write(infile.read());
print time.time() - starttime
system(flush)

print "\ndelete all files:"
starttime = time.time()
system("rm -rf test")
print time.time() - starttime
system(flush)

```