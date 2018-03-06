---
layout: post
title: Linux文件系统
categories: Linux
description: 文件系统的描述
keywords: Linux
---

本文旨在归纳总结Linux文件系统的特性

# 描述
文件系统将磁盘空间划分为 n 个 block，每个 block 大小为 sectorsize 的 n 倍，又将 n 个 block 分为一组，每组有自己独立的 SuperBlock GroupDescriptors Blockbitmap Inodebitmap InodeTable DataBlock。

# 名词解释

**inode** :Index node 索引节点 存放指向的 blocks 组成的文件的元信息（大小，权限，时间戳，地址指针）。

**Inodebitmap** : 对位标识描述对应 indoeblock 的可用状态。  

**Blockbitmap** ：对位标识描述对应 datablock 的可用状态。

**SuperBlock** ：记录整个文件系统的相关信息 datablock 与 Inodeblock 的总量以及使用量, block 与 Inode 的大小，文件挂载的相关信息。（*每个 groupblock 都可能含有 superblock 除第一个以外，其余为备份*）

`dumpe2fs -h /Device (查看超级块信息)`

**GroupDescriptors** : 描述该 group 的各项信息，主要有 group 起始与结尾的 block 号，该组 block 以及 inode 的使用状况。

`dumpe2fs /Device （查看组描述）`

**InodeTable** : inode 固定大小为 128 B，文件系统格式化便自动创建，以条目格式存放在 inodetable 的 block 中，存放文件的元信息。

**DataBlock** : 实际存放文件内容的地方

 *目录特殊于普通文件，datablock 中存放的是该目录下的文件名（子目录）和其对应的 Inodenumber *
