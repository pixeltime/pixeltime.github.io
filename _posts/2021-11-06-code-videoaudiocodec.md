---
layout: post
title: "音视频编解码"
categories: other
---

由于之前弄tcp通讯那块，所以对于音视频的编码也不是很难理解

```sh
音视频格式
```
flv,MKV 常见的视频格式

mpegx(百度) h264(百度) 视频裸流,

g.726x(百度) aac(百度) 音频裸流,

 
例如一个flv文件可以理解为 h264+aac


```sh
直播流
```

rtmp(百度) flv(百度) hls(百度)

rtmp 承载在tcp上，协议较复杂，建立tcp通讯(先握手，发送createstream，发送play)，音视频打包成rtmp包

flv 承载在http上，一般叫http-flv，客户端发送http请求，服务端推送httpchunk，音视频数据打包成flv包

hls 承载在http上,客户端请求m3u8文件，该文件定义了ts流，然后循环(m3u8,ts)，音视频打包成ts包


日常相关的东西，要理解，真不容易 庆幸又get一个技能