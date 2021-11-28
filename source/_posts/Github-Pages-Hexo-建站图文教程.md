---
title: Github Pages + Hexo 建站图文教程
date: 2021-11-28 23:47:28
tags:
---
## <font face="华文细黑" color="#CC3352">1. 前言</font>
安装 NodeJs、Git 工具。
无需安装 hexo, 使用 npx 命令即可。

npx 是 npm(Node Package Manager) 引入的一个工具。优点免去了全局安装。
- 临时安装可执行依赖包，不用全局安装，不用担心长期的污染。
- 可以执行依赖包中的命令，安装完成自动运行。
- 自动加载node_modules中依赖包，不用指定$PATH。
- 可以指定node版本、命令的版本，解决了不同项目使用不同版本的命令的问题。

npx 免全局安装 hexo, npm 从 5.2 版本增加了 npx 命令。

示例：
查看 hexo 版本
```xml
npx hexo -v
```
## <font face="华文细黑" color="#CC3352">2. 环境准备</font>
### <font face="华文细黑" color="#CC3352">2-1. 免安装 Hexo</font>
hexo 官方文档: <a href="hexo.io/zh-cn/docs/">hexo.io/zh-cn/docs</a>

`重要：注意版本兼容，不兼容会导致命令执行报错`
|Hexo版本|最低兼容 Node.js 版本|
|-|-|
|5.0+|10.13.0|
|4.1 - 4.2|	8.10|
|4.0|	8.6|
|3.3 - 3.9|	6.9|
|3.2 - 3.3|	0.12|
|3.0 - 3.1|	0.10 or iojs|
|0.0.1 - 2.8|	0.10|

免安装 Hexo，查看版本信息
```xml
 npx hexo -v
INFO  Validating config
hexo: 5.4.0
hexo-cli: 4.3.0
os: win32 10.0.17134
node: 12.0.0
v8: 7.4.288.21-node.16
uv: 1.28.0
zlib: 1.2.11
brotli: 1.0.7
ares: 1.15.0
modules: 72
nghttp2: 1.38.0
napi: 4
llhttp: 1.1.1
http_parser: 2.8.0
openssl: 1.1.1b
cldr: 34.0
icu: 63.1
tz: 2018e
unicode: 11.0
```
### <font face="华文细黑" color="#CC3352">2-2. 安装 Git、NodeJs</font>

安装 Git (无版本要求)
```xml
$ git --version
git version 2.18.0.windows.1
```

安装 Node.js 12.0.0 (考虑与 hexo 的版本兼容问题)<br>
历史版本下载地址: <a href="nodejs.org/dist/">nodejs.org/dist/</a>
```xml
$ node -v
v12.0.0
```
### <font face="华文细黑" color="#CC3352">2-3. Git 配置</font>
>下面的 Hexo 初始化命令 hexo init folder 会拉取 https://github.com/hexojs/hexo-starter.git 源文件。需要配置 Git 并连接到远程仓库。
>若已安装 Git 并连接到远程仓库，跳过该步骤即可。

安装 Git，生成并配置私钥 id_rsa 连接上 ssh 。一般的，打开 Git Bash 能够成功连接代码托管平台即可，此处以 Github 为例，能够正常 clone 仓库，拉取推送提交代码即可。
另外，通过`ssh -T `命令可在 Git Bash 测试是否连接成功
```xml
Administrator@DESKTOP-OB9FR3E MINGW64 ~/.ssh/github
$ eval $(ssh-agent)
Agent pid 1107

Administrator@DESKTOP-OB9FR3E MINGW64 ~/.ssh/github
$ eval 'ssh-agent'
SSH_AUTH_SOCK=/tmp/ssh-lTvsTJJ3ANQQ/agent.1111; export SSH_AUTH_SOCK;
SSH_AGENT_PID=1112; export SSH_AGENT_PID;
echo Agent pid 1112;

Administrator@DESKTOP-OB9FR3E MINGW64 ~/.ssh/github
$ ssh-add id_rsa
Identity added: id_rsa (2469031115@qq.com)

Administrator@DESKTOP-OB9FR3E MINGW64 ~/.ssh/github
$ ssh -T git@github.com
Hi niaonao! You've successfully authenticated, but GitHub does not provide shell access.
```

Git 连接 ssh 可参考：<a href="developers.blog.csdn.net/article/details/103004901">Git 配置 SSH-Key 从远程存储库 clone 项目</a>
## <font face="华文细黑" color="#CC3352">3. Hexo 建站初始化</font>
WIN + R 进入命令行窗口，在路径 D:\workspace\customWeb 下执行下列命令，Hexo 将会在指定文件夹中新建所需要的文件。
```xml
$ npx hexo init web
$ cd web
$ npm install
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/3d5c525639d14834aed16ebd5d6e7bea.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAbmlhb25hbw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)

文件说明
- _config.yml
网站的 配置 信息，您可以在此配置大部分的参数。
- package.json
应用程序的信息
- scaffolds
模板文件夹，新建文章时，Hexo 会根据 scaffold 来建立文件。
- source
资源文件夹
- themes
主题文件夹，hexo 会根据主题来生成页面。

更多配置: <a href="hexo.io/zh-cn/docs/configuration">hexo.io/zh-cn/docs/configuration</a>

静态文件生成后启动服务器
```xml
# 清除上次生成的文件
$ npx hexo clean
# 生成文件
$ npx hexo generate
# 运行服务
$ npx hexo server
```

```xml
$ npx hexo server
INFO  Validating config
INFO  Start processing
INFO  Hexo is running at http://localhost:4000 . Press Ctrl+C to stop.
INFO  See you again
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/0667b72a06d94f4b866eb24a3108f234.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAbmlhb25hbw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)

## <font face="华文细黑" color="#CC3352">4. Github Page 服务</font>
Github Pages 是一个免费的静态网页托管服务，您可以使用 Github Pages 托管博客、项目官网等静态网页。
登录 Github 并创建新仓库，名称格式为 `xxx.github.io`，xxx 为你的账户名，这个仓库会被识别为 Git Page 服务。我这里创建 niaonao.github.io 仓库。
>accountName.github.io 仓库名称命名格式为 `你的 Github 账户名+.github.io`, Github 会自动识别 github.io 为 Github Page 服务。
>Gitee 也支持 Gitee Pages 服务。目前 Gitee Pages 支持 Jekyll、Hugo、Hexo 编译静态资源。

## <font face="华文细黑" color="#CC3352">5. Hexo Deploy 部署</font>
### <font face="华文细黑" color="#CC3352">5-1. 部署配置</font>
安装部署工具
```xml
$ npm install hexo-deployer-git --save
```

修改部署配置 _config.yml

deploy.repo 配置托管仓库地址
```xml
deploy:
  type: git
  repo: git@github.com:niaonao/niaonao.github.io.git
  branch: master
```
### <font face="华文细黑" color="#CC3352">5-1. 生成文件并部署</font>
然后重新生成文件并部署
```xml
$ npx hexo clean
$ npx hexo genarate
$ npx hexo deploy
```
执行日志
```xml
$ npx hexo clean
INFO  Validating config
INFO  Deleted database.
INFO  Deleted public folder.

$ npx hexo g
INFO  Validating config
INFO  Start processing
INFO  Files loaded in 313 ms
INFO  Generated: archives/index.html
INFO  Generated: archives/2021/index.html
INFO  Generated: archives/2021/11/index.html
INFO  Generated: fancybox/blank.gif
INFO  Generated: fancybox/helpers/fancybox_buttons.png
INFO  Generated: index.html
INFO  Generated: fancybox/fancybox_loading.gif
INFO  Generated: fancybox/fancybox_sprite.png
INFO  Generated: fancybox/fancybox_sprite@2x.png
INFO  Generated: fancybox/fancybox_overlay.png
INFO  Generated: fancybox/fancybox_loading@2x.gif
INFO  Generated: js/script.js
INFO  Generated: fancybox/jquery.fancybox.css
INFO  Generated: fancybox/helpers/jquery.fancybox-media.js
INFO  Generated: fancybox/helpers/jquery.fancybox-thumbs.css
INFO  Generated: fancybox/helpers/jquery.fancybox-thumbs.js
INFO  Generated: fancybox/helpers/jquery.fancybox-buttons.js
INFO  Generated: fancybox/helpers/jquery.fancybox-buttons.css
INFO  Generated: css/fonts/fontawesome-webfont.eot
INFO  Generated: css/style.css
INFO  Generated: css/fonts/fontawesome-webfont.ttf
INFO  Generated: css/fonts/fontawesome-webfont.woff
INFO  Generated: fancybox/jquery.fancybox.pack.js
INFO  Generated: css/fonts/FontAwesome.otf
INFO  Generated: 2021/11/26/hello-world/index.html
INFO  Generated: fancybox/jquery.fancybox.js
INFO  Generated: css/fonts/fontawesome-webfont.svg
INFO  Generated: css/images/banner.jpg
INFO  28 files generated in 1.31 s

$ npx hexo d
INFO  Validating config
INFO  Deploying: git
INFO  Clearing .deploy_git folder...
INFO  Copying files from public folder...
INFO  Copying files from extend dirs...
warning: LF will be replaced by CRLF in 2021/11/26/hello-world/index.html.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in archives/2021/11/index.html.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in archives/2021/index.html.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in archives/index.html.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in css/fonts/fontawesome-webfont.svg.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in css/style.css.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in fancybox/helpers/jquery.fancybox-buttons.css.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in fancybox/helpers/jquery.fancybox-buttons.js.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in fancybox/helpers/jquery.fancybox-media.js.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in fancybox/helpers/jquery.fancybox-thumbs.css.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in fancybox/helpers/jquery.fancybox-thumbs.js.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in fancybox/jquery.fancybox.css.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in fancybox/jquery.fancybox.js.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in fancybox/jquery.fancybox.pack.js.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in index.html.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in js/script.js.
The file will have its original line endings in your working directory.
[master 2f76ec6] Site updated: 2021-11-26 17:42:13
 2 files changed, 2 insertions(+), 2 deletions(-)
Enumerating objects: 70, done.
Counting objects: 100% (70/70), done.
Delta compression using up to 4 threads.
Compressing objects: 100% (48/48), done.
Writing objects: 100% (70/70), 509.67 KiB | 1.30 MiB/s, done.
Total 70 (delta 9), reused 0 (delta 0)
remote: Resolving deltas: 100% (9/9), done.
To github.com:niaonao/niaonao.github.io.git
 + d6f6e29...2f76ec6 HEAD -> master (forced update)
Branch 'master' set up to track remote branch 'master' from 'git@github.com:niaonao/niaonao.github.io.git'.
INFO  Deploy done: git
```
### <font face="华文细黑" color="#CC3352">5-3. 访问服务</font>
发布完成，访问 <a href="niaonao.github.io">niaonao.github.io</a> 可看到模板文件已更新到 github 托管仓库。

![在这里插入图片描述](https://img-blog.csdnimg.cn/ad2681608b5f47f8831e2a081ed25050.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAbmlhb25hbw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)

此时已经通过 Git 部署到代码仓库 git@github.com:niaonao/niaonao.github.io.git

![在这里插入图片描述](https://img-blog.csdnimg.cn/a2d14dcb778f40ddb84854af1f765e52.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAbmlhb25hbw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)

## <font face="华文细黑" color="#CC3352">6. 博客个性化</font>
### <font face="华文细黑" color="#CC3352">6-1. 博文新建删除</font>
```xml
$ npx hexo new '第一篇博客'
INFO  Validating config
INFO  Created: 
```
会在相对路径 `\\source\\_posts` 下生成对应的 `\<title\>.md` 文件

![在这里插入图片描述](https://img-blog.csdnimg.cn/ccd71f75df45457986b956d34f56ec7c.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAbmlhb25hbw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)

通过 npx hexo new \<title\> 新建一篇博客，从 \\source 下移除该文件重新部署发布即相对的删除了该篇博客。
### <font face="华文细黑" color="#CC3352">6-2. 个性化主题</font>
主题：<a href="hexo.io/themes">hexo.io/themes</a>
选择一款主题，点击跳转到资源托管平台，下载压缩文件解压缩到 \\\themes 文件夹下，与默认主题 landscape 同级目录。

![在这里插入图片描述](https://img-blog.csdnimg.cn/f0e85db484474cde84fa9f3aff5ea25a.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAbmlhb25hbw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)

在 _config.yml 修改配置即可
```xml
theme: landscape
```
本地访问
```xml
$ npx hexo clean | npx hexo generate | npx hexo server
INFO  Validating config
INFO  Start processing
INFO  Hexo is running at http://localhost:4000 . Press Ctrl+C to stop.
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/a9b31e67aa974ecb8a8638f87e543cc1.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAbmlhb25hbw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)

部署发布
在建站路径下右键打开 Git Bash，执行以下命令部署
注意部署失败，请检查 Git 配置及分支是否正确，默认分支为 mster，注意更新 _config.yml 配置保持分支一致。
```xml
$ npx hexo clean | npx hexo generate | npx hexo deploy
```
发布完成

![在这里插入图片描述](https://img-blog.csdnimg.cn/c8651844ebe447ef81446d9e90a55536.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAbmlhb25hbw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)

效果演示：<a href="niaonao.github.io">niaonao.github.io</a>

## <font face="华文细黑" color="#CC3352">7. line.mathAll is not function 报错</font>
报错出现原因是 NodeJs 版本过低，建议使用 NodeJs 12.0.0 及以上版本。

>参考文章：<a herf="blog.csdn.net/sinat_37781304/article/details/82729029">hexo史上最全搭建教程</a>
>Hexo 常见问题解答：<a href="hexo.io/zh-cn/docs/troubleshooting">hexo.io/zh-cn/docs/troubleshooting</a>
><font size="4" color="#CC3352">Powered By niaonao</font>