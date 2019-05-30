---
title: Writing blog post by using hexo framework 
tags:
 - hexo
 - blog
 - github's page
categories:
 - blog
 - hexo
teaser:  Install and configure hexo. Create blog post in markdown form and Host it to github
---
In this blog

* A short introduction to [Hexo Framework](https://hexo.io): installation and setup
* Creating a blog post in markdown form
* Hosting blogs to [GitHub](https://github.com)

#### Hexo - short introduction

[Hexo Framework](https://hexo.io) is a fast, simple & powerful blog framework based on nodejs.

{% img logo-icon https://hexo.io/icon/favicon-196x196.png 70 70 hexo logo %}

You can write posts in [Markdown](https://daringfireball.net/projects/markdown/) or other languages and **hexo** generates statics files with a beautiful theme in seconds

In addition offers **Hexo** alot of [plugins](https://hexo.io/plugins/), which make it easy to extend functions without modifying the source code of the core module

#### <i class="far fa-save"></i>  Install Hexo

Before installing **hexo** you do need to have a couple of other thing installed first:

* [Node.js](https://nodejs.org/en/)
* [git](https://git-scm.com/book/de/v1/Los-geht%E2%80%99s-Git-installieren)

**Hexo** can be installed with npm

``` bash
# install hexo-cli global
$ npm install hexo-cli -g
```

#### <i class="fas fa-wrench"></i>  Setup

Now is **Hexo** ready to use. You should do some setup for your project

##### Initialize

{% codeblock Initalise project folder lang:bash %}
# i want to save my blog folder in `workspace/Code/node-projects`
$ cd workspace/Code/node-projects
# install blog folder `rock-on-blogs`
$ hexo init rock-on-blogs
# cd rock-on-blogs
$ npm install
{% endcodeblock %}

Once initialised, the structure of your project look like this:

<pre>
	.
	├── _config.yml
	├── package.json
	├── scaffolds
	├── source
	|	├── _drafts
	|	└── _posts
	└── themes
</pre>


You will see installed dependencies in **package.json**

```json
{
  "name": "hexo-site",
  "version": "0.0.0",
  "private": true,
  "hexo": {
    "version": "3.8.0"
  },
  "dependencies": {
    "hexo": "^3.8.0",
    "hexo-deployer-git": "^1.0.0",
    "hexo-generator-archive": "^0.1.4",
    "hexo-generator-category": "^0.1.3",
    "hexo-generator-feed": "^1.2.2",
    "hexo-generator-index": "^0.2.0",
    "hexo-generator-tag": "^0.2.0",
    "hexo-renderer-ejs": "^0.3.0",
    "hexo-renderer-marked": "^1.0.1",
    "hexo-renderer-stylus": "^0.3.1",
    "hexo-server": "^0.2.0"
  },
  "devDependencies": {
    "gulp": "^4.0.2"
  }
}
```
More info about [config files](https://hexo.io/docs/setup)

##### Starting a local server

``` bash
$ hexo server
```

Your website will run at http://localhost:4000 by default. When the server is running, Hexo will watch for file changes and update automatically so it’s not necessary to manually restart the server. You need to refresh your browser if any changes in your blog file.

If you want to use another port

``` bash
$ hexo server -p 5000
```

More info: [Server](https://hexo.io/docs/server.html)

#### Creating and writing a new post

``` bash
$ hexo new "My New Post"
```
In `source/_post`

More info: [Writing](https://hexo.io/docs/writing.html)

#### Deploy to remote sites (github)

Commit your changes first, then execute

``` bash
$ hexo deploy
```

More info: [Deployment](https://hexo.io/docs/deployment.html)

***Links:***
* [Hexo Documentation](https://hexo.io/docs/)