---
title: 使用hexo + gitpages + cloudStudio搭建博客系统
date: 2019-04-09 14:43:52
categories: 
- hexo
- 随记
tags: 
- 博客
---
>之前都是在CSDN撰写博客，近段时间看见一篇博客讲述说hexo + gitpages 可以免费搭建一个属于个人的博客，琢磨琢磨就开始搭建了，下面就记录下搭建过程。
<!-- more -->

## 环境介绍
### hexo
[Hexo](https://hexo.io/zh-cn/docs/) 是一个快速、简洁且高效的博客框架。Hexo 使用 Markdown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。  
  

### gitpages
对于它相信大家一定不陌生，不过还是在这介绍一下吧。GitHub Pages 本用于介绍托管在 GitHub 的项目， 不过，由于他的空间免费稳定，用来做搭建一个博客再好不过了。总之，github Pages可以被认为是用户编写的、托管在github上的静态网页。  
  
    

### Clound Studio
[CloudStudio](https://dev.tencent.com/help/doc/cloud-studio) 是基于浏览器的集成式开发环境（IDE），为开发者提供了一个永不间断的云端工作站。Cloud Studio 还具有一些特色功能，如一键环境切换、多人协同编辑、在线预览等等，可以帮助开发者完成各种应用的开发、编译与部署工作。   
说人话就是一个云端的可供多人在线协作开发的一个IDE工具，用起来非常方便。  

## 搭建流程
### Cloud Studio
#### 创建运行空间
注册coding账号绑定腾讯云账号后进入Cloud Studio新建工作空间
{% asset_img hexo-cloudstudio-1.png %}  

+ 选好来源及运行环境 
+ 绑定SSH key至git仓库  

{% asset_img hexo-cloudstudio-2.png 绑定SSH Key%}
搞定之后创建就ok
### hexo
#### 初始化环境
进入空间首先就是敲命令了
```
hexo init <folder>
```
其中`<folder>`就是你想要创建的文件夹。  
ps:`<folder>`为空的话取当前的文件夹,前提是当前文件夹为空，否则会报错。
![](https://dn-coding-net-production-pp.codehub.cn/eeff1c31-1770-4045-9f3e-7924d361dade.jpg ) 
执行完成后接着敲
```
cd <folder>
npm install
```
这两执行完后，基本的包结构也就创建好了
#### 配置hexo 
在hexo根目录找到_config.yml文件,找到deploy项,修改如下（使用gitPage发布）：
```
deploy:
  type: git
  repo: <repository url> #https://bitbucket.org/JohnSmith/johnsmith.bitbucket.io
  branch: [branch] #published
  message: [message]
```
详细查看[Hexo官方文档](https://hexo.io/zh-cn/docs/deployment)
  

## 写作  

### hexo
#### 写文章
你可以执行下列命令来创建一篇新文章。
```
$ hexo new [layout] <title>
```
您可以在命令中指定文章的布局（layout），默认为 post，可以通过修改 _config.yml 中的 default_layout 参数来指定默认布局。  
详细查看[Hexo官方文档](https://hexo.io/zh-cn/docs/writing)
  
#### 生成博客
写完 md 源文件后，我们需要 Hexo 帮忙生成静态文件，以便能在浏览器中看到渲染后最终的效果。
执行生成文件命令：
```
hexo generate
```
或者其简写形式：
```
hexo g
```
终端执行命令后效果如下。目录中会多出一个 public 文件夹，刚才生成的文件都放在其中。  

#### 部署博客
Hexo 提供了快速方便的一键部署功能，让您只需一条命令就能将网站部署到服务器上。
```
hexo deploy
```
或者其简写形式：
```
hexo d
```
生成+部署：
```
hexo d -g
```

## 访问
### gitpages  

#### 对部署的仓库设置pages
进入git仓库页面中的Settings选项进行配置,配置如下：
{% asset_img hexo-cloudstudio-3.png %}
#### 域名解析CNAME
yourname.github.io配置到域名解析中
{% asset_img hexo-cloudstudio-4.png %}
上图是使用coding+gitpages来区分国内国外两种环境所做的双托管配置,  
正常来说只用配置一项然后解析线路类型选择默认就ok。
#### 访问
如果访问配置域名跳转到该页面的话,就代表博客已经大功告成了。。。
![](https://dn-coding-net-production-pp.codehub.cn/cc04c804-9fec-44f8-89fe-c64604eb1351.jpg)


  

## 参考资料
[hexo官方文档](https://hexo.io/zh-cn/)  
[最快的 Hexo 博客搭建方法](https://blog.coding.net/blog/CS-Hexo)  
[把搭建的Hexo关联Git](https://www.jianshu.com/p/330e0ae1ebd7)  
[Hexo博客双线部署](https://www.jianshu.com/p/f4fa869a6cc7)

