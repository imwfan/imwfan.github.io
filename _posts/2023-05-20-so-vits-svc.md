---
date: 2023-05-15 18:26:40
layout: post
title: AI孙燕姿？学习如何使用so-vits-svc打造属于自己的AI歌手！
subtitle: 
description: 
image: https://pic1.zhimg.com/70/v2-e0144f5212aa8cd006451a3a9d36e493_1440w.avis?source=172ae18b&biz_tag=Post
optimized_image: https://pic1.zhimg.com/70/v2-e0144f5212aa8cd006451a3a9d36e493_1440w.avis?source=172ae18b&biz_tag=Post
category: 
tags:
  - ai
  - so-vits-svc
author: imwfan
paginate: true
---






<!--page-->
最近刷短视频刷到AI孙燕姿唱的《遇见》，还原度还挺高。于是我就去研究了一下，没想到效果还不错。那么，如何通过AI技术来打造属于自己的AI歌手模型呢？

首先我们要安装UVR_v5.5.0这个软件来处理声音。因为使用模型进行推理的话，你需要一段已经演唱好的声音垫进去。

**一：前期准备**

### 1.安装CUDA驱动

首先我们要检查显卡的CUDA Toolkit版本，<span data-search-entity="0">命令行界面</span>输入：nvidia-smi，回车。通过表格右上角的CUDA Version来确定你应该下载的CUDA Toolkit驱动版本

![](https://pic4.zhimg.com/v2-a5aa38659179ebacd01ed57540e7f4f7_1440w.jpg)

CUDA驱动地址：[<span class="invisible">https://</span><span class="visible">developer.nvidia.com/cu</span><span class="invisible">da-toolkit-archive</span><span class="ellipsis"></span>](https://link.zhihu.com/?target=https%3A//developer.nvidia.com/cuda-toolkit-archive)

选择“自定义”，然后全选，点击下一步
![](https://pic4.zhimg.com/v2-79b62f3d12f97424a9541a236cd4b1b3_1440w.jpg)

 一直下一步就行了
![](https://pic3.zhimg.com/v2-ac26d5065b78d6c337328e365386e516_1440w.jpg)

### 2.安装ffmpeg

下载地址：[<span class="invisible">https://www.</span><span class="visible">gyan.dev/ffmpeg/builds</span><span class="invisible"></span>](https://link.zhihu.com/?target=https%3A//www.gyan.dev/ffmpeg/builds)

**操作方法：**

1. 在Win10开始菜单按钮上鼠标右键单击，弹出菜单选择“系统”

![](https://pic3.zhimg.com/v2-b3405272ac231ffe608d81480918a986_1440w.jpg)

2. 在“系统”界面，选择右边的“高级系统设置”

![](https://picx.zhimg.com/v2-3b39f091eee15eff712d2171eb18ab33_1440w.jpg)

3. 在对话框中，点击右下角的“<span data-search-entity="3">环境变量</span>”按钮

![](https://pica.zhimg.com/v2-d642b7a005c215902635324728d8b01e_1440w.jpg)

4. 选择上面<span data-search-entity="4">用户变量</span>的Path一行，然后点击下面的“编辑”按钮

![](https://pica.zhimg.com/v2-d0201bbd236d9160758a8ea86ca3aa74_1440w.jpg)

5. 点“新建”按钮，把刚才的“D:\Program Files\ffmpeg-5.1.2-full_build\bin”路径复制进去，然后确定。

![](https://picx.zhimg.com/v2-2e53d22c8f892ba7a82f9d77512e4587_1440w.jpg)

指定ffmpeg路径

6. **重启电脑**，再验证刚才两项内容是否已经运行。

*   **检查CUDA核心有没有输出：nvcc -V**
*   **检查FFmpeg：ffmpeg**

和我下图一样就代表你安装成功

![](https://pic3.zhimg.com/v2-214f14392671cae720631305dbc3af04_1440w.jpg)

**3.安装UVR**

双击安装文件UVR_v5.5.0_setup.exe，需要安全同意。如果有Windows的安全筛选，就选择更多，仍坚持运行。

相关算法文件可以在软件的设置页面的Download Center下载

**![](https://pic4.zhimg.com/v2-e03d577bbb90defb25375a684bfc9db3_1440w.jpg)**

**4.安装So-VITS-SVC 4.0**

### **整合包地址：**[<span class="invisible">https://</span><span class="visible">pan.baidu.com/s/12u_LDy</span><span class="invisible">b5KSOfvjJ9LVwCIQ</span><span class="ellipsis"></span>](https://link.zhihu.com/?target=https%3A//pan.baidu.com/s/12u_LDyb5KSOfvjJ9LVwCIQ)

**解压码：公众号**后台回复9004即可

将整合包解压到电脑硬盘中（路径中尽量不要包含中文），整合包内已经搭建好了运行所需的所有环境依赖，你无需自己手动搭建环境。如果你用的老版本的模型的话

把旧版的**G_模型**和**Kmeans聚类模型**放到新版整合包的以下目录：**.\logs\44k**

把旧版模型对应的**config.json**（在configs文件夹内）放置到新版的以下目录：**.\configs**

**二、声音处理**

**1.提取人声**

So-VITS-SVC 4.0只能识别WAV格式的音频文件，所以在需要把你声音的格式转换成WAV格式。可以使用这个工具进行转换：[<span class="invisible">https://www.</span><span class="visible">aconvert.com/cn/audio/m</span><span class="invisible">p4-to-wav/</span><span class="ellipsis"></span>](https://link.zhihu.com/?target=https%3A//www.aconvert.com/cn/audio/mp4-to-wav/)  

![](https://picx.zhimg.com/v2-e1aea46c61abcb67dea22adf1326717b_1440w.jpg)

使用UVR去掉背景音（需要处理两次）

Select Input输入你的文件地址，Select Output是你文件处理后的地址

第一次：如下图配置即可

![](https://pic1.zhimg.com/v2-6949edeab0df5ab4322e20eb2eef9a5c_1440w.jpg)

第二次，去除合声

![](https://pic2.zhimg.com/v2-2cafc71edb51b0d058db20fe8fd30f07_1440w.jpg)

## 2.切割音频

不过因为音频太长，不要超过三十秒，很容易爆显存，需要对音频文件进行切片。

我们通过 Audio Slicer这个工具实现音频切分 。

![](https://pic2.zhimg.com/v2-bdb0fff63d7f1bfafbeb6e70f6b0ebc9_1440w.jpg)

得到以下文件

![](https://picx.zhimg.com/v2-d799f370cf0d291e05744cfa9923dfa3_1440w.jpg)

项目的 so-vits-svc-4.0/dataset_raw 目录下创建一个文件夹，将刚才处理的数据放进去。

**三、模型训练**

运行so-vits-svc<span data-search-entity="1">根目录</span>的【启动webui.bat】打开Web UI界面，切换到训练Tab下面。然后点击识别数据集，这时候上面就会展示你数据集文件夹的名字，也会是你模型的名字。

![](https://pic1.zhimg.com/v2-341e872c3bee02d91c8702114a37f494_1440w.jpg)

点击写入<span data-search-entity="2">配置文件</span>，显示配置写入完成就可以了

![](https://pic4.zhimg.com/v2-818c7c1883a6853542148c77506e660d_1440w.jpg)

点击从头开始训练

![](https://picx.zhimg.com/v2-2ddd940d0c3a8a7fed9d5e8f7baa224b_1440w.jpg)

切换推理Tab，点击刷新

![](https://pic3.zhimg.com/v2-a0f9d0c0a93729e73a92c8a1fac58ffa_1440w.jpg)

点击G开头的模型，选择配置文件，然后加载模型

![](https://pic3.zhimg.com/v2-3d178ec36a4ce0419ff429b5888336d4_1440w.jpg)

上传你要训练的音频

![](https://pic3.zhimg.com/v2-593bdf656d554fa1cf808d71889b1fb0_1440w.jpg)

变调这里女转女，男转男可以不变

![](https://pic4.zhimg.com/v2-6e3fbff2b81a78b3b2e3049f837ba117_1440w.jpg)

最后点击转换，就完成了。

![](https://pic1.zhimg.com/v2-3e3821d533fecd0587d94af409d3f786_1440w.jpg)

如果转换后，声音不清晰，沙哑，有明显的电流声。回到训练界面，点击继续训练，直到你满意即可。

![](https://picx.zhimg.com/v2-5c9c7a9b4ec0eed38c93adedfa26decb_1440w.jpg)

不过，要想创造出具备高质量的AI歌手模型，并不是一件容易的事。毕竟，一个歌手的音质和唱腔，不仅仅取决于声音本身，还取决于其思维、经验、音乐和文化素养等多方面的因素。因此，在进行训练过程中，我们需要结合AI技术和专业音乐知识，进行反复的实践和训练，才能打造出完美的AI歌手模型。

<!--page-->











