## Jenkin安装
Jenkins是一个开源软件项目，旨在提供一个开放易用的软件平台，使软件的持续集成变成可能。Jenkins是基于Java开发的一种持续集成工具，用于监控持续重复的工作，功能包括：
1、持续的软件版本发布/测试项目。
2、监控外部调用执行的工作。

一、在安装和启动Jenkins之前要先安装java，在后续自动化编译和测试项目会用到maven，版本控制使用的是git。其中maven和git使用的是apt-get的方式安装。

java的安装，从oracle下载jdk8的压缩包[http://www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html)，解压jdk压缩包，并修改环境变量的配置,
```
$ tar -zxvf jdk-8u111-linux-i586.tar.gz
$ sudo vi /etc/profile

```
