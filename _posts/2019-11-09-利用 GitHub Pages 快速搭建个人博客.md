---
layout:     post
title:      利用GitHub Pages + jekyll快速搭建个人博客
subtitle:   处女博，献给这篇教程
date:       2019-11-09
author:     阿望
header-img: img/tag-bg.jpg
catalog: true
tags:
    - 教程
---

## 前言

想搭建自己博客很久了（虽然搭了也不见得能产出多频繁）。

最初萌生想写自己博客的想法，想象中，是自己一行一行码出来的成品，对众多快速构建+模板式搭建不屑一顾，也是那段时间给闲的，从前后端选型、数据库敲定，到实际代码编写，越写越发现自己要弄的东西太多太多，而且，没有模板，没有原型，当初我的审美还是很欠缺的，每写一行css都是怀疑的，痛苦的，直到一年以后，我的博客还处于代码阶段，且中间好几次因为工作太忙，长时间没碰它，想法越来越弱，直至搁浅。

这段时间换了工作，昨天发版，今天闲的不行，于是这想法突然又冒出来了，网上闲逛逛，发现了这篇小白式教程，曾经对快速构建+模板式搭建不屑一顾的我，经过岁月的沉淀，现在的想法：嗯，真香！

于是，我的处女博，就贡献给这篇教程吧，也算是感谢一下老板这篇傻瓜式教程了。

## 博客搭建

博客搭建主要依赖于教程[《利用 GitHub Pages 快速搭建个人博客》](https://www.jianshu.com/p/e68fba58f75c)，她的步骤都写得很详细，按着步骤来基本上问题不大，这里做个步骤总结：

> 1. 最基本的，你得先有个GitHub账号

已经有账号的往下看，没有的同学点击[这里](https://github.com/)去申请

> 2. fork我的仓库到你的git里面

进入[我的仓库](https://github.com/awang0608/awang0608.github.io)将仓库fork到你的git上：点击右上角的fork按钮，等一会儿页面自动刷新。

![image](https://awang0608.github.io/img/2019-11-09/fork-from-qiubaiying.jpg)

> 3. 修改setting

进入你自己的仓库-setting：修改你的仓库名为 你的仓库名.github.io（这里有个问题，稍后解释），改这里：

![image](https://awang0608.github.io/img/2019-11-09/modify-setting.jpg)

注意：一定是你的仓库名.github.io，不然的话，你会发现git不会正确发布，比如我把仓库名改成了aaa.github.com，这个时候，下面GitHub Pages那块儿显示的发布地址就是 *https://awang0608.github.io/aaa.github.com/* ，而不是我们预期的 *https://awang0608.github.io/* 了。

走到这一步之后，就可以用自己的仓库地址访问了，接下来就是粗暴的删我的文章！删我的图片！删我的配置！将这一切，改成自己的，就可以啦。

## 遇到的问题

整个想法从萌生到开始搭建到搭建完成，差不多是一下午的时间，在按照教程走的这个过程中，发现了几个小问题，幸而都一一解决，在这里将解决办法奉上，希望对看到这篇教程的小伙伴们能有一些帮助。

> 最后一步，到改了仓库名为自己的仓库名后，使用github.io地址访问一直报404

教程给出的解决方案并没有解决我的问题，百思不得其解，还是百度大法好呀，要解决404的问题，需要将原仓库名awang0608.github.io修改成awang0608.github.com，等个几秒钟强刷https://awang0608.github.io/地址，就能看到网站正常显示。

![image](https://awang0608.github.io/img/2019-11-09/question-404-solve.png)

> 使用百度分析工具[Baidu Analytics](https://tongji.baidu.com/web/welcome/login?castk=LTE%3D)的时候，因为对分析网站不熟悉，找了很久找不到自己的ba_track_id

在这里：

![image](https://awang0608.github.io/img/2019-11-09/ba-track-id.png)

我也不知道这个马赛克打了有什么意义，但就是，想打。

> Gitalk集成后报错：Error: Issues are disabled for this repo.

差不多就是下面这个鬼样子：

![image](https://awang0608.github.io/img/2019-11-09/issues-disabled-for-repo.png)

据说导致的原因是fork了别人的仓库，是不会有自己issues的，所以

解决办法：重新建一个空白项目，把代码移过去，这里需要注意的是，新建空白项目后，注意修改setting，主要有三个地方：一是setting里面的仓库名（关键点见步骤3），这个时候可以毫不犹豫地把.com后缀舍弃，直接使用.io后缀了，二是Features里面的Issues记得勾选（一般是默认勾选），三是需要自己设置GitHub Pages，GitHub Pages->Source:选择master，这时候不要动页面，它会自己刷新。

![image](https://awang0608.github.io/img/2019-11-09/modify-github-pages.jpg)

刷新过后

![image](https://awang0608.github.io/img/2019-11-09/after-modify-github-pages.jpg)

注意哦，页面若是显示类似 ==Your site is ready to be published at https://awang0608.github.io/qiubaiying.github.io/.== 就是错的哦（这一点前面提到过，我这儿是因为没有改仓库名），要显示  ==Your site is published at https://awang0608.github.io/==，并且前面有个绿色的勾，才能正确的用这个地址显示。

> Gitalk集成后报错：Error: Not Found.

![image](https://awang0608.github.io/img/2019-11-09/gitalk-not-found.png)

这个问题主要是前几个问题导致的，在解决404问题的时候，将后缀io改成了com，然后自然而然地，_config.yml文件中关于Gitalk的配置也改成了.com结尾，而且，git上Settings-> Developer settings->OAuth Apps里注册的Homepage URL也填成了.com结尾，但是，在解决Issues are disabled for this repo问题的时候，我们是直接抛弃了.com，使用.io的，所以会出现Not Found的情况，这个时候，将，_config.yml文件中关于Gitalk的配置和Homepage URL改回.io结尾。

> 项目跑起来后发现右侧多了一个滚动条，体验极其不友好.

这个就很easy啦，调试器打开搜查元素发现是article元素设置了overflow-x:hidden导致的，虽然我没明白为什么教程中的网站没有出现这个问题，但是我大手一挥，删掉了这个样式。

## 个性设置

在网站顺利跑起来的后几天里，我分别给网站新增了小桃心、打赏和浏览量展示的功能，后续看情况，如果有更多的小设置能俘虏我的话，我会陆续将它们加进来，变成一个花里胡哨的网站，可别嫌弃呀[手动捂脸哭]。

#### 小桃心

小桃心的源代码是在网上找的，原功能是鼠标点击冒心心，我给新增了一个随机冒心心的功能（新增了一个定时器，慢慢跑），还让它变大了点，直接设置定时器的话，会发现如果停留在当前页之后切换到其他页面稍微长一点的时间，就有满屏的小桃心，晃瞎了我，于是加了一个判断，最多冒10个出来，嗯，心情愉悦，有兴趣的朋友可以查看源码：[sweetHeart.js](https://blog-static.cnblogs.com/files/moonLightcy/sweetHeart.js)，或者直接引用，就可以在你的网站也加上这些小心心咯~

#### 打赏

打赏功能随便一百度就有无数的教程，这里我就不再赘述，只是提醒一下，在引用的时候最好不要加前面的协议字符，否则容易404，还纳闷半天为什么不得行，还有就是，同一个网站上的微信和支付宝的付款图，微信随时能访问，支付宝的偶尔会报403，这个暂时还没找到解决的办法。

#### 浏览量

浏览量展示使用的是不蒜子的脚本，方便，简单。不蒜子自己的定位是：极简网页计数器，两行代码，搞定计数。（悄咪咪地说，不止计数极简，连它的[官网](http://busuanzi.ibruce.info/)也真真儿是极简）

要使用不蒜子必须在页面中引入busuanzi.js，不蒜子可以给任何类型的个人站点使用。鉴于前端的引用惯性，我将这个脚本引用在了footer.html的最后，然后，在page.html中找个地方添加了代码来显示站点总访问量：

```
    // footer.html
    <script async src="//busuanzi.ibruce.info/busuanzi/2.3/busuanzi.pure.mini.js"></script>
    //page.html
    <div>本站总访问量<span id="busuanzi_value_site_pv">0</span>次</div>
```
站点总访问量有两种计算方式：
> pv的方式，单个用户连续点击n篇文章，记录n次访问量

> uv的方式，单个用户连续点击n篇文章，只记录1次访客数

这两种使用方式分别对应id：busuanzi_value_site_pv和id：busuanzi_value_site_uv；

在post.html中也添加了代码来显示单页面访问量：

```
    <span style="font-size: 14px;">
        <span id="busuanzi_container_page_pv">
            共<span id="busuanzi_value_page_pv">0</span>次阅读
        </span>
    </span>
```
不蒜子自身只提供标签+数字，至于显示的style和css动画效果，可随意发挥，只需要保证id正确即可。

## 友情提示

在根据教程配置Homepage URL的时候是直接填写的https://awang0608.github.io/，但实际上需要填写的整个仓库的git地址：https://github.com/awang0608/awang0608.github.io。

## 结语

历经一下午将博客搭建好，历时3小时做了这篇总结，虽然是小白教程，但自己解决了教程中遇到的问题，还是比较开心的，接下来准备做的是优化，因为我个人作为一个前端来讲，确实觉得这个博客的主题吧，其实总体来讲还是很不错的，只是我实在无法接受页面布局上一张图占了整个浏览器的70%，其实大家能发现，点进一张博文详情，首先是看不到多少有效内容的，都被一张大图占据了空间，有效信息非常少。

仔细看了看项目代码，理清了它的实现，发现要改起来还是比较简单的，而且，我还可以做一些我自己比较喜欢的优化，所以，我准备动起来了。

可能有人会有疑问，不喜欢这个主题那为什么不更换一个主题呢？好吧，其实是因为我看了jekyll提供的主题，发现，这个已经很不错了，没有找到更喜欢的[手动捂脸哭]，当然，如果自己审美在线的话，我还是可以为jekyll贡献我自己的主题的。

如果有想去研究一下主题的，去这里：[jekyll主题官网](http://jekyllthemes.org/)。

正文 完

插个小曲，今天中午起来发现我的朋友做了一个自动领喵币和蚂蚁森林自动领能量的应用，对他的崇拜瞬间上升了一个档次，不是因为他做应用的技术，而是因为他在那么忙的公司都还有空把它做出来！大佬就是大佬，思想觉悟都跟尔等小民不一样。