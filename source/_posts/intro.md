---
title: First blog with Hexo Framework
tags:
 - hexo
 - blog
 - framework
categories:
 - blog
teaser: Install, configure hexo. Create my first blogpost in markdown form and host it to github
---

 In diesem Blogartikel wollte ich erzählen (oder notieren), wie ich meinen ersten Blog mit [Hexo](https://hexo.io) erstellt habe.
Anschließend erfasse ich auch, wie ein Blogartikel auf [GitHub](https://github.com) gehostet wird.

## Create my first blog article

### GitHub Account

### Install Hexo

**Requirements**:
&nbsp;&nbsp; [Node.js](https://nodejs.org/en/) muss installiert werden (aktuelle Version).
&nbsp;&nbsp; [git](https://git-scm.com/book/de/v1/Los-geht%E2%80%99s-Git-installieren) muss installiert werden (aktuelle Version).

Die Installation des Hexo-Frameworks ist relative einfach. Dafür muss das Paket hexo-cli via npm installiert werden.

``` bash
# install hexo-cli global
$ npm install -g hexo-cli
```

### Add blog folder

#### <i class="fa fa-gear fa-spin fa-2x" style="color: firebrick"></i> Configuration

``` bash
# i want to save my blog folder in `workspace/Code/node-projects`
$ cd workspace/Code/node-projects
# install blog folder `rock-on-blogs`
$ hexo init rock-on-blogs
```

### Create a new post

``` bash
$ hexo new "My New Post"
```

More info: [Writing](https://hexo.io/docs/writing.html)

### Run server

``` bash
$ hexo server
```

More info: [Server](https://hexo.io/docs/server.html)

### Generate static files

``` bash
$ hexo generate
```

More info: [Generating](https://hexo.io/docs/generating.html)

### Deploy to remote sites

``` bash
$ hexo deploy
```

More info: [Deployment](https://hexo.io/docs/deployment.html)
