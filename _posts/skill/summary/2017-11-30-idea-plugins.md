---
layout: post
title: IDEA常用插件集锦
date: 2017-11-30 21:09:35 +0800 
categories: 工欲善其事必先利其器
tag: idea
description: java开发必备常用IDEA插件
keywords: java 插件 idea 
---
* content
{:toc}

`IDEA` 是 `java web` 的开发神器，这里罗列些自己高频使用的插件，希望也能显著的提高各位的编码体验和工作效率。

<!-- more -->

<!-- TOC -->

- [Grep Console](#grep-console)
- [GitToolBox](#gittoolbox)
- [IdeaVim](#ideavim)
- [AceJump](#acejump)
- [Log Support 2](#log-support-2)
- [MyBatis plugin](#mybatis-plugin)

<!-- /TOC -->

## Grep Console 

开发过程中，我们常用控制台输出日志来定位错误，但是冗长、实时滚动的控制台日志，往往会淹没我们所要关注的内容，这款插件可以很好的为你排忧。主要功能如下：

* 高亮查询匹配的文本
* 过滤不关心的记录行
* 匹配到文本时播放语音
* tail 文件

1. 安装后，控制台会有这个图标按钮

  ![](https://tu-img-1.aixinxi.net/o_1c06j18bk14k9e6n1m9m139l1okca.png-w.jpg)

2. 点击按钮可以打开配置页面, 上图出现的日志屎黄高亮，就是下面正则匹配 `WARN` 级别日志, 红色的 `ERROR`, 白色的 `INFO`, 甚至如果你想特别关注某些第三方 `jar` 包的日志输出，可以像我这里一样匹配对应包路径里面的关键字，我这里是关注 `JRebal` 日志

  ![](https://tu-img-1.aixinxi.net/o_1c06it5601feerkvj0neg41itba.png-w.jpg)

---

## GitToolBox

功能如下：

* `Git` 状态显示，底部状态条、工程管理器，显示当前分支超前或者落后远程仓库多少个版本

* 可配置定时拉取同步分支



## IdeaVim

编辑区增加 `Vim` 快捷键，从此编码如丝般顺滑

## AceJump

`AceJump` 可以快速的导航光标到编辑器任意可视区内， 按 `Ctrl + ;`, 输入任意想聚焦的位置相应字母，即可跳转

 ![](https://tu-img-1.aixinxi.net/o_1c06jt9ljevg21f5966a1nf5a.png-w.jpg)

## Log Support 2

快速生成常用日志代码片段，下面以 `slf4j` 作为日志门面为例，即使开始类里面没有声明日志成员变量，只要输入 `loge + TAB` 就可以快速生成 `LOGGER`(变量名可配置) 成员变量

* 支持常用日志组件

 ![](https://tu-img-1.aixinxi.net/o_1c084bi721pgu1d45h6t1r7f15dua.png-w.jpg)

  ```java
            private static final Logger LOGGER = LoggerFactory.getLogger(Test.class);
   ```

 ![](https://tu-img-1.aixinxi.net/o_1c06latfmtov12hq183u1dga12t4a.gif-w.jpg)

## MyBatis plugin

快速在 `Mapper` 和 对应命名空间的 `xml` 之间跳转

   ![](https://tu-img-1.aixinxi.net/o_1c06l4pqtdht16k73a2pvga3ka.gif-w.jpg)
