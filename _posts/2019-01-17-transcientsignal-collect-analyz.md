---
layout: post
title:  "便携式瞬态信号采集与分析仪"
author: XUP-2020
categories: [ project, 2020competition ]
image: assets/images/transcientsignal_collect_analyz_cover.jpg
---

&ldquo;瞬态&rdquo;信号一般是指持续时间较短或在时间上变化较快的信号，常见的瞬 态信号有诸如雷达脉冲信号、跳频调频信号、线性调频信号等。由于瞬态信号具 有抗干扰、抗衰落等优点，这种信号形式在军事和民用通信领域被广泛应用。现 阶段专业的瞬态信号分析工具比较少，而传统的外差式频谱仪、实时频谱分析仪、 调制域分析仪等仪表又无法完整地分析瞬态信号特性。如何准确快速地对瞬态信 号进行采集和分析，是摆在工程师面前的一道难题。

**便携式瞬态信号采集与分析仪**

**by&nbsp;李承昊、谭雷雨&amp;任子龙**

&nbsp;

&ldquo;瞬态&rdquo;信号一般是指持续时间较短或在时间上变化较快的信号，常见的瞬 态信号有诸如雷达脉冲信号、跳频调频信号、线性调频信号等。由于瞬态信号具 有抗干扰、抗衰落等优点，这种信号形式在军事和民用通信领域被广泛应用。现 阶段专业的瞬态信号分析工具比较少，而传统的外差式频谱仪、实时频谱分析仪、 调制域分析仪等仪表又无法完整地分析瞬态信号特性。如何准确快速地对瞬态信 号进行采集和分析，是摆在工程师面前的一道难题。

考虑到瞬态信号形式在通信领域的广泛应用，以及瞬态信号分析工具匮乏的 现状，本文针对瞬态信号的采集与实时分析问题设计并实现一种便携式高精度瞬 态信号采集与分析设备。该设备集分析与采集于一体，具有瞬态信号实时分析和 瞬态信号分选采集两大功能，即可独立使用又可联合使用，达到对目标瞬态信号 实时分析、分选采集与存储的目的。

设备采用&ldquo;AD9361+Zynq-7000 SoC&rdquo;的硬件架构，性能高、功耗低、体积 小，配备电池具备一定的续航能力，便于携带。通过应用 CDMA 实现高速数据 搬移，并在算法上简化短时傅里叶变换算法(STFT)等得到信号的时频信息，设 计并实现了对瞬态信号的实时分析功能。针对检测环境中的非合作目标信号，通 过分析信号特征， 应用 STFT 算法、功率检测算法、模板匹配算法等，设计并 实现按照目标信号特征值的瞬态信号分选采集功能。设备具有专用的人机交互界 面，用户可以通过上位机界面查看瞬态信号的实时分析的结果，并可对待采集的目标信号进行特征参数配置。

![image_7]({{ site.baseurl }}/assets/images/article_17/image_7.png)

团队成员与标志物合影

&nbsp;

![image_1]({{ site.baseurl }}/assets/images/article_17/image_1.png)

团队成员与作品合影

![image_2]({{ site.baseurl }}/assets/images/article_17/image_2.png)

作品及配套设施

![image_3]({{ site.baseurl }}/assets/images/article_17/image_3.png)

作品全貌

![image_4]({{ site.baseurl }}/assets/images/article_17/image_4.png)

作品实际大小

![image_5]({{ site.baseurl }}/assets/images/article_17/image_5.png)

作品硬件板卡反面照片

![image_6]({{ site.baseurl }}/assets/images/article_17/image_6.png)

作品硬件板卡正面照片
