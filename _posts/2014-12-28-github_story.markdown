---
layout: post
title:  GitHub, Google Code, and other
category: technology 
---

# GitHub

2014.12

自从最近google code日益难以访问以来，我就一直在思考着替代的方案。然后在大徐的blog的指引之下，找到了github。

应该说使用git和svn相比，在现在的网络条件下，还是有不少优势的。我托管代码的目的，只是给自己的blog提供一个代码链接的地方而已，基本无意使用这个和他人协作。由于git的版本库是在本地的，即使github由于某种原因倒掉了，我也可以很方便的换一个替代品。

## GitHub导入其他版本库的代码

由于Google Code日益难以访问，因此我灵机一动，何不使用GitHub的导入功能，从Google Code中导出代码，然后再访问之？

以box2d为例，它的svn地址是：

https://box2d.googlecode.com/svn/

GitHub导入版本库功能的地址是：

https://import.github.com/new

## GitHub使用技巧

https://github.com/trending/python?since=monthly

这个可以看到python的月度趋势，便于分析技术热点。其他语言可以此类推。

## 搭建本地GitHub Blog服务

1.安装ruby

如果是Windows的话，还要在安装ruby之前，安装MSYS2，并安装make、gcc等应用。

install Ruby on Windows：

https://rubyinstaller.org/

2.修改gem的源

作为生活在水深火热的墙内人民，有必要进行下面一步修改gem的源，方便我们更快的下载所需的组件：

{% highlight bash %}
sudo gem sources --add https://gems.ruby-china.org/ --remove https://rubygems.org/
{% endhighlight %}

>**关于 Windows 下证书无法验证问题 (certificate verify failed)**   
>ruby 没有包含 SSL 证书，所以 https 的链接被服务器拒绝。   
>解决方法很简单，首先在这里下载证书 http://curl.haxx.se/ca/cacert.pem, 然后在环境变量里设置SSL_CERT_FILE这个环境变量，并指向cacert.pem文件。

3.安装ruby-dev

在ubuntu上可以这样：

`sudo apt-get install ruby-dev`

在windows下需要下载一个Dev-kit的安装包。但是Ruby的网站经常访问不了，所以其实还可以这样安装：

`gem install devkit`

4.安装jekyll和rdiscount

`gem install jekyll rdiscount`

5.进入blog的根目录之后,运行

`jekyll serve`

## Markdown

自从我在github建立blog以来，一直都在使用markdown语言。这里仅针对我使用过程中遇到的问题做一个笔记。

### markdown渲染器

Jekyll原生支持maruku，rdiscount，kramdown，redcarpet等markdown渲染器。其中的maruku由于已经不维护，在Jekyll 3.0以后被抛弃。

其实使用哪个markdown渲染器对外观的影响都不大，外观更多的是css的事情，因此够用就好。

开始用的是大徐模板里的rdiscount，最近发现该渲染器不支持代码中的空行。

接着换成kramdown，但是又不支持HTML表格里的rowspan。

然后换成redcarpet，而redcarpet会对下划线进行改写，需要加上no_intra_emphasis扩展以关闭之。修改提交之后，github又告诉我，马上要停用redcarpet，统一使用kramdown。

于是又换回kramdown，反复折腾之后，才发现kramdown可以支持rowspan，但是它的语法要求非常严格，必须符合XHTML才行。

错误写法：`<td rowspan=2>`

正确写法：`<td rowspan="2">`

### 语法高亮

之前一直使用pygments作为语法高亮的着色器。近来，github推荐我使用rouge。经过一番研究才发现，pygments是用python写的，难怪windows环境下的Jekyll老是无法集成pygments。

### StackEdit

StackEdit是一个在线的markdown编辑工具，被CSDN等网站所使用。

官网：

https://stackedit.io/

# Google Code

2013.12

一直以来，在sohu写blog都面临一个很大的问题。代码全贴上的话，太占篇幅，而以附件形式提供代码，又不为blog系统所支持。

之前的解决办法是使用网盘，但是网盘时间一长之后，就不再可用，而我显然也不可能经常去刷新网盘，使得其随时可用。再者，网盘也不是专业的代码托管方式。

好在现在有了google code。

# Google code的倒掉

2015.3

昨天收到了Google Code即将关闭的邮件，很是震惊。不过想想也在情理之中，用过GitHub之后，对Google Code也就不那么有爱了。就像用了svn，对cvs无爱；用了git，对svn无爱一样。不过对svn的无爱，只是部分的。如果是公司性质的小团队开发的话，仍然推荐svn，因为权限管理比较方便，概念也比git简单。而如果是不方便上网的环境的话，git的优势就比较明显了。

# Other

## SVN

一直以来都是在Windows下使用TortoiseSVN客户端来操作svn。现在到了linux环境下，由于找了一圈貌似也没有什么很给力的GUI客户端。所以只有对svn的命令行使用做一些研究了。

 好在之前一直使用英文版的TortoiseSVN，因此在使用svn help后，基本操作方面倒是没有遇到什么大的问题。只有commit的时候，除了commit之外，还要update一下，然后当前目录的svn状态才会切换到提交了新版本之后的状态。

## Google Reader倒掉之后

2014.1

好久没上Google Reader了，这几天有空想上去，才发现Google Reader已经在去年的7月被关闭了。记得当初自己还曾基于Google Reader的API，做了一个Android上的RSS阅读器，当然完成度只有40%左右。没想到Google Reader这么一关，这个作品也就彻底废品了。。。

之前使用Google Reader，主要的目的是浏览cnbeta。但cnbeta的rss是摘要型的，必须随时在线才可查阅正文。而我的碎片时间主要是上下班赶车的路上，这个场景是没有上网条件的。幸好，现在有人做了一个全文的rss：http://cnbeta.catke.com/

但是无论是这个全文rss，还是cnbeta本身的rss，都有条目数量的限制。超过这个数量的老条目，也就无法获得了。怎么样才能像Google Reader那样，无遗漏的保存一段时间以来的所有条目呢？倘若是以前的话，你必须拥有一台时刻在线的PC，不间断的刷新rss。

而现在的话，你可以有别的选择，比如ifttt.com。ifttt是If this then that的缩写。国内的山寨版本有“如果云”。这些网站允许你自己创建一定的规则，来完成一定的动作。具体到当前的目标，就是创建以下规则：一旦rss的内容有更新，就立即将新内容以电子邮件的方式发送到我的邮箱里。

剩下的问题就简单了，找一个好用的邮箱。使用邮箱的手机客户端，将邮件下载到手机上，这样每天的早报就有了:)

# 我的AI简史

2018.5

上一篇技术简史还是2014.12的事情，时间又过了3年半。除了在智能硬件上捣鼓了一年多以外，这几年就主要是在AI上折腾了。

2016.3的AlphaGo大战李世石事件，虽然新闻效应很大，对我的震撼也很大，但对于我从事AI，实际上并无直接关联。

我的AI路的开端实际上非常偶然。某天闲逛，无意发现了一个开源app的UI使用了毛玻璃特效。作者特意指出该特效使用了Gauss filter。

接着便搜索到了一个介绍Gauss filter的blog，这是该博主OpenCV系列的其中一篇，于是从此入了CV的坑。这大概是2016年3月底的事情，距离AlphaGo大战李世石不过一周左右。

2016.4，公司开始涉足大数据研发，但暂时和我没有交集。

2016.5，参加某安防展，看到了CV在停车场中，对于车辆跟踪的应用，对CV兴趣更浓。同时得知同事L是此中高手。

2016.7，在OpenCV的官方手册中，发现了ML一词。接着找到了吴恩达早期的ML讲义，从此入坑ML。

2016.8，大数据项目进入开展阶段，我自告奋勇，负责算法的设计。从此成为职业AI人。

2016.10，入坑NLP。

2016.12，入坑DL。但是由于初期ML的基础较差，因此在看完MLP之后，暂时停了一阵子。2017.5以后，全面转入DL。

2017.10，入坑RL。

2018.3，入坑ASR。

# WebKit

WebKit的代码可以从它的官网www.webkit.org下获得。

在以下网页可以获得webkit向各种GUI移植的相关信息。

http://trac.webkit.org/wiki

由于获得的代码比较新，所以在linux平台下常有一些组件由于过于古老而导致编译失败。所以需要使用yum或者apt-get之类的工具从网上更新相关的组件。这里不推荐使用RHEL或者CentOS之类的服务器版本，因为服务器版本为了追求稳定性，不但组件不是最新的，就连网上的组件源也不是最新的。

可以使用ubuntu 9.04桌面版，不过里面缺少很多开发用的组件，除了

http://trac.webkit.org/wiki/BuildingGtk

列出的之外，还有不少组件需要下载。主要有：

1)autoconf

2)libtool

3)gtk-doc-tools

4)libgail-dev

# GraphQL

GraphQL是在Facebook内部应用多年的一套数据查询语言和runtime。

官网：

http://graphql.org/

中文官网：

http://graphql.cn/

代码：

https://github.com/facebook/graphql

参考：

https://zhuanlan.zhihu.com/p/20638731

GraphQL and Relay浅析

https://mp.weixin.qq.com/s/4AnLu0m2IILGwyPyuK37Fg

基本操作：Go创建GraphQL API

# DL参考资源

https://mp.weixin.qq.com/s/bgP_xMfi3hXayscf9D5JIg

谷歌提出Sim2Real：让机器人像人类一样观察世界

https://mp.weixin.qq.com/s/aqfwn0kiXbZwVDVhHXBAXQ

谷歌大脑研究员玩转汉字RNN：神经网络生成新华字典

https://mp.weixin.qq.com/s/GxWOuIf25JQnQoCstVyGLQ

李飞飞团队提出OpenTag模型：减少人工标注，自动提取产品属性值

https://mp.weixin.qq.com/s/HaTNeqblwp2mALznK2nvMA

用脑电波控制智能假肢：如何利用深度学习技术进行EGG数据分类

https://mp.weixin.qq.com/s/iAMYqJjlMWAvFq4Hddh4ig

从0上手Kaggle图像分类挑战：冠军解决方案详解

https://mp.weixin.qq.com/s/LtWMGRBk2sbPDjeC9PmJ7g

弱监督学习下的商品识别：CVPR 2018细粒度识别挑战赛获胜方案简介

https://mp.weixin.qq.com/s/ZIDiFrN3qQV4u-m9Wr3wiA

斯坦福完全可解释深度神经网络：你需要用决策树搞点事

https://mp.weixin.qq.com/s/M7w7tMVd23YToIW7DypYjA

用DL实现Bug自动归类：微软研究院提出DBRNN-A

https://mp.weixin.qq.com/s/KX85CCpYrXFOvdTU5Q4Frg

阿里巴巴论文提出针对影视作品的语音情感识别信息融合框架

https://mp.weixin.qq.com/s/1R9ttaKnXso_quIGTY1nfA

海康、UCLA、北理联合提出3D DescriptorNet：可按条件生成3D形状，克服模式崩溃

https://mp.weixin.qq.com/s/-4b3u02KiIt5i4Yzz-Ed3g

从信息论的角度理解与可视化神经网络

https://mp.weixin.qq.com/s/NJf5e25tvT_xKXLD7UY1AQ

MySQL智能调度系统。这篇blog其实和MySQL关系不大，算是DL在负载均衡方面的应用吧。

https://mp.weixin.qq.com/s/D0n3xY0k25d6Ouf4mCi7Nw

让AI识别语义空间关系：斯坦福大学李飞飞组提出“参考关系模型”

https://mp.weixin.qq.com/s/_P-4hhd7QiOwrR_uBCPbZg

脑洞大开的机器视觉多领域学习模型结构

https://mp.weixin.qq.com/s/yQG0983RjQHIkt9oBlkDqQ

瞎谈CNN：通过优化求解输入图像

https://mp.weixin.qq.com/s/iZZHmxGFHQHk1rlzMzDQcg

训练深度神经网络失败的罪魁祸首不是梯度消失，而是退化

https://mp.weixin.qq.com/s/yvHZ9hVueYUKsMXcNQQzmQ

深度学习会被可微分编程取代？

