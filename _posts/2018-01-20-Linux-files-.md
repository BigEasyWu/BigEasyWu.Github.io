---
layout: post
title: Linux文件权限与目录权限
categories: Linux
description: 文件权限的梳理
keywords: Linux
---

梳理 Linux 中文件权限与目录权限的区别

> 权限的本质是管理 U(user) G(group) O(other) 对目录或文件 Block块的资格
# 文件权限

### r 权限
可读取 DataBlock 中的内容

### w 权限
可对 DataBlock 中的内容进行更改

### x 权限
可对文件进行运行

# 目录权限

### r 权限
可查看目录的 DataBlock 块，里面存储目录下文件以及子目录的名称已对应的 inode 号，拥有 r 权限能查看名称

### w 权限
可新建目录下文件或子目录；删除目录下文件或子目录；重命名重定位目录下文件或子目录

### x 权限
是否能成为工作目录的标准，拥有权限后可读取目睹对应 DataBlock 中 Inode 号，并加载inode节点读取目录下文件或子目录的元信息

**开放查看目录至少需要开启 r ，x 权限**

**开放修改目录需要开启全部权限**
