---
date: 2023-05-22 12:26:40
layout: post
title: 如何搭建一款AI修图工具(去路人、修复)-LamaCleaner
subtitle: 
description: 
image: https://pic1.zhimg.com/70/v2-72d25333a97b4687957748d9a878f1aa_1440w.avis?source=172ae18b&biz_tag=Post
optimized_image: https://pic1.zhimg.com/70/v2-72d25333a97b4687957748d9a878f1aa_1440w.avis?source=172ae18b&biz_tag=Post
category: 
tags:
  - ai
  - LamaCleaner
author: imwfan
paginate: true
---






<!--page-->
话说十一长假到了，先祝福各位同学国庆快乐。今天我分享给大家一个炸裂的**AI修图**工具-**LamaCleaner**。

<u>它是由</u> <u>**SOTA AI**</u> <u>模型提供支持的<span data-search-entity="2">图像修复</span>工具。从照片中删除任何不需要的物体、缺陷、人物，或擦除并替换（由<span data-search-entity="3">稳定扩散</span>驱动）照片上的任何东西。</u>

总而言之，这个修图工具简直就是你拍照的得力助手，让你能够轻松应对各种拍摄需求，让每一张照片都完美无瑕。不管是快速修复、去背景，还是消除路人，它都能轻松搞定。快来试试吧，让你的十一旅行照片更加出彩！

先来看一下效果：
 ![](https://pic2.zhimg.com/v2-3ca04d665fde2941a27c33f2b5b97969_1440w.jpg) 

 ![](https://pic1.zhimg.com/v2-dd037ff7c0bdfad3b4fa11e7d7145d44_1440w.jpg) 

 ![](https://pic2.zhimg.com/v2-6585d633877286f4340a27d1db060a87_1440w.jpg) 

是不是非常炸裂，下面我将给各位同学介绍如何去使用。

**一、下载项目**

打开下面这个网站
`https://github.com/Sanster/lama-cleaner`
    ![](https://pic2.zhimg.com/v2-bca3b95bd71942e9c2fd07a347af4513_1440w.jpg)

    然后点击绿色的按钮
 ![](https://pic1.zhimg.com/v2-54a3c3d3ceac74d623279d28fb3c3ab6_1440w.jpg)

    点击左边的复制按钮
![](https://picx.zhimg.com/v2-7281fe6718050967efde34a2eb8ad4bf_1440w.jpg)

    接着我们打开一个文件夹，在目录上方输入cmd

 ![](https://pic2.zhimg.com/v2-c603b8b358ca4d36f12f1c198dcfbbab_1440w.jpg)

    接着输入这一段命令
   `git clone https://github.com/Sanster/lama-cleaner.git`

    如果没有下载Git的同学，动手能力强的可以观看我以前的文章

    [AutoGPT来了！手把手教你如何本地安装AutoGPT（建议收藏）](https://link.zhihu.com/?target=http%3A//mp.weixin.qq.com/s%3F__biz%3DMzU3MjAyNTI2MQ%3D%3D%26mid%3D2247484363%26idx%3D1%26sn%3D2f06a87f6e207accded6f832abb0a7b6%26chksm%3Dfcd67309cba1fa1f9d340ec0c70cd5c8d7156d7ece43fc48029fff8a88ac35b79c856fa95d9b%26scene%3D21%23wechat_redirect)

    如果git下载太慢了，也可以直接在我后台回复**LamaCleaner**获取项目文件

    ![](https://pic1.zhimg.com/v2-aae823535932859bfa48337a4d885e60_1440w.jpg)

    **二、下载依赖**

    输入以下命令，等待片刻。
    `pip install lama-cleaner`
  ![](https://pic3.zhimg.com/v2-c31234836cf56e18cecd111f60087c92_1440w.jpg)

    如果没有下载python的同学，也可以观看我以前的文章

  [AutoGPT来了！手把手教你如何本地安装AutoGPT（建议收藏）](https://link.zhihu.com/?target=http%3A//mp.weixin.qq.com/s%3F__biz%3DMzU3MjAyNTI2MQ%3D%3D%26mid%3D2247484363%26idx%3D1%26sn%3D2f06a87f6e207accded6f832abb0a7b6%26chksm%3Dfcd67309cba1fa1f9d340ec0c70cd5c8d7156d7ece43fc48029fff8a88ac35b79c856fa95d9b%26scene%3D21%23wechat_redirect)

    **三、运行项目**

    直接在输入框里面输入以下命令，如果你的电脑没有显卡的话，将下面的_--device=cuda_改为_--device=cpu_
  <div class="highlight"><pre>`lama-cleaner --model=lama --device=cuda --port=8080`</pre></div>![](https://pic3.zhimg.com/v2-a393b725839463df0215fd9ee4e0281c_1440w.jpg)

    最后进入这个界面就代表你运行成功了
   ![](https://picx.zhimg.com/v2-1deca7acf4227cc41c3efcb3891e5e53_1440w.jpg)

    最后在游览器输入下面这行代码，和我界面一样就代表你运行成功了。
   <div class="highlight"><pre>`http://127.0.0.1:8080/
</div>![](https://pic4.zhimg.com/v2-23d525bd8f9ff221f179ff6a87e2666d_1440w.jpg)

**四、简单实践**

现在我们简单的操作操作，熟悉一下流程

点击中间按钮，上传图片
![](https://pic3.zhimg.com/v2-7bb6b9d111e93a3365368e0429facb1a_1440w.jpg)

图片上传成功就是我现在这个样子
![](https://pic2.zhimg.com/v2-b7beeeb133dfc3a343e280dc5712a43f_1440w.jpg)

接着我们长按画笔，点击我们需要消除的部分
![](https://pic1.zhimg.com/v2-3d6e507520f8551580fbab8b75a03276_1440w.jpg)

最后就得到这个去除背景的图片了，是不是很神奇
![](https://picx.zhimg.com/v2-24bc51ef4a154b3f46658f8dea61212b_1440w.jpg)




<!--page-->











