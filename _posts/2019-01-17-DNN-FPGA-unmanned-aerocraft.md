---
layout: post
title:  "DNN-FPGA 加速器的无人机目标探测软硬件协同优化"
author: XUP-2020
categories: [ project, 2020competition ]
image: assets/images/DNN_FPGA_unmanned_aerocraft_cover.jpg
---
基于 DNN 的目标探测算法应用非常广泛，比如自动驾驶、目标追踪、人脸探 测与识别、视频语义分析、行人计数等，但是基于深度学习的目标探测算法有着计 算量大、部署困难等问题，在移动端这个问题尤其明显。针对这个问题，我们提出 了一套软硬件协同设计的流程，包含软硬件协同模型设计，软硬件协同量化，软硬 件协同硬件设计以及软硬件协同系统设计。

**基于 DNN-FPGA 加速器的无人机目标探测软硬件协同优化**

**by&nbsp;姜伟雄，孙豪&amp;刘心哲**

&nbsp;

基于 DNN 的目标探测算法应用非常广泛，比如自动驾驶、目标追踪、人脸探 测与识别、视频语义分析、行人计数等，但是基于深度学习的目标探测算法有着计 算量大、部署困难等问题，在移动端这个问题尤其明显。针对这个问题，我们提出 了一套软硬件协同设计的流程，包含软硬件协同模型设计，软硬件协同量化，软硬 件协同硬件设计以及软硬件协同系统设计。软硬件协同模型设计即针对 FPGA 的 特点搭建适合放在 FPGA 上部署的网络。我们针对 FPGA 的硬件特点总结出一套 适合在 FPGA 上部署的算子，然后将该算子构建成轻量级的神经网络。量化即将 浮点型表示的网络模型转换成用整型表示并计算，软硬件协同量化在量化时充分 考虑硬件的特点，使量化后的网络可以高效地用硬件实现。软硬件协同硬件设计即 在前面的软硬件协同模型设计以及量化的基础上，设计高效的针对特定网络的硬 件加速器。最后，完成系统构建后我们分析系统的性能瓶颈，并将系统瓶颈转移到 硬件加速器中。

在本设计中，我们首先设计了一个轻量级的目标探测网络 SkrNet，在 DJI 无 人机航拍数据集上以 1.4MB 的参数量获得了 73.9%的精度。然后将 SkrNet 的权重 量化到 int6，特征图量化到 uint8，并且在测试集上取得了跟浮点型完全相同的精 度。接着，我们设计了针对 SkrNet 的专用硬件加速器，并且针对 int6-uint8 乘法实 现了 DSP 复用技术，可以让一个 DSP 每个周期计算两个非独立的乘累加，使吞吐 量翻倍。最后我们完成了完整系统的构建并进行软硬件协同系统优化，使图像预处 理时间下降 75%，系统吞吐量增加 30%。我们在 Xilinx 的 Ultra96 和 ZCU104 两个 平台上分别达到了 60fps 和 120fps 的性能，这也是保证精度(&gt;70%)条件下目前世 界最快的速度。相比目前的最优设计，我们的速度达到 2.4 倍，精度提升 1.5%，能耗降低 40%。

关键词:FPGA;DNN 加速器;DNN 量化;软硬件协同设计

![image_5]({{ site.baseurl }}/assets/images/article_12/image_5.png)

**指导老师、参赛队员与作品合影**

&nbsp;

![image_1]({{ site.baseurl }}/assets/images/article_12/image_1.png)

**作品全貌**

![image_2]({{ site.baseurl }}/assets/images/article_12/image_2.png)**作品特写**

![image_2]({{ site.baseurl }}/assets/images/article_12/image_2.png)

**作品特写**![image_3]({{ site.baseurl }}/assets/images/article_12/image_3.png)

**作品特写**

![image_4]({{ site.baseurl }}/assets/images/article_12/image_4.png)

**作品特写**
