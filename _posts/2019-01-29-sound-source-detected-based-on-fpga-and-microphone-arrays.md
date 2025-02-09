---
layout: post
title:  "基于 FPGA 和麦克风阵列的高速高精度声源定位"
author: XUP-2020
categories: [ project, 2020competition ]
image: assets/images/sound_source_detection.jpg
---
作者：赵辰宇、白瑞昕、张慈庭

![isolution]({{ site.baseurl }}/assets/images/all_white.jpg)

## 第一部分 设计概述 / Design Introduction
1.1 设计目的

频繁杂乱的鸣笛声，不但给周边居民的生活质量造成很大影响，而且增加了驾驶员的疲劳，影响行驶安全，并使乘客和行人在出行时倍感烦躁不安。在大多 数城市的道路上，时常出现禁止鸣笛的标志，然而并不是所有人都能自觉地遵守 规则，对鸣笛之人进行适当的处罚是确保这项规定能够顺利实施的必要举措。

我们决定利用麦克风阵列获取声音信号，使用 FPGA 技术计算声音的位置， 使用 OPENMV 实现图像的抓拍，最终实现对鸣笛车辆的准确定位。

1.2 应用领域

本作品实际应用前景广泛。

用于民用领域：在交通监控中，对违规鸣笛的车辆进行定位并拍照取证，提高监控效率；在音视频会议系统中，采集会议发言人的语音信号，并进行实时处 理来确定发言人的当前位置坐标；在安防系统中，利用声源定位系统来辅助传统 摄像头，从而调整监控方向，弥补了普通的运动识别在光线昏暗条件下的不足， 提升安防效果；等等。

用于军事领域：既可以有效的发现敌方目标所在的位置，又可以充分的隐藏 自身。

1.3 主要技术特点

（1）采用麦克风阵列来获取声音信号 相较于传统麦克风，麦克风阵列具有空间选择性，能明显抑制干扰；可以用 于获取多个声源或移动声源信号，也可以用在一些特殊场合，该系统对于远处和 近处的声源，均可以正常工作。

（2）利用 FFT 算法和 CORDIC 算法计算相位 前者是离散傅氏变换（DFT）的快速算法，是有限长序列傅里叶变换的有限 点离散采样，从而实现了频域离散化，使频域采样按照数字运算的方法进行。后者是一个“化繁为简”的算法，将许多复杂的运算转化为一种“仅需要移位和加 法”的迭代操作。

（3）用 verilog 语言编码并利用 FPGA 实现 本作品用 FPGA 作处理器处理声音信号，利用了 FPGA 硬件并行的优势，在 每个时钟周期内完成更多的处理任务，超越了数字信号处理器的运算能力。

1.4 关键性能指标

（1）完成对实验室等室内环境的静止的鸣笛声源定位，并用摄像头以及舵 机云台对鸣笛者进行抓拍，抓拍成功率超过 90%，并且每次抓拍得到的鸣笛者偏 离照片中心不超过 50%.

（2）完成对实验室等室内环境的缓慢移动的持续鸣笛声源定位，并用摄像 头以及舵机云台对鸣笛者进行跟拍，跟拍成功率超过 90%，并且在跟拍过程中摄 像头内不丢失鸣笛者图像。

（3）完成对实验室等室内环境的快速移动的持续鸣笛声源定位，并用摄像 头以及舵机云台对鸣笛者进行跟拍，跟拍成功率超过 80%，并且在跟拍过程中摄 像头出现鸣笛者的时间超过跟拍总时间的 80%.

（4）对上述指标（1）中的抓拍在鸣笛开始的 0.5 秒内完成抓拍

1.5 主要创新点

（1）所有过程完全采用数字化的信号处理方式，所有通信均为数字通信， 所有处理的信号都为数字信号，相比于易受各种干扰的模拟信号系统，数字信号 处理抗干扰能力更强，通过多路信号并行处理来实现。

（2）利用了 FPGA 硬件并行的优势，打破了顺序执行的模式，在每个时钟周 期内完成更多的处理任务，超越了数字信号处理器（DSP）的运算能力。通过使 用尽可能多的麦克风通道，来提高定位的精确度。

（3）FPGA 良好的运算性能允许建立实时性良好的定位系统，可以做到追踪 高速行驶的鸣笛汽车。

（4）本项目将定位的空间由原有的二维空间拓展为三维空间，提高了追踪 定位的灵活性和准确性。

 

## 第二部分 系统组成及功能说明 / System Construction & Function Description

 

2.1 整体介绍

![system_diagram]({{ site.baseurl }}/assets/images/sound_source_dt1.png)
本系统由声源定位系统和图像抓拍系统两部分组成，其中声源定位系统 由麦克风阵列模块、PDM 解码模块、相位计算模块组成，后两个模块通过 FPGA 板实现，图像抓拍系统通过 OPENMV 实现。

声源产生声音信号，传送给麦克风阵列，编码产生 PDM 波，再通过接收 PDM 波的缓冲区，送入高阶 fir 滤波器实现对 PDM 的解码，然后将结果传入 相位计算模块，即先通过 FFT 算法进行频谱分析，再利用 CORDIC 算法计算 相位得到声源的坐标，最后通过基于 OPENMV 的图像抓拍系统显示声源位置 并抓拍。

2.2 各模块介绍

2.2.1 麦克风阵列模块

我们用到的硅麦型号为 SPW0690LM4H-1，这是一种小型、高性能、低功耗， 底部端口硅数字麦克风与单位 PDM 输出。包括一个声传感器，一个低噪声输入缓冲器和 sigma-delta 调制器。

它具有的特性：低失真/高 AOP、高信噪比、低功耗模式下低电流消耗、平 坦的频率响应、高驱动能力、射频屏蔽、支持双多路通道、极稳定的性能、全指 向性等等。在采集声音方面，在很宽的频带内增益保持一致，高保真的采集语音 信号，灵敏度高，能够检测到环境中微弱的声音信号。它的全指向性可以拾取各 方向的声音，对来自四面八方的声音同样敏感，特别适合用在本项目中。
![speaker_inside]({{ site.baseurl }}/assets/images/sound_source_dt2.png)
![demo]({{ site.baseurl }}/assets/images/sound_source_dt4.png)
2.2.2 处理器

本作品使用 Ego1 开发板作为处理器，型号为 Xilinx Artix-7 系列的 XC7A35T-1CSG324C FPGA。
![board_overview]({{ site.baseurl }}/assets/images/sound_source_dt5.png)
![configuration]({{ site.baseurl }}/assets/images/sound_source_dt6.png)
Xilinx 7系列的FPGA芯片内部集成了两个12bit位宽、采样率为1MSPS的ADC， 拥有多达 17 个外部模拟信号输入通道，为用户的设计提供了通用的、高精度的 模拟输入接口。
![XADC_diagram]({{ site.baseurl }}/assets/images/sound_source_dt7.png)
2.2.3 PDM 解码模块——基于高阶 fir 低通滤波器

PDM 的解码采用高阶 fir 滤波器的算法。PDM 编码虽然只有 0 和 1 两种电平， 但 PDM 编码保留了原始的未编码数据的所有频率分量，同时增加了高频噪声成 分 FIR 滤波器是数字信号处理系统中最基本的元件，它可以在保证任意幅频特性 的同时具有严格的线性相频特性，其单位抽样响应是有限长的，此系统稳定。根 据自顶向下的层次化、模块化的设计思想，将整个滤波器的设计划分为多个模块， 利用硬件描述语言 Verilog 进行各个模块的功能设计，并用 Matlab 软件设计 98阶滤波器各抽头系数。

对 PDM 编码进行傅里叶变换，得到的频率响应如下图：
![PDM_phase_domain]({{ site.baseurl }}/assets/images/sound_source_dt8.png)

由于声音定位系统是为了得到人耳可分辨的声音，或得到清晰的骑车鸣 笛声音，并且人耳可以分辨的声音频率为 20-20000Hz，而高于 20000Hz 的声音 信号是我们不需要的，所以我们的低通滤波器的通带频率设置为 0-20000Hz，截 止频率设置为 48000Hz，阻带频率设置为 100000Hz。PDM 信号经过该滤波器， 不仅可以实现 PDM 信号向 PCM 信号的解码，还顺带滤除了我们不需要的高频声 音信号。该 fir 滤波器的差分方程表达式为
![formula]({{ site.baseurl }}/assets/images/sound_source_dt9.png)
将原始信号进行编码，并经过 97 阶 fir 低通滤波器的信号与原始信号的对比 图如图 9、10 所示，其中绿色的为解码后的信号，蓝色的为原始信号。
![comparision]({{ site.baseurl }}/assets/images/sound_source_dt10.png)
由图可知，设计的滤波器较好的将编码后的信号还原为原始信号，并且原始 信号所包含的频率分量受到的影响较小。

用 VIVADO 软件编写 verilog 语言实现该 97 阶的数字滤波器，由于需要大量 的串行浮点运算，所以所消耗的时间较多，但通过硬件，可用并行运算进行处理。 通过计算，我们设计的 97 阶滤波器需要 97 个乘法器和 98 个加法器，具体代码 见附录。

2.2.4 相位计算模块

（1）通过 FFT 算法进行频谱分析

FFT 是离散傅氏变换（DFT）的快速算法，是有限长序列傅里叶变换的有限点 离散采样，从而实现了频域离散化，使频域采样按照数字运算的方法进行。

使用 Xilinx Vivado 内置的 Fast FourierTransform IP core 进行快速傅里叶变换， 配置使用 Radix-2 架构，使用 8 通道,每个通道一帧包含 512 个数据点，如图 11。
![step1]({{ site.baseurl }}/assets/images/sound_source_dt11.png)
输入的数据位宽为 16 位，输出则采用 Fixed Point、Unscale，同时为顺序输 出，配置如图 12。
![step2]({{ site.baseurl }}/assets/images/sound_source_dt12.png)
3）运用 CORDIC 算法计算相位

CORDIC 算法是一个“化繁为简”的算法，将许多复杂的运算转化为一种“仅 需要移位和加法”的迭代操作。

假设在 xy 坐标系中有一个点 P1（x1，y1），将 P1 点绕原点旋转θ角后得到 点 P2（x2，y2）。
![cordic]({{ site.baseurl }}/assets/images/sound_source_dt13.png)
于是可以得到 P1 和 P2 的关系：
![formula]({{ site.baseurl }}/assets/images/sound_source_dt14.png)
2.2.5 图像抓拍系统

在本作品中，使用分辨率为 640*480 的以数字图像传感器为核心的摄像头， 并使用具有角度不断变化并可以保持的舵机，构成图像抓拍系统。
![camera_and_motor]({{ site.baseurl }}/assets/images/sound_source_dt15.png)

OPENMV 通过接收 FPGA 串口发送的声源位置信息，从而控制舵机转向声源 的方向，使得我们使用的摄像头可以准确的对准声源，并下达指令给上位机（PC） 进行拍照或录像。照片将存储在上位机的内存中。

 

## 第三部分 完成情况及性能参数 / Final Design & Performance Parameters

 
（1）完成了在实验室对静止的鸣笛声源进行定位，并用摄像头以及舵机云 台对鸣笛者进行抓拍，抓拍成功率超过 95%，并且每次抓拍得到的鸣笛者偏离照 片中心不超过 30%，抓拍延时在 0.5 秒以内。照片效果如下图所示。
![photo1]({{ site.baseurl }}/assets/images/sound_source_dt16.png)
（2）完成对实验室的快速移动的持续鸣笛声源的定位，并用摄像头以及舵 机云台对鸣笛者进行实时跟拍，跟拍成功率超过 80%，并且在跟拍过程中摄像头 出现鸣笛者的时间超过跟拍总时间的 95%，跟拍效果如下图所示
![photo2]({{ site.baseurl }}/assets/images/sound_source_dt17.png)
3）上位机屏幕能够实时显示摄像头的情况，并且储存了抓拍到的鸣笛者 照片，以及持续鸣笛跟拍的视频。
## 第四部分 总结 / Conclusions

 
4.1 可扩展之处

（1）我们使用的 4 路数字麦克风阵列 PCB 板预留了额外的 28 个空焊的麦克 风接口，可以扩展至 32 路。从而可以尽可能地减小数字麦克风接收的误码率， 并且再次提高定位的精度。

（2）我们用来控制舵机云台的 OPENMV 拥有自带的摄像头，并且具有图像 识别等功能，将来可以使用 OPENMV 进行图像处理并配合声源定位系统进行综 合跟拍以及抓拍，从而提高跟拍的成功率以及抓拍的准确度。

（3）我们使用了高性能的上位机对跟拍和抓拍的图像进行实时显示，并保 存到上位机中。上位机将来可以对保存下来的照片进行二次分析，对抓拍到的车 辆进行车牌识别，并将违章记录上传到云端，并利用大数据进行监管，对一些违 章次数较多的车辆进行处罚。

（4）本项目使用到的 FPGA 芯片型号仅仅为 XILINX 的 A 系列入门级的 XC7A35T，如果更换为板载资源更多的型号，将会进一步提高声源定位运算的速 度。