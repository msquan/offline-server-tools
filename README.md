# 线下服务工具集
自己常用的一些线下服务小工具

golang可以方便地build成跨平台的可执行文件，并且体积很小，比较适合做这类小工具。之前用nodejs写过这类工具，但是部署依赖比较麻烦，不方便分享。


## 1、本地开发远程同步工具
详见 sync-deploy-service

### 描述
实时同步开发代码、编译产出，到线下机器（开发机、测试机），触发部署脚本

### 背景与用途
- 本地开发因为办公网限制，无法连db及上下游服务；堡垒机开发通过远程桌面诸多不便还挺卡。
- 可以用这个工具，在你超高配的本地电脑开发，同步代码或者编译产出到线下机器，再触发部署，还能实时看远程服务的输出日志信息

### 特色
- 基于http协议(websocket)传输，服务端可以使用安全策略开放的http端口
- 将远程deploy命令的stdout、stderr实时同步到本地，方便根据日志开发调试
- 支持web页面列出服务器的同步目录，方便查看文件列表和更新时间等
- 同步前根据md5预检查是否需要传输文件，LRU缓存

### 效果
![效果图](./sync-deploy-service/snapshot.jpg)


## 2、简单文件上传执行器
详见 upload-and-run

### 描述
这是一个简单的文件上传后，调用脚本执行，并反馈处理结果给前端的小服务工具。

### 背景与用途
经常要给PM跑数（数据统计），有的跑数需求，需要频繁搞。
那么就可以用这个，**把跑数脚本包装成一个简易的服务**。
后续相似的跑数需求，PM就可以自助跑了。

### 效果
![效果图](./upload-and-run/snapshot.png)