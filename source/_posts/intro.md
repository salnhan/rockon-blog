---
title: Experiences with Hexo Framework
categories: hexo framework blog
teaser: Create and host your blog with Hexo, which is a blogging framework
---

 In diesem Blogartikel wollte ich erzählen (oder notieren), wie ich meinen ersten Blog mit [Hexo](https://hexo.io) erstellt habe.
Anschließend erfasse ich auch, wie ein Blogartikel auf [GitHub](https://github.com) gehostet wird.

## Blogartikel anlegen 

### GitHub Account anlegen (falls nicht vorhanden)

### Installation Hexo

**Requirements**:
&nbsp;&nbsp; [Node.js](https://nodejs.org/en/) muss installiert werden (aktuelle Version).
&nbsp;&nbsp; [git](https://git-scm.com/book/de/v1/Los-geht%E2%80%99s-Git-installieren) muss installiert werden (aktuelle Version).

Die Installation des Hexo-Frameworks ist relative einfach. Dafür muss das Paket hexo-cli via npm installiert werden.

``` bash
# install hexo-cli global
$ npm install -g hexo-cli
```

### Blog-Ordner anlegen

#### <i class="fa fa-gear fa-spin fa-2x" style="color: firebrick"></i> Configuration

Anmerkung: Speicherort des Blog-Ordners beachten

``` bash
# i want to save my blog folder in `workspace/Code/node-projects`
$ cd workspace/Code/node-projects
# install blog folder `rock-on-blogs`
$ hexo init rock-on-blogs
```


Ein Ordner muss angelegt, um die Blogposts zu verwalten

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
