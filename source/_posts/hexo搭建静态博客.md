---
title: hexo搭建静态博客(1)
date: 2021-11-17 15:18:09
tags:
 - 技术
---

# 1.hexo简介
基于node.js的静态网页生成器，可以做博客，产品展示，文本文档等；基于markdown。
拥有大量的插件和主题。
官网地址：https://hexo.io/zh-cn/
github地址：https://github.com/hexojs
hexo示例：https://github.com/hexojs/awesome-hexo

### 原理
自己写好md文件，通过hexo转化为静态html文件，通过github pages将静态文件托管

# 2.安装

## 2.1安装准备
需要node.js、npm
需要git

## 2.2 安装
`$ npm install -g hexo`

## 2.3 创建一个hexo项目
```
$ cd /f/Workspaces/hexo/
$ hexo init
```
## 2.4 创建一篇文章

```
$ hexo new "firstblog"
$ hexo g # 生成
$ hexo s # 启动服务
```
可以看到自己的博客了
# 3.上传到github上托管
`hexo d`
##3.1 创建仓库
创建名字为“用户面.github.io”的仓库
##3.2 配置ssh key
生成密钥
`ssh-keygen -t rsa -C "邮件地址"
`
找到.ssh\id_rsa.pub文件
将密钥复制到github上
进入个人设置 -> SSH and GPG keys -> New SSH key：

测试是否成功
```
$ ssh -T git@github.com # 注意邮箱地址不用改
```
提示
```You’ve successfully authenticated, but GitHub does not provide shell access.```

说明成功
配置账号

```
$ git config --global user.name "liuxianan"// 你的github用户名，非昵称
$ git config --global user.email  "xxx@qq.com"// 填写你的github注册邮箱
```
##3.3配置hexo项目config文件
```
deploy:
  type: git
  repository: git@github.com:liuxianan/liuxianan.github.io.git
  branch: master
```