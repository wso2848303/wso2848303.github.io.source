---
title: vscode sync setting 配置
date: 2019-07-22 18:35:55
tags: ["vscode"]
---

## 插件名称——Settings Sync

## 关于3.4.0版本

我是使用的这个版本（不如说是今天才开始使用的），百度了很多的使用教程，发现与我现在使用的版本在配置上还是有比较大的区别的，主要就是老版本需要手动去配置一个git gist，然后把这个gist id配置到vscode； 然而在我使用的过程中，发现这一步完全不需要，只vscode中安装插件，然后登录GitHub账号，就会进行自动配置。

以及其中非常重要的一点是，github中手动申请的gist id，填入vscode的配置中后，发现会出现gist id 错误的问题。

## 功能

跨平台同步vscode所使用的配置（包括插件）

使用前提： vscode、 github账号

1. vscode 下载___Settings Sync___插件
2. shift+alt+u 打开配置页（这个快捷键同时也是日后配置完成后的上传）
3. 点击login登录github账号并授权
4. 配置页可以进行部分配置
5. 同时也可以通过配置settings.json来进行配置

___具体配置参数可以通过插件首页来查询___