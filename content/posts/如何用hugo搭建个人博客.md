---
title: "如何用hugo搭建个人博客"
date: 2020-02-28T15:57:37+08:00
draft: true
---

## 前言
Hugo是目前比较流行的个人博客快速生成器，相比Hexo来说操作更为简单。

很多小白在第一次使用Hugo的时候会遇到一些问题，那今天来给大家介绍一下怎样搭建自己的第一个博客~

## 1.  安装Hugo
这里MAC用户和Windows用户的操作是不同的。

- MAC用户
  
  在控制台依次输入`brew install hugo`、`hugo version`就可以下载下来了

- Windows用户
  
  1. 去[Hugo releases 页面](https://github.com/gohugoio/hugo/releases)下载hugo_xxx_Windows-64bit.zip文件
  2. 解压后只需要把文件夹中hugo.exe文件单独拿出来，放到你预先建立的文件夹里，如你在D盘的software文件夹中建了一个名为hugo的文件夹，则你最后得到的地址为D:\Software\hugo\hugo.exe
  3. 把D:\Software\hugo\加到环境变量的PATH中，**这一步很关键**
  4. 重启终端，运行hugo version查看版本，效果代码如下
    ```Bash
    Paula Hu@DESKTOP-0HMOCK9 ~/code_control/paulahu.github.io (master)
    λ hugo version
    Hugo Static Site Generator v0.65.3-211BA42A windows/amd64 BuildDate: 2020-02-23T09:58:40Z
    ```
## 2.  搭建博客
- 可以参考[Hugo官网](https://gohugo.io/),点击Quick Start快速开始，因为第一步我们已经完成了，所以从第二步开始，到第七步结束
- 下面我给大家演示一下
  
  1. 新建新的hugo页面,这里的quickstart可以改为你自己设的名称
   ```Bash
   hugo new site quickstart
   ```
    2. 添加主题，可以是默认的，也可以是别的主题，这里演示默认的主题，输入下面两行代码
   ```Bash
   git init
   git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke
   ```
   3. 把默认主题添加到配置中，打开config.toml文件，输入命令
   ```Bash
   echo 'theme = "ananke"' >> config.toml
   ```
   到这里页面配置好了，下面可以试写你的第一个博客

   4. 输入如下命令,`my-first-post`是可以修改的，表示你的文章标题
   ```Bash
   hugo new posts/c.md
   ```
    5. 这个时候默认在posts文件夹下生成了你的第一个博客，现在修改标题，`draft`改为true，内容可以随意编辑，比如
   ```Markdown
    ---
    title: "开博大吉"
    date: 2020-02-28T11:47:15+08:00
    draft: true
    ---
    ## 大家好
    
    这是我的博客，希望能写一些好的文章分享给大家~~~
    ```
    6. 接着输入如下代码，可以预览你的博客
   ```Bash
   hugo server -D
   ```
   运行后会出现如下代码，注意不要按Ctrl+C，直接点击里面的链接就可以预览
   ![](/images/hugo1.png)

   7. 建立静态页面，这里会生成一个public目录，这个目录实际上就是一个网站，我们只需输入如下代码
   ```Bash
   hugo -D
   ```

## 3.  使用GitHub Pages预览HTML
现在网站搭建好了，怎样能让别人看到呢，我们可以在GitHub上新建一个仓库，将本地的public目录上传就可以预览了，具体操作如下。

1. 因为我们只需上传/public/目录就可以了，所以我们新建一个.gitignore文件，在里面写上/public/
2. 新建一个GitHub仓库，并与本地关联
3. 把本地public目录下的所有文件上传到GitHub
4. 打开新建的仓库，在settings里找到GitHub Pages选项，Source选择master分支，不勾选Enforce HTTPS选项
5. 点击上面出现的链接就可以预览了

## 4.  如何再次新建博客
重复以下步骤即可

1. 新建一个markdown文件，完成博客内容
2. 预览效果
3. 将更新内容部署到public目录
4. 进入到public目录
5. 把最新的public目录上传到GitHub

相关代码如下：
```Markdown
hugo new posts/博客名.md
hugo server -D
hugo -D
cd public
```
注意，第三步是在public目录外操作，第四步是在public目录下操作

## 小结
完成上述工作一个个人博客就算搭建成功了。当然，我们也可以申请自己的域名，将博客部署到网站上，相关的内容我后续会介绍，请关注我的博客哦~~~



   
   
