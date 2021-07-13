# 本地运行网站

要在本地运行网站，你需要安装Ruby以及Jekyll，详情请看[**这里**](https://jekyllrb.com/docs/installation/)

**安装**

输入

```
git clone https://github.com/Zenfendson/OpenHW.git 
```

在本地的根路径下打开powerershell,输入`Jekyll bundle`等命令创建依赖

这个项目的依赖通过Gemfile管理，Gemfile.lock里面有着当前Jekyll版本下对应的依赖，你需要根据你的Jekyll版本更新，尝试`bundle update`指令

成功后输入`bundle exec Jekyll serve`运行，也可在命令后加入后缀`--livereload`, 可是执行`_config.yml`的更改

# 如何添加新的文章

添加文章只需要简单的添加markdown文件，不需要参与到很多的html的开发，甚至不需要本地环境配置

有时加入新文章会发生gitpages新文章的部署出错，这是还是考虑本地化运行看看，或者把文件删了重来

## 添加文本

在_post路径下创建新的.md file 注意命名格式为：**Year-Month-Day-name.md**

Jekyll 自动根据文件名的前缀对文章排序，该时间也对应文章发布时间。

注意文件名应为全英文且**小写**，并且**name**这部分不能与其它某一文件相同，该框架使用这部分名字生成对应的html

## 添加图片

在`_asset/image/`下存放所有图片，文件名应为全小写，推荐一篇文章单独建立一个文件夹存放图片，方便管理
图片大小比例推荐为3：2

# 网站的大致结构和配置

本网站使用了GitHub pages 默支持的Jekyll编译工具开发静态网站

### 那Jekyll是如何进行编译的呢？相关的文件起什么作用呢？

### 关于 `_config.yml` 文件

该文件描述了网站的相关配置，一些基本设置需要在其中更改，如用到的插件，作者和联系方式等等。

### 关于 `index.html` 文件

网站的home界面由本文件设置

### 关于 `_includes` 文件夹

该路径下存放了网站要用的各种小插件

### 关于 `_layouts` 文件夹

该路径下存放了网站相关页面的布局

### 关于 `_pages` 文件夹

该路径下存放了网站页面的模板

### 关于 `_site` 文件夹

存放Jekyll编译过后的网站的html

其它路径暂不做过多介绍

[参考视频](https://www.youtube.com/watch?v=Zt_QzSbyDcw&t=897s)
