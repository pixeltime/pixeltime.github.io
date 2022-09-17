---
title: "音视频编解码"
date: 2021-11-06 +0800
categories: ["音视频学习"]
tags: [音视频格式]
---

```sh
音视频格式
```
flv,MKV 常见的视频格式

mpegx、h264视频裸流,

g.726x、aac、音频裸流,

 
例如一个flv文件可以理解为 h264+aac


```sh
直播流
```

rtmp(百度) flv(百度) hls(百度)

rtmp 承载在tcp上，协议较复杂，建立tcp通讯(先握手，发送createstream，发送play)，音视频打包成rtmp包

flv 承载在http上，一般叫http-flv，客户端发送http请求，服务端推送httpchunk，音视频数据打包成flv包

hls 承载在http上,客户端请求m3u8文件，该文件定义了ts流，然后循环(m3u8,ts)，音视频打包成ts包

