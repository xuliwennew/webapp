# WebApp开发实战系列 01-版本管理工具 #

> 作者：徐礼文  2016/10/5 12:20:11 

----------

# Git简介 #
> Git是什么？
> 
> Git是目前世界上最先进的分布式版本控制系统（没有之一）。
> 
> Git有什么特点？简单来说就是：高端大气上档次！

## 一、Git的诞生 ##

> 很多人都知道，Linus在1991年创建了开源的Linux，从此，Linux系统不断发展，已经成为最大的服务器系统软件了。
> 
> Linus虽然创建了Linux，但Linux的壮大是靠全世界热心的志愿者参与的，这么多人在世界各地为Linux编写代码，那Linux的代码是如何管理的呢？
> 
> 事实是，在2002年以前，世界各地的志愿者把源代码文件通过diff的方式发给Linus，然后由Linus本人通过手工方式合并代码！
> 
> 你也许会想，为什么Linus不把Linux代码放到版本控制系统里呢？不是有CVS、SVN这些免费的版本控制系统吗？因为Linus坚定地反对CVS和SVN，这些集中式的版本控制系统不但速度慢，而且必须联网才能使用。有一些商用的版本控制系统，虽然比CVS、SVN好用，但那是付费的，和Linux的开源精神不符。
> 
> 不过，到了2002年，Linux系统已经发展了十年了，代码库之大让Linus很难继续通过手工方式管理了，社区的弟兄们也对这种方式表达了强烈不满，于是Linus选择了一个商业的版本控制系统BitKeeper，BitKeeper的东家BitMover公司出于人道主义精神，授权Linux社区免费使用这个版本控制系统。
> 
> 安定团结的大好局面在2005年就被打破了，原因是Linux社区牛人聚集，不免沾染了一些梁山好汉的江湖习气。开发Samba的Andrew试图破解BitKeeper的协议（这么干的其实也不只他一个），被BitMover公司发现了（监控工作做得不错！），于是BitMover公司怒了，要收回Linux社区的免费使用权。
> 
> Linus可以向BitMover公司道个歉，保证以后严格管教弟兄们，嗯，这是不可能的。实际情况是这样的：
> 
> Linus花了两周时间自己用C写了一个分布式版本控制系统，这就是Git！一个月之内，Linux系统的源码已经由Git管理了！牛是怎么定义的呢？大家可以体会一下。
> 
> Git迅速成为最流行的分布式版本控制系统，尤其是2008年，GitHub网站上线了，它为开源项目免费提供Git存储，无数开源项目开始迁移至GitHub，包括jQuery，PHP，Ruby等等。
> 
> 历史就是这么偶然，如果不是当年BitMover公司威胁Linux社区，可能现在我们就没有免费而超级好用的Git了。

## 二、集中式vs分布式 ##

![](http://img.blog.csdn.net/20131003101333421?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvamFja3lzdHVkaW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

## 三、Git经典的开发流程 ##

![](http://img.blog.csdn.net/20131003103359359?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvamFja3lzdHVkaW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)


----------


# Git基本术语 #


### 1.分支（Braches） ###
一个分支意味着它是一个独立拥有自己历史版本信息的代码线。你可以从已有的代码中生成一个新的分支，这个分支与其余的分支完全独立。默认的分支叫做master。用户可以选择一个分支，选择一个分支叫做Checkout.

### 2.提交（Commit） ###
当你提交你的更改到Git库中，它将创建一个新的提交对象。这个提交对象会有一个新版本的唯一标识。本次修订后，可以检索，例如，如果你想看到一个旧版本的源代码。每个提交对象中都会包含修改者和提交者，从而有可以确定是谁做了改变。修改者和提交者，可以是不同的人。

### 3.头（HEAD） ###
头是一个象征性的参考，最常用以指向当前选择的分支。

### 4.仓库（Repository） ###
仓库包含了随着时间的推移和各种不同的分支和标签不同版本历史。在Git仓库的每个副本是一个完整的信息库。你可以从仓库中获取你的工作副本。

### 5.修订（Revision） ###
表示代码的一个版本状态。Git通过用SHA1 hash算法表示的ID来标识不同的版本。每一个 SHA1 ID都是160位长，16进制标识的字符串。

### 6.标记（Tags） ###
标记指的是某个分支某个特定时间点的状态。通过标记，可以很方便的切换到标记时的状态。

### 7.URL ###
URL决定了仓库所在的位置。

### 8.工作树/区（Working tree） ###
工作区中包含了仓库的工作文件。您可以修改的内容和提交更改作为新的提交到仓库。

### 9.暂存区（Staging area） ###
暂存区是工作区用来提交更改（commit）前可以暂存工作区的变化。暂存区包含了工作区的一系列更改快照，这些快照可以用来创建新的提交。

### 10.索引（Index） ###
索引是暂存区的另一种术语。

### 11.工作区，暂存区和版本库的关系 ###
![](http://img.blog.csdn.net/20130928111447703?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvamFja3lzdHVkaW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)