---
layout: post
title:  "基于 ZYNQ UltraScale+ MPSoC 的智能电网宽带微 功率无线通信系统原型机"
author: XUP-2020
categories: [ project, 2020competition ]
image: assets/images/zynq_ultra_mpsoc_com_cover.jpg
---

微功率无线技术是一种专注于低功耗、低成本、低复杂度、短时延、低速率， 高可靠的近程无线网络通信技术。宽带微功率无线通信系统将提供传输性能更好、 稳定性更高、兼容性更有保障的本地台区(一台变压器的供电区域)下的通信方 式，该技术将有力地推进国家电网的发展和建设。

**基于 ZYNQ UltraScale+ MPSoC 的智能电网宽带微 功率无线通信系统原型机**

by&nbsp;**叶宇欣、杨正海&amp;袁帅**

微功率无线技术是一种专注于低功耗、低成本、低复杂度、短时延、低速率， 高可靠的近程无线网络通信技术。宽带微功率无线通信系统将提供传输性能更好、 稳定性更高、兼容性更有保障的本地台区(一台变压器的供电区域)下的通信方 式，该技术将有力地推进国家电网的发展和建设。宽带微功率无线通信系统具有 以下几个显著的特点:(1)实时数据量不大;(2)无线环境复杂;(3)发射功率受限; (4)设备工作周期长且成本低廉。因此，该系统所使用的无线传输技术必须具备复 杂度低、抗干扰能力强、灵敏度高和功耗低等特性。

基于 Chirp 信号的无线传输技术具有低复杂度、低功耗、抗多径能力强和抗 干扰效果好等优点，并已于 2004 年被列为 IEEE 802.15.4 标准的物理层备用技 术。Chirp 无线传输技术的优点和宽带微功率无线通信系统的需求十分吻合，所 以将其做为宽带微功率无线通信系统传输技术的首选方案。

宽带微功率无线通信系统原型机使用 Xilinx 的 ZYNQ UltraScale+ MPSoC XCZU6CG 作为基带处理芯片，使用 ADI 公司的 AD9361 作为射频收发器。采用 ARM+FPGA硬件架构，使用Cortex-R5实时处理单元运行协议栈软件，FPGA主 要负责对基带数据进行 CRC 编码/校验、Tubro 编码/译码、信道交织/解交织、以 及 Chirp 调制/解调，最后通过射频前端发送或接受信号。宽带微功率无线通信系 统原型机设计满足国家电网公司《电力用户用电信息采集系统通信协议:微功率 无线通信标准》要求的无线抄表系统，包含中心节点和子节点，用于电力用户用 电信息采集。该系统具有自动组网，数据传输，多跳中继，自动路由等功能。

**关键词:智能电网，无线微功率，物联网，协议栈**

![image_7]({{ site.baseurl }}/assets/images/article_15/image_7.png)

**参赛队员与指导老师合影**

![image_1]({{ site.baseurl }}/assets/images/article_15/image_1.png)

**参赛队员与作品合影**

![image_2]({{ site.baseurl }}/assets/images/article_15/image_2.png)

**模块整体**

![image_3]({{ site.baseurl }}/assets/images/article_15/image_3.png)

**射频版反面**

![image_4]({{ site.baseurl }}/assets/images/article_15/image_4.png)

**射频版正面**

![image_5]({{ site.baseurl }}/assets/images/article_15/image_5.png)

**数字版反面**

![image_6]({{ site.baseurl }}/assets/images/article_15/image_6.png)

**数字版正面**
