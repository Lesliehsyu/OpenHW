---
layout: post
title:  "基于无线视频传输的运动物体追踪系统"
author: XUP-2020
categories: [ project, 2020competition ]
image: assets/images/wireless_stream_movingob_detect_cover.jpg
---

对于遥感卫星通常需要监测地面较大运动物体，气象卫星需要监测地面云图， 有特勤任务的无人机也要对指定的物体进行跟踪，类似于此类应用的系统，通常 都有如下几个需求:视频源要尽量的清晰且数据无损，无线数据传输要稳定，识 别定位跟踪算法要准确迅速。

**基于无线视频传输的运动物体追踪系统**

**by&nbsp;王飞、尉倞浩&amp;田刚**

对于遥感卫星通常需要监测地面较大运动物体，气象卫星需要监测地面云图， 有特勤任务的无人机也要对指定的物体进行跟踪，类似于此类应用的系统，通常 都有如下几个需求:视频源要尽量的清晰且数据无损，无线数据传输要稳定，识 别定位跟踪算法要准确迅速。

根据以上三点需求，本文设计了一款基于无线视频传输的运动物体追踪系统。 该系统主要由三部分组成:1080P 高清视频数据获取及转码部分，高速无线通信 部分，基于上位机软件的分析显示部分。视频数据源首先获取到 HDMI 格式视频 数据，通过信号转接板将信号转换成 SFP 光纤传输数据，之后送至发射基带板。 发射基带进行信源编码，信道编码，QAM 映射，根升余弦滤波成型后将数据送至 DA，DA 将数字数据模拟转换后，送至射频前端进行发射。接收端通过天线收到模 拟信号后，经外部低噪放和差分放大将信号初步调理至 AD 采样范围，AD 将模拟 信号量化后直接送入基带接收处理板。由 FPGA 进行同步、均衡、根升余弦、抽 样、QAM 逆映射、信道译码、信源译码等操作后，恢复出发射前信号，之后将数 据转换成 SFP 光纤数据，送至视频信号处理板。视频信号处理板首先对 SFP 光纤 数据进行有效数据提取，随后按照视频格式形成 PCIE 兼容数据，送至上位机。 上位机根据收到的数据进行运动物体的识别与追踪，同时在界面上显示。

视频部分采用了无损无压缩编码方式，直接将摄像头获取到的所有数据进行 了直传，数据量较大，抽取时序要求严格，但为上位机准确识别与追踪提供了便 利。无线通信部分采用了经典架构，不仅能够提供足够的带宽，实现更高的传输 速率，还能够对各类算法进行灵活实现。采用三帧帧法进行运动物体识别，可以 快速的识别到运动的物体，且保持跟踪状态。

关键词:无损视频传输 无线通信 三帧帧法 运动物体跟踪

&nbsp;

![image_1]({{ site.baseurl }}/assets/images/article_13/image_1.png)

**作品特写**

![image_2]({{ site.baseurl }}/assets/images/article_13/image_2.png)

**作品特写**

![image_3]({{ site.baseurl }}/assets/images/article_13/image_3.png)

**作品特写**

![image_4]({{ site.baseurl }}/assets/images/article_13/image_4.png)

**作品特写**

![image_5]({{ site.baseurl }}/assets/images/article_13/image_5.png)

**作品特写**

![image_6]({{ site.baseurl }}/assets/images/article_13/image_6.png)

**队员与指导老师合影**

![image_7]({{ site.baseurl }}/assets/images/article_13/image_7.png)**与作品合照**

![image_8]({{ site.baseurl }}/assets/images/article_13/image_8.png)

**作品全照**
