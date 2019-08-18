---
layout: '[page]'
title: Hello-World之后
date: 2019-08-09 22:06:44
tags:[blog, GitPage]
---
# 0. 前言

  知道Github能做博客已经有相当长一段时间了，但是，由于能力、精力等多种因素的限制，博客一直处于下图的状态：

![01.jpg](https://i.loli.net/2019/08/09/rQ81lwcifpyDeTs.jpg)

  说来，十分惭愧，这篇blog也已经从最初的8.09写到了08.12。
  作为“Hello， World！”之后的第一篇博客，主要是给自己使用GitPage搭建Blog做个记录，当然，如果能够帮助到后来的小伙伴们，那就更好啦！
  工欲善其事必先利其器，然额，贯于GitPage搭建bolg的步骤，目前网上的各种教程较为分散，主要是以成功的在GitPage上成功实现Fork及访问为主，所以，也给很多小伙伴带来了神奇的困惑，自然而然冒出来的问题便是，然后嘞？然后我再咋搞呢？所以，本着如何较系统地从入门到实践的角度，记录下本次从搭建到第一篇博客发布的过程，也算是从本人的角度对使用Github Page搭建博客过程的一个Trouble Shotting的记录。

 <!--more-->

## 本文主要参考以下文章实现
> 1. [手把手教你使用Hexo + Github Pages搭建个人独立博客](https://div.io/topic/1691)
> 2. [Hexo + yilia 搭建博客可能会遇到的所有疑问](http://www.54tianzhisheng.cn/2017/12/18/hexo-yilia/)
> 3. [Markdown基本语法](https://www.jianshu.com/p/191d1e21f7ed)
> 4. [windows 下 git bash 打开特定的文件目录](https://blog.csdn.net/assassinsshadow/article/details/79820299)
> 5. [安装Node.js](http://www.w3cschool.cc/nodejs/nodejs-install-setup.html)
> 6. [Hexo官网: 快速、简洁且高效的博客框架](https://hexo.io/zh-cn/docs/)
> 7. [用Hexo写出第一篇博客](https://www.jianshu.com/p/56d99a3049a5)

# 1. 步骤
## 1.1 申请Github账号，并创建自己博客的**Repositories**
  想来，这个环节应该是最简单的，网上有无数的教程阔以帮助实现，具体过程不再赘述。
  当然，链接提供是必备的啦，详看参考文章1。
  需要特别指出的是，每个帐号只能有一个仓库来存放个人主页，而且仓库的名字必须是username/username.github.io，对，这个username就是你自己的用户名，这是特殊的命名约定。
  比如我的用户名是yangluom，我的blog仓库就是yangluom/yangluom.github.io这个啦。
  ![02.jpg](https://i.loli.net/2019/08/12/w6Gsdv2VhaPFjMB.jpg)
  比方说你得用户名是abc123，那你就可以创建abc123.github.io这个Repositories（资源仓库）,并通过http://abc123.github.io 来访问你的个人主页。
  这里特别提醒一下，需要注意的个人主页的网站内容是在master分支下的。

## 1.2 在本地下载、安装Hexo
  嗯，这可能是让人小纠结的问题，我既然要在github上搭博客，直接在github上操作不就完了么？其实并不是，这个过程是，你必须先在本地搞定你自己静态网页的内容后，然后部署到github上。
  所以，要先实现本地系统的环境配置。要使用Hexo，需要在你的系统中支持Nodejs以及Git。（本部分主要参考[手把手教你使用Hexo + Github Pages搭建个人独立博客](https://div.io/topic/1691)，如有雷同，纯属必然，并无偶然。。。）

### 1.2.1 安装Node.js
  [下载Node.js](https://nodejs.org/download/)
  由于我使用的操作系统是64位WIN10系统，所以，仅就该系统下如何安装予以展示，其他操作系统的安装，可以参考下文进行：
  参考地址：[安装Node.js](https://www.runoob.com/nodejs/nodejs-install-setup.html)
  这次安装，我采用了Node.js v10.16.3 LTS(长期支持版本)版本，如果目前版本已过时，大家可以根据自己使用的操作系统，去[Node.js的官网](https://nodejs.org/en/download/)下载最新的LTS版本软件：
  ![00.jpg](https://i.loli.net/2019/08/18/hGOUydvKgVPkIF5.jpg)
  
  具体安装如下，其他版本安装应该类似：
  双击已经下载的安装包，将出现如下界面，点击“Next”继续就可以了；
  ![00.jpg](https://i.loli.net/2019/08/18/hGOUydvKgVPkIF5.jpg)
  
   勾选接受协议选项，点击 next（下一步） 按钮 : 
   ![002.jpg](https://i.loli.net/2019/08/18/NKG9zf6y2qTHRcF.jpg)
   
   Node.js默认安装目录为 "C:\Program Files\nodejs\" , 你可以修改目录，并点击 next（下一步）：
   ![003.jpg](https://i.loli.net/2019/08/18/vHh78EGpuztckre.jpg)
   
   点击树形图标来选择你需要的安装模式 （如无特殊需求，选项默认就可以啦）, 然后点击下一步 next（下一步），继续进行安装：
   ![004.jpg](https://i.loli.net/2019/08/18/7iPCVpOgwGy15Nu.jpg)
   
   点击 Install（安装） 开始安装Node.js。你也可以点击 Back（返回）来修改先前的配置。 然后并点击 next（下一步）；然后，点击 Finish（完成）按钮退出安装向导，至此，Node.js就已经安装在我们的电脑上啦 。

   最后，检测一下PATH环境变量是否配置了Node.js：
   点击开始→ 运行→ 输入"cmd" → 输入命令"path"，输出如下结果：
```bat
	C:\Users\luyou>path
PATH=C:\WINDOWS\system32;C:\WINDOWS;C:\WINDOWS\System32\Wbem;C:\WINDOWS\System32\WindowsPowerShell\v1.0\;C:\WINDOWS\System32\OpenSSH\;C:\Program Files\MacType;C:\Program Files\nodejs\;D:\python\pywin\Scripts\;D:\python\pywin\;C:\Users\luyou\AppData\Local\Microsoft\WindowsApps;D:\moe2014\bin;C:\Users\luyou\AppData\Local\GitHubDesktop\bin;C:\Users\luyou\AppData\Roaming\npm
```
   我们可以看到环境变量中已经包含了C:\Program Files\nodejs\


### 1.2.2 安装Git
  下载地址：http://git-scm.com/download/
  > 此处可能有的小坑，即git安装后，可能需要在指定目录打开，此时，可以如下操作：
  
  > 找到gitbash快捷图标，右键，点击属性
  > 将目标： –cd -to-home 删掉
  > 起始位置填写即将打开的路径，如下图。点击【应用】【确定】。
  
![03.jpg](https://i.loli.net/2019/08/13/Y2EMAmZ4jvkxDes.jpg)

### 1.2.3 安装Hexo
```shell
  $ cd g:/hexo
  $ npm install hexo-cli -g
  $ hexo init blog
  $ cd blog
  $ npm install
  $ hexo g # 或者hexo generate
  $ hexo s # 或者hexo server，此时，如果系统没报错的话，即可在http://localhost:4000/ 查看
```
现在我们打开http://localhost:4000/ 已经可以看到一篇内置的blog了。 

目前我安装所用的本地环境如下：(可以通过hexo -v查看)
![04.jpg](https://i.loli.net/2019/08/15/AabERYQyLnqUIto.jpg)

在这里说下Hexo常用的几个命令：
> 1. hexo generate (hexo g) 生成静态文件，会在当前目录下生成一个新的叫做public的文件夹
> 2. hexo server (hexo s) 启动本地web服务，用于博客的预览
> 3. hexo deploy (hexo d) 部署播客到远端（比如github, heroku等平台）
> ```shell
  $ hexo new "postName"			#新建文章
  $ hexo new page "pageName"	#新建页面
>```

常用简写
>```shell
  $ hexo n == hexo new		#新建文章
  $ hexo g == hexo generate	#生成静态文件
  $ hexo s == hexo server		#启动本地web服务
  $ hexo d == hexo deploy		#部署播客到远端
>```


常用组合
> ```shell
  $ hexo d -g #生成部署
  $ hexo s -g #生成预览
> ```


### 1.2.4 Hexo主题设置
这里以主题yilia为例进行说明（也就是本博客的主题啦）。

#### 1.2.4.1 安装主题
> ```shell
  $ hexo clean
  $ git clone https://github.com/litten/hexo-theme-yilia.git themes/yilia
> ```

#### 1.2.4.2 更新主题
> ```shell
  $ cd themes/yilia
  $ git pull
  $ hexo g # 生成
  $ hexo s # 启动本地web服务器
> ```

现在打开http://localhost:4000/ ，会看到我们已经应用了一个新的主题。

## 1.3. 本地Hexo部署到Github
 这一步恐怕是最关键的一步了，让我们把在本地web环境下预览到的博客部署到github上，然后就可以直接通过http://abc123.github.io访问了。不过很多教程文章对这个步骤语焉不详，这里着重说下。

> 首先需要明白所谓部署到github的原理。

> 1. 之前步骤中在Github上创建的那个特别的repo（abc123.github.io）一个最大的特点就是其master中的html静态文件，可以通过链接http://abc123.github.io来直接访问。
> 2. Hexo -g 会生成一个静态网站（第一次会生成一个public目录），这个静态文件可以直接访问。
> 3. 需要将hexo生成的静态网站，提交(git commit)到github上。
> 明白了原理，怎么做自然就清晰了。

### 1.3.1. 使用hexo deploy部署
hexo deploy可以部署到很多平台，具体可以参考[Hexo官网的这个链接](https://hexo.io/docs/deployment.html). 如果部署到github，需要在配置文件_config.xml中作如下修改：
> ```shell
deploy:
  type: git
  repo: git@github.com:abc123/abc123.github.io.git
  branch: master
> ```
然后在命令行中执行
> ```shell
hexo d
> ```
即可完成部署。

注意需要提前安装一个扩展：
> ```shell
$ npm install hexo-deployer-git --save
> ```

在实际操作过程中，我在"hexo d"这一步碰到了神奇的问题，希望能够帮到碰到类似问题的小伙伴，具体如下：
当我输入"hexo d"命令后，系统提示：
> ```shell
ERROR Deployer not found: git
> ```

![05.jpg](https://i.loli.net/2019/08/18/ChR8GM6vJioxg7y.jpg)

于是,根据linghucong 大的教程，进行安装:
> ```shell
> $ npm install hexo-deployer-git --save
> npm WARN babel-eslint@10.0.2 requires a peer of eslint@>= 4.12.1 but none is installed. You must install peer dependencies yourself.
> npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.9 (node_modules\fsevents):
> npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.9: wanted {"os":"darwin","arch":"any"} (current: {"os":"win32","arch":"x64"})
> 
> + hexo-deployer-git@1.0.0
> added 24 packages from 10 contributors and audited 9166 packages in 37.295s
> found 1 low severity vulnerability
> run `npm audit fix` to fix them, or `npm audit` for details
> ```

其实，这里已经明确报过错误信息啦：“npm WARN babel-eslint@10.0.2 requires a peer of eslint@>= 4.12.1 but none is installed. You must install peer dependencies yourself.”
但我当时并木有看懂，就继续根据提示操作了下：
> ```shell
  $ npm audit fix
  npm WARN babel-eslint@10.0.2 requires a peer of eslint@>= 4.12.1 but none is installed. You must install peer dependencies yourself.
  npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.9 (node_modules\fsevents):
  npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.9: wanted {"os":"darwin","arch":"any"} (current: {"os":"win32","arch":"x64"})
> 
> up to date in 5.492s
> fixed 0 of 1 vulnerability in 9166 scanned packages
>    1 vulnerability required manual review and could not be updated
> ```

但，并木有解决问题，于是又转回了报错的提示：“npm WARN babel-eslint@10.0.2 requires a peer of eslint@>= 4.12.1 but none is installed. You must install peer dependencies yourself.”，google后的解决方案是：
> ```shell
> $ npm install eslint@4.x babel-eslint@8 --save-dev
> npm WARN deprecated circular-json@0.3.3: CircularJSON is in maintenance only, flatted is its successor.
> npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.9 (node_modules\fsevents):
> npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.9: wanted {"os":"darwin","arch":"any"} (current: {"os":"win32","arch":"x64"})
> 
> + babel-eslint@8.2.6
> + eslint@4.19.1
> added 108 packages from 125 contributors, updated 12 packages and audited 9456 packages in 63.142s
> found 1 low severity vulnerability
>   run `npm audit fix` to fix them, or `npm audit` for details
> ```

继续跟着提示操作：
> ```shell
> $ npm audit fix
> npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.9 (node_modules\fsevents):
> npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.9: wanted {"os":"darwin","arch":"any"} (current: {"os":"win32","arch":"x64"})
> 
> up to date in 7.582s
> fixed 0 of 1 vulnerability in 9456 scanned packages
>   1 vulnerability required manual review and could not be updated
> ```

于是，这下就可以成功使用“$ npm install hexo-deployer-git --save”命令，安装扩展了：

> ```shell
> $ npm install hexo-deployer-git --save
> npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.9 (node_modules\fsevents):
> npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.9: wanted {"os":"darwin","arch":"any"} (current: {"os":"win32","arch":"x64"})
> 
> + hexo-deployer-git@1.0.0
> updated 1 package and audited 9456 packages in 23.449s
> found 1 low severity vulnerability
>   run `npm audit fix` to fix them, or `npm audit` for details
> ```

安装完“hexo-deployer-git”扩展后，本以为就阔以使用“$ hexo d”命令实现部署了，然而：

> ```shell
> $ hexo d
> INFO  Deploying: git
> INFO  Setting up Git deployment...
> Initialized empty Git repository in H:/blog/hexo/blog/.deploy_git/.git/
> [master (root-commit) 5cd33de] First commit
>  1 file changed, 0 insertions(+), 0 deletions(-)
>  create mode 100644 placeholder
> INFO  Clearing .deploy_git folder...
> INFO  Copying files from public folder...
> INFO  Copying files from extend dirs...
> [master 06d32bd] Site updated: 2019-08-07 00:10:46
>  19 files changed, 2616 insertions(+)
>  create mode 100644 2019/07/25/hello-world/index.html
>  create mode 100644 archives/2019/07/index.html
>  create mode 100644 archives/2019/index.html
>  create mode 100644 archives/index.html
>  create mode 100644 fonts/default-skin.b257fa.svg
>  create mode 100644 fonts/iconfont.16acc2.ttf
>  create mode 100644 fonts/iconfont.45d7ee.svg
>  create mode 100644 fonts/iconfont.8c627f.woff
>  create mode 100644 fonts/iconfont.b322fa.eot
>  create mode 100644 fonts/tooltip.4004ff.svg
>  create mode 100644 img/default-skin.png
>  create mode 100644 img/preloader.gif
>  create mode 100644 img/scrollbar_arrow.png
>  create mode 100644 index.html
>  create mode 100644 main.0cf68a.css
>  create mode 100644 main.0cf68a.js
>  create mode 100644 mobile.992cbe.js
>  delete mode 100644 placeholder
>  create mode 100644 slider.e37972.js
> Permission denied (publickey).
> fatal: Could not read from remote repository.
> 
> Please make sure you have the correct access rights
> and the repository exists.
> FATAL Something's wrong. Maybe you can find the solution here: https://hexo.io/docs/troubleshooting.html
> Error: Spawn failed
>     at ChildProcess.<anonymous> (H:\blog\hexo\blog\node_modules\hexo-util\lib\spawn.js:52:19)
>     at ChildProcess.emit (events.js:198:13)
>     at ChildProcess.cp.emit (H:\blog\hexo\blog\node_modules\cross-spawn\lib\enoent.js:40:29)
>     at Process.ChildProcess._handle.onexit (internal/child_process.js:248:12)
> ```

Permission denied，是的“Permission denied (publickey). fatal: Could not read from remote repository.”。这就是这步的报错信息啦，嗯，这表明，并木有成功配置GitHub 的ssh链接密钥，或者并没有生成ssh key，如不确定，可以在ternimal下执行：

> ```shell
　　cd ~/.ssh ls
> ```

来查看是否有文件id_rsa以及文件id_rsa.pub

如果你没有ssh key的话，在ternimal下输入命令：

> ```shell
ssh-keygen -t rsa -C "youremail@example.com"，
> ```

 youremail@example.com 改为自己的邮箱即可，途中会让你输入密码啥的，不需要管，一路回车即可，会生成你的ssh key。（如果重新生成的话会覆盖之前的ssh key。）
 
>Your identification has been saved in /home/tekkub/.ssh/id_rsa.
>Your public key has been saved in /home/tekkub/.ssh/id_rsa.pub.
>The key fingerprint is:
>SHA256:(大概43位的字母、数字或符号的排布) youremail@example.com

进入github账户中

点击右上角图像，打开设置，里面有添加ssh密钥，将拷贝的公钥内容粘贴到里面，标签随便写，最好是让自己知道是哪一台主机的公钥。然后点击添加，这个时候就在github账户中添加好了ssh公钥

![06.jpg](https://i.loli.net/2019/08/19/zt6YEIdVHbfnqPj.jpg)

这时候，就可以使用“$ hexo d”命令实现部署了：
> ```shell
> $ hexo d
> INFO  Deploying: git
> INFO  Clearing .deploy_git folder...
> INFO  Copying files from public folder...
> INFO  Copying files from extend dirs...
> On branch master
> nothing to commit, working tree clean
> Counting objects: 32, done.
> Delta compression using up to 8 threads.
> Compressing objects: 100% (25/25), done.
> Writing objects: 100% (32/32), 150.47 KiB | 1.95 MiB/s, done.
> Total 32 (delta 5), reused 0 (delta 0)
> remote: Resolving deltas: 100% (5/5), done.
> To github.com:abc123/abc123.github.io.git
>  * [new branch]      HEAD -> master
> Branch master set up to track remote branch master from git@github.com:abc123/abc123.github.io.git.
> INFO  Deploy done: git
> ```

部署结束后，可以运行
> ```shell
git clone https://github.com/abc123/abc123.github.io.git .deploy/abc123.github.io
> ```

命令，将部署的文件同步回本地以归档，需要特别注意的是在上传代码到github之前，一定要记得先把你以前所有代码下载下来（虽然github有版本管理，但备份一下总是好的），因为从hexo提交代码时会把你以前的所有代码都删掉。

> ```shell
> $ git clone https://github.com/abc123/abc123.github.io.git .deploy/abc123.github.io
> Cloning into '.deploy/yangluom.github.io'...
> remote: Enumerating objects: 32, done.
> remote: Total 32 (delta 0), reused 0 (delta 0), pack-reused 32
> Unpacking objects: 100% (32/32), done.
> ```

## 1.4. 开始“Hello， World”之后的第一篇博客
### 1.4.1 配置文件命名规则和路由地址
https://www.jianshu.com/p/56d99a3049a5
### 1.4.2 创建博客
https://www.cnblogs.com/liuxianan/p/build-blog-website-by-hexo-github.html#%E5%86%99%E5%8D%9A%E5%AE%A2

https://www.jianshu.com/p/56d99a3049a5

定位到我们的hexo根目录，执行命令：
> ```shell
hexo new 'my-first-blog'
> ```

hexo会帮我们在./source/_posts下生成相关md文件：

```shell
$ ll ./source/_posts/
total 24
-rw-r--r-- 1 luyou 197609 18149 8月  19 01:12 2019-08-09-Hello-World之后.md
-rw-r--r-- 1 luyou 197609   826 7月  25 21:09 hello-world.md
```


### 1.4.3 写作
我们只需要打开这个文件就可以开始写博客了，默认生成如下内容：

### 1.4.4 发布
部署修改
通过 
```shell
hexo d -g 
```
部署本地的博客文件到github

# 2. 其他进阶设置


# 3. 总结