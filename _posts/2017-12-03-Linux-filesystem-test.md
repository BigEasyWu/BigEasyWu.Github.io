---
layout: post
title: Linux文件系统
categories: Linux
description: 文件系统的描述
keywords: Linux
---

本文旨在归纳总结Linux文件系统的特性

  文件系统将磁盘空间划分为n个block，每个block大小为sectorsize的n倍，又将n个bloc分为一组，每组有自己独立的SuperBlock GroupBolck Blockbitmap Inodebitmap InodeTable DataBlock。
