---
layout: post
title: tmux的使用方法
tags: [tmux]
author: Xiang Li
---

# tmux的使用方法

在远程使用Linux服务器的过程中，由于网络或软件等各类原因，我们往往会断开与服务器的连接，这时候运行的命令也往往会因为网络中断而停止运行。**nohup**的使用能帮助我们解决很多问题，例如使用：`nohup command &`的方式能够将任务提交到后台中运行，等到运行完再进行查看。然而类似的方法在需要反复调试的过程中并不适用，尤其是当我们需要在一些有着特殊要求的集群上运行时更是无法满足要求（曾遇到过一个集群，十五分钟没有任何操作自动断开网络连接），而对于使用R进行大量数据操作时nohup也是无法满足要求的。这时候**tmux**就派上用场了。

## tmux的安装

如果有root权限，以Ubuntu为例，可以直接运行`sudo apt install tmux -y`进行安装。在安装了conda的情况下，也可以使用`conda install conda-forge::tmux`即可进行安装，同时建议安装在base环境中方便所有的环境使用。

## tmux最核心的用法

对于普通的用户来说，刨除掉那些相对来说有些花里胡哨的用法，最核心的命令个人认为只有四条：

* 创建sessions：`tmux new -s session_name` (session_name可以替换成任何你想创建的名字)
* 进入sessions：`tmux a -t session_name`
* 查看有哪些sessions：`tmux ls`
* 将session挂入后台：先按住**ctrl**，然后按住**b**，松开以后按一下**d**，即ctrl + b，d。

以上为我日常使用中最核心的命令，通常情况下，使用这四条命令足以满足大部分人的需求。

## 一些稍微进阶的用法

* 将当前session分成上下两部分：`tmux split` （快捷键ctrl + b，"）
* 将当前session分成左右两部分：`tmux split -h` （快捷键ctrl + b，%）
* 关闭其中的一个window：快捷键ctrl + b，x
* 在不同window之间切换：快捷键ctrl + b，上下左右方向键

