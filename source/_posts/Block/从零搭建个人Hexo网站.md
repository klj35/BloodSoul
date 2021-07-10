---
title: 从零搭建个人 Hexo 网站
top: false
cover: false
toc: true
mathjax: false
date: 2021-07-10 18:43:02
author: 血魂S
summary: 从零搭建个人 Hexo 网站，使用 Matery 主题进行美化，同时部署到 GitHub，并使用备份插件进行快速备份
categories: Hexo
tags:
    - Command
    - Config
    - Zero2One
---

# 一、准备工作

#### a. 下载并安装 [**Node.js**](https://nodejs.org/zh-cn/download/)

打开 cmd 验证安装是否成功

```bash
node -v
```

显示出对应版本号，表示安装成功

![](https://raw.githubusercontent.com/klj35/BloodSoulBlockImage/main/img/image-20210710194608900.png) 

查看 NPM 是否安装成功，输入如下指令

```bash
npm -v
```

![](https://raw.githubusercontent.com/klj35/BloodSoulBlockImage/main/img/image-20210710200815627.png) 

#### b. 下载并安装 [**Git 客户端**](https://git-scm.com/downloads)

打开 cmd 验证安装是否成功

```bash
git --version
```

显示出对应版本号，表示安装成功

![](https://raw.githubusercontent.com/klj35/BloodSoulBlockImage/main/img/image-20210710195514143.png) 

新建博客工程要存放的文件夹，我这边使用 Hexo_Matery，在Hexo_Matery文件夹内，鼠标右键->Git Bash Here，输入如下指令，设置淘宝源

```bash
npm config set registry https://registry.npm.taobao.org
```

# 二、搭建 Hexo

#### a. 初始 Hexo 指令集

```bash
npm install hexo-cli -g
```

#### b. 初始化 Hexo 博客

```bash
hexo init
```

#### c. 进行本地预览博客

```bash
hexo s
```

打开浏览器输入：[http://localhost:4000](http://localhost:4000)，能够正常预览，表示搭建成功！

![](https://raw.githubusercontent.com/klj35/BloodSoulBlockImage/main/img/image-20210710211816860.png) 

# 三、将 Hexo 部署到 GitHub

#### a. 配置 GitHub 环境

> - 注册 GitHub 账号：[https://github.com/](https://github.com/)
> - 设置本地 Git 与 远端 GitHub 的密钥
> 	- 在你的博客文件夹内（我的示例为`Hexo_Matery文件夹`）鼠标右键->Git Bash Here
> 	- 配置你的 git 全局账号，命令输入如下：
> 		- git config --global user.name "你的Github用户名"
> 		- git config --global user.email "你的Github邮箱" 
> 	- 配置 ssh key，命令输入如下：
> 		- ssh-keygen -t rsa -C "你的Github邮箱"    (生成新的公钥)
> 		- less ~/.ssh/id_rsa.pub    （查看公钥，并将其复制）
> 	- 在 [GitHub 设置界面](https://github.com/settings/keys)填入密钥
> 	- 验证密钥是否通过，命令输入如下：
> 		- ssh -T git@github.com
> - 新建一个仓库资源 [https://github.com/new](https://github.com/new)，该资源的 SSH Clone 地址后面要用到

#### b. 编写 Hexo 博客的部署项

> - 在 `Hexo_Matery文件夹` 内根目录下，打开 `_config.yml` 文件
> - 在 deploy 项，按如下输入：
> 	- <img src="https://raw.githubusercontent.com/klj35/BloodSoulBlockImage/main/img/image-20210710220753733.png" style="zoom: 80%;" /> 
> 	- `url` 就是项目的 SSH Clone 地址，`branch` 为需要部署到的分支名称

#### c. 部署并推送到 GitHub

> - 在 `Hexo_Matery文件夹` 内根目录下，鼠标右键->Git Bash Here
> - 安装 GitHub 部署插件，输入：npm install hexo-deployer-git --save
> - 进行 GitHub 部署，输入：hexo clean && hexo g&& hexo d
> - 在你刚才创建的 GitHub 资源项目中，选择 `Settings`
> - 在 `Settings` 界面中选择左下角的 `Pages`，选择对应分支（示例为 `master`），然后点击 `Save`
> - <img src="https://raw.githubusercontent.com/klj35/BloodSoulBlockImage/main/img/image-20210710222300137.png" style="zoom: 50%;" /> 
> - 中间生成的链接即是你的博客地址

#### d. 处理部署到 GitHub 上排版丢失问题

> - 复制 c 步骤最后生成的地址
> - 在 `Hexo_Matery文件夹` 内根目录下，打开 `_config.yml` 文件
> - 将地址填入 `url` 项
> - 并将 `root` （没有这手动写一个）项改成 "/you_project_name/"
> - 在 `Hexo_Matery文件夹` 内根目录下，鼠标右键->Git Bash Here，输入：hexo clean && hexo g&& hexo d
> - <img src="https://raw.githubusercontent.com/klj35/BloodSoulBlockImage/main/img/image-20210710223221224.png" style="zoom:80%;" /> 

# 四、使用 Matery 主题美化

详细使用方式请参见我的 [Matery 主题使用说明](https://klj35.github.io/BloodSoul.github.io/2021/07/02/block/matery-zhu-ti-shi-yong-shuo-ming/)

# 五、进行备份

> - 在 `Hexo_Matery文件夹` 内根目录下，鼠标右键->Git Bash Here
> - 安装备份插件，输入指令：npm install hexo-git-backup --save
> - 在 `Hexo_Matery文件夹` 内根目录下，打开 `_config.yml` 文件，添加如下配置
> - <img src="https://raw.githubusercontent.com/klj35/BloodSoulBlockImage/main/img/image-20210710225730474.png" style="zoom:80%;" /> 
> - 仓库逗号后面的是备份成的分支名称
> - 在 Git Bash 内输入命令：hexo b
