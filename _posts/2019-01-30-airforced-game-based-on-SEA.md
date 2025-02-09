---
layout: post
title:  "基于SEA的飞机大战游戏"
author: XUP-2020
categories: [ project, 2020competition ]
image: assets/images/airforce_game_cover.jpg
---
作者：卞思格；宋长骏；陈炜鑫



第一部分 设计概述

 

1.1 设计目的

我们设计了一款基于 SEA 的飞机大战游戏。飞机大战游戏是一款休闲益 智类游戏，既简单又耐玩。在初始界面，我们有开始游戏、重新开始、皮肤 选择和结束游戏四个选项。开始游戏后，玩家可以用游戏手柄方便的控制飞 机在屏幕上向任意方向移动，通过躲避子弹和射击敌机得分，在屏幕左上角 可以看到当前生命和得分。

1.2 应用领域

最近的一些复古游戏网上商店吸引了许多喜欢老式电子游戏的买家。一 些爱好者一直在收集复古游戏产品，一些普通玩家也开始收集旧式磁带和 CD，还有小时候玩过的游戏机。

虽然复古游戏只占全球 1090 亿美金游戏行业的一小部分，但确是非常 有吸引力的缝隙市场。该游戏平台可以作为一个复古游戏机使用，经过后期 加工改良，可以将游戏移植到专用游戏机或手机等设备上，供玩家使用。这 款飞机大战游戏，可以放松心情，释放压力，提高反应能力。

1.3 主要技术特点

（1） 在 BRAM 资源较少的情况下，采用了图片压缩编码的方式，以较少 的数据量来表示原来的像素矩阵。

（2） 我们编写了游戏的主菜单和控制逻辑，游戏功能丰富，界面美观。

（3） 我们外接了自制游戏手柄，可以直插在开发板上，方便地控制游戏。

1.4 关键性能指标

（1） 游戏界面美观，飞机图标清晰，游戏动画显示流畅；

（2） 游戏手柄上的摇杆与按键灵敏度高、指令延迟小

1.5 主要创新点

（1） 使用了自制游戏手柄，相比普通按键，能更方便地控制游戏，提升用 户体验。

（2） 在板载 BRAM，资源较少的情况下，采用了图片压缩编码的方式，以 较少的数据量来表示原来的像素矩阵。

第二部分 系统组成及功能说明

 

2.1 整体介绍

系统硬件由 SEA 开发板（型号 xc7s25ftgb196-1）、游戏手柄拓展板和 HDMI 显示屏组成。FPGA 读取按键和摇杆的状态，来控制游戏显示的内容， 其中，FPGA 通过 IIC 方式来读取摇杆的状态。游戏总体控制模块分为按键 功能控制、主菜单控制、游戏逻辑控制和文字图片信息显示控制四个方面。 根据玩家不同的指令，HDMI 屏上显示相应的内容。

![system_diagram]({{ site.baseurl }}/assets/images/airforce_game_1.png)

![RTL_invivado]({{ site.baseurl }}/assets/images/airforce_game_2.png)

2.2 各模块介绍

根据总体系统框图，给出各模块的具体设计说明。

（1） 游戏总体控制模块

按键功能控制：不同的按键对应不同的指令，该模块主要负责按键消 抖与指令转化。

主菜单控制：游戏初始界面的主菜单有开始游戏、重新开始、皮肤选 择和结束游戏四个选项。可以通过按键上下移动光标，选择不同功能。

游戏逻辑控制：该模块主要进行了游戏规则的设计。

显示模块：主要负责文字显示和飞机图标、子弹显示。

（2） HDMI 显示驱动模块：驱动 HDMI 屏，在屏上流畅的显示游戏界面。

（3） 游戏手柄驱动模块：驱动手柄上的 PCF8591 芯片，输出摇杆的位置状 态。

（4） IIC 通信模块：实现游戏手柄和 FPGA 的通信，FPGA 读取 PCF8591 输出的数据。

 第三部分 完成情况及性能参数

 

显示的菜单如图 3 所示，可以上下移动光标选择相应的功能。游戏界面如图 4 所示，实现了摇杆控制飞机朝任意方面移动。图片清晰，画面显示流畅，指令 延时小，并且游戏规则正确，可以给玩家良好的游戏体验感。完整作品如

第四部分 总结

![game_introduction]({{ site.baseurl }}/assets/images/airforce_game_3.png)
![game_introduction]({{ site.baseurl }}/assets/images/airforce_game_4.png)
![game_introduction]({{ site.baseurl }}/assets/images/airforce_game_5.png)

4.1 可扩展之处

A.利用板载的 esp32 模块，实现脱机下载。

B.可以存储一些其他游戏，设计个游戏选择菜单。

C.利用板载的蓝牙模块，实现联机游戏。

D.增加游戏音乐部分

> It would seem the claim could also extend to die cut books in general, as we can’t find anything sooner, but do let us know in the comments if you have further light to shed on this! Such books are, of course, still popular in children’s publishing today, though the die cutting is not now limited to mere outlines, as evidenced in a beautiful 2014 version of the same Little Red Riding Hood story. 