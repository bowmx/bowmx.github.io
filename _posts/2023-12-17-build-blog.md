---
layout: post
title: 个人博客搭建
date: 2023-12-17 23:00 +0800
categories: [Web, 博客搭建]
tags: [blog]   
---
这是这个site的第一篇blog, 我们以这个折腾了一天的东西为始, 分享一下来自对web技术几乎零基础的人的经验.

## 环境搭建
### Repo侧
- 这里我是用的是免费的github pages和开源的'Jekyll Chirpy Theme'.
- 我们直接进入[Github-chirpy-starter](https://github.com/cotes2020/chirpy-starter), 然后点击右上角 `Use this template` -> `Create a new repository`然后在`Repository name` 一栏中填入<USRE_NAME>.github.io, 然后你就会在自己github的repositories看到自己刚刚创建好的repo, 就此Repo环境搭建完成.
- 直接在浏览器中访问<USRE_NAME>.github.io,就应该可以看到一个模板页面了.

> 你也可以通过fork别的repo来达成这一结果, 就不再赘述了.

### Local侧
- 首先我们需要安装ruby
    ```shell
    sudo apt install ruby-build
    sudo apt install ruby-dev
    ```
- 把刚刚新创建的Repo clone下来
    ```shell
    git clone git@github.com:<USRE_NAME>/<USRE_NAME>.github.io
    ```
- 进入到clone下来的目录, 然后以下命令进行初始构建.
    ```shell
    bundle
    ```
- 构建成功后, 可以使用以下命令初始化一个web server [localhost](http://127.0.0.1:4000/), 可以直接访问观察实时效果, 便于调试.
    ```shell
    bundle exec jekyll s
    ```

>我是用的环境是WSL2下的Ubuntu 22.04.3 LTS, Windows和MacOS环境下可自行探索.

## 项目结构
```shell
$ tree -L 1
.
├── Gemfile
├── Gemfile.lock
├── LICENSE
├── README.md
├── _config.yml
├── _data
├── _plugins
├── _posts
├── _site
├── _tabs
├── assets
└── index.html
```
只谈几个重要的:
- _config.yml 
    - 配置文件, 主页名, github链接, 亮暗主题等都可以在这自行设置.
- _data/ 
    - 一些数据文件.
- posts/ 
    - 发布的markdown格式的文章都在这.
- site/ 
    - 构建出的网页相关源码.
- _tabs/ 
    - 左侧标签.
- index.html
    - 主页的HTML源文件, 没有特殊需求不用动.

## 发布blog
### Option 1
- 在_posts下创建一个markdown格式的文件, 其命名格式为`YYY-MM-DD-NAME.md`
- 文件头部需要加上以下
    ```yaml
    ---
    title: TITLE
    date: YYYY-MM-DD HH:MM:SS +/-TTTT
    categories: [TOP_CATEGORIE, SUB_CATEGORIE]
    tags: [TAG]     # TAG names should always be lowercase
    ---
    ```
- 本地检查格式
- push到github

### Option 2
每次都写日期很麻烦, 因此我们可以引入一个工具[jekyll-compose](https://github.com/jekyll/jekyll-compose).
- 在项目根目录clone该工具
    ```shell
    git clone https://github.com/jekyll/jekyll-compose
    ```
- 在Gemfile中加上一行命令
    ```shell
    gem 'jekyll-compose', group: [:jekyll_plugins]
    ```
- 执行命令重新构建
    ```shell
    bundle
    ```
- 这样创建新的post会方便一些
    ```shell
    bundle exec jekyll page "My New Page"
    ```
- 本地检查格式
- push到github

> 更多用法自行探索.

## 成果展示
![Alt text](/assets/images/image1.png)