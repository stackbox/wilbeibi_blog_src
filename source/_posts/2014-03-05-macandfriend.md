---

title: Mac程序员和他的朋友们
date: 2014-03-05
categories: Collection
tags: [miscellaneous]
description: Mac编程环境的配置和常用软件
---


## 为什么要用Mac
Linux内核作者[Linus早就开始使用Mac了](http://www.zdnet.com/torvalds-switches-to-apple-1139183867/)（虽然面对记者表现的很扭捏）。Gnome的作者更是理直气壮[叛逃Linux投奔Mac](http://tirania.org/blog/archive/2013/Mar-05.html)。如你所知，Mac OSX是[开发者们的最爱](http://programmers.stackexchange.com/questions/51670/why-do-programmers-use-or-recommend-mac-os-x)。因为它一方面有非常棒的用户体验，一方面是基于Unix，尽得shell的益处，又避免了Linux下种种繁琐。什么，太贵了，看看[MacTalk是怎么说的](http://www.cnblogs.com/chijianqiang/p/mmac.html)。

工欲善其事，必先利其器。这里分享下我的Mac应用和配置。

<!--more-->

基于原则:
+ 尊重软件版权，能购买正版的，请尽量购买正版
+ Don’t Shave Yaks, 不要因为花太多时间配置工具而浪费工作的时间
+ 奥卡姆剃刀，如果一项功能需求只是偶尔用一下，就别配置了。

## 应用&效率
### Dropbox
大名鼎鼎的Dropbox，无需赘述。是居家旅行，出门必备同步神器。Dropbox较之Google Drive更轻量级，更快，适合在多平台同步正在编辑的文档或者代码。记得Google Drive是没有Linux版客户端的，而Dropbox有！而且，Dropbox的文件分享链接是直接指向文件的，对于在remote terminal上工作且尚不熟悉scp和rsync的同学来说是福音（`rsync --daemon`效果可以媲美Dropbox）。相比之下，Google Drive 更适合来存放资料，因为它能搜索文档内关键词。
### Mou
我见过最好的MarkDown编辑器，简洁，漂亮，可配置，支持MathJax公式编辑。
![](http://mouapp.com/images/Mou_Screenshot_1.png)


### Evernote
笔记软件，我主要用它在收藏平时看到的好的RSS文章，Prime版的多人协作，幻灯片功能也很赞。
### Pocket
众多的ReadItLater软件中的一个，推荐Pocket是因为它的文本抽取出来的格式比较好，在移动端上的App做的也很出色。

### Kaleidoscope
比较多文档之间的差异。一个命令行党应该忠诚的效忠用`diff`来比较文件，但是Kaleidoscope真的太好用了，关键是它不仅能逐行比较，还能一块块匹配着比较，还能两个文件夹比较，还能Merge文件。

### Alfred 2
这是一个神奇的快速启动软件，就为了它，你就值得买个Mac。MacTalk里谦虚的称它为“神兵利器”。你可以用它来：
* 打开任何应用
* 查找文件
* 执行shell命令
* 当计算器用
* 直接写email
* 在Google/Amazon/Wikipedia上搜索条目
* ... ...  
嗯，以上只是它的普通功能，只有这些还不足以称之为伟大。Alfred之牛掰，在于其可编程的第三方workflow插件机制，这样可以在Alfred里搜豆瓣图书，搜Github仓库，查看天气或PM2.5，搜索自己的Evernote笔记，查API文档，一切能想到的，[都可以实现](http://www.zhihu.com/question/20656680)。
![](http://i.imgur.com/XDWlNGv.png)
![](http://i.imgur.com/3hpPO97.png)

### TextExpander
文本自动补全的插件，自定义好触发的关键词，每次输入这些关键词的时候，biu~，想打的字就全弹出来了。把自己的电话，邮箱，或者写邮件的模板存进去，能避免很多重复的劳动。
### Popclip
文字选中弹出扩展。每次选中文字后，可以快速的把选中文字进行复制，粘贴，查找，加入笔记本等等。
### RescueTime (Time sink)
默默的运行在后台，告诉你你的时间都浪费在哪儿了。每周发邮件告诉你你在哪个软件，哪个网站上花了多少时间，这一天/周的效率有多高。你可以定义什么是有效率的行为（比如用Evernote写笔记，用Emacs写代码）加分，哪些是偷懒的行为（看美剧，刷豆瓣）扣分。
### LimeChat
IRC应用，选它是因为其他的IRC应用都太！！难！！用！！了！！
### AppCleaner
删软件清理残余。
### Moom
还在像傻帽一样花半天找到窗口边框笨手笨脚地缩放大小么？用Moom吧，能快速排好窗口，自定义想要的窗口大小。
### The unarchiver
普通解压用`tar`命令，但如何有非UTF-8的中文编码，还是用unarchiver比较方便（命令行下得用`find` + `iconv`写一长串，太虐心）
## 编程&配置
### Dash
查文档利器。作者在新版本对它收费$20，丧心病狂，但从长远考虑，还是值得的。能配合Alfred用，省心。
### Textmate
bundle功能很好用，方便快速掌握一门语言。写前端代码很方便。其他时候，还是用Vim/Emacs吧。
### TotalCommander
命令行党都有过每天得把Terminal拖来拖去的苦恼。TotalCommander正是这样一款下拉式的终端，类似Gnome下的Guake，也支持多窗口，强烈推荐。
### iTerm2
不管你用bash，zsh还是tcsh，有一个好用的Terminal软件是十分必要的，iTerm2就正是一个优秀的终端。好看，配置性极强，有很多方便的功能，戳[这篇文章](http://www.yangzhiping.com/tech/iterm2.html)。
### Homebrew
Mac下的包管理器，和ports平分天下。想装什么东西，尽管`brew install` 就好。
### Z shell (tmux及配置文件)
基于bash的shell，被誉为The Last Shell。配置当然很复杂，不过不要紧，拿来主义一下，用[oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh)一行代码安装。

### z/autojump
每天还在为输各种`cd`而浪费时间？[z](https://github.com/rupa/z) 是个极为方便的小配置，它把用户访问过的目录存在记录里，每次输入`z <访问过的目录的关键词>`，就biu的一声到了。autojump也是类似的工具。



![](http://i.imgur.com/XFdMrp9.jpg)


---------

PS: 这篇文章只是兴之所至，所以很多东西还没来得及说，我会长期更新
Wed Mar  5 01:21:05 EST 2014
