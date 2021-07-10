---
title: Hexo 常用命令说明
top: false
cover: false
toc: false
mathjax: false
date: 2021-07-10 17:59:20
author: 血魂S
summary: Hexo 常用命令说明
categories: Hexo
tags:
    - Command
---

# Hexo 常用命令

#### 新建一个 Markdown 文档

```bash
hexo new "markdown_name"
```

#### 新建一个页面

```bash
hexo new page "page_name"
```

#### 新建一个草稿

```bash
hexo new draft "draft_name"
```

#### 发布草稿

```bash
hexo publish "draft_name"
```

#### 清除缓存文件 (`db.json`) 和已生成的静态文件 (`public`)

```bash
hexo clean
```

#### 生成静态文件

```bash
hexo g
```

#### 本地运行静态文件

```bash
hexo s
```

#### 部署到远端

```bash
hexo d
```

#### 备份到远端

```bash
hexo b
```

#### 查看命令帮助

```bash
hexo help
```

#### Windows 常用组合命令

```bash
hexo g && hexo s
```

```bash
hexo clean && hexo g && hexo s
```

```bash
hexo clean && hexo g && hexo d
```

```bash
hexo clean && hexo g && hexo d && hexo b
```

###### **官方使用说明**（[https://hexo.io/zh-cn/docs/commands](https://hexo.io/zh-cn/docs/commands)）

