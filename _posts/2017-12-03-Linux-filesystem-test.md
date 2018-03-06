---
layout: post
title: Linux文件系统
categories: Linux
description: 文件系统的描述
keywords: Linux
---

本文旨在归纳总结Linux文件系统的特性

# 描述

  * 文件系统将磁盘空间划分为n个block，每个block大小为sectorsize的n倍，又将n个block分为一组，每组有自己独立的SuperBlock GroupDescriptors Blockbitmap Inodebitmap InodeTable DataBlock。


**inode** :Index node 索引节点 存放指向的blocks组成的文件的元信息（大小，权限，时间戳，地址指针）。

**Inodebitmap** : 对位标识描述对应indoeblock的可用状态。  

**Blockbitmap** ：对位标识描述对应datablock的可用状态。

**SuperBlock** ：记录整个文件系统的相关信息datablock与Inodeblock的总量以及使用量,block与Inode的大小，文件挂载的相关信息。（*每个groupblock都可能含有superblock除第一个以外，其余为备份*）

`dumpe2fs -h /Device (查看超级块信息)`

**GroupDescriptors** : 描述该group的各项信息，主要有group起始与结尾的block号，该组block以及inode的使用状况。

`dumpe2fs /Device （查看组描述）`

**InodeTable** : inode固定大小为128B，文件系统格式化便自动创建，以条目格式存放在inodetable的block中，存放文件的元信息。

**DataBlock** : 实际存放文件内容的地方

 *目录特殊于普通文件，datablock中存放的是该目录下的文件名（子目录）和其对应的Inodenumber*
