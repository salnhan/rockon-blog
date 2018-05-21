---
title: Work with Gulp
tags:
 - gulp
 - frontend
categories:
 - frontend
teaser: Install, configure, and run gulp tasks to compile your sass files or synschronize your browser.
---

Howto install gulp

# Table of Contents
  * [Chapter 1](#Installation)
  * [Chapter 2](#Using)
  * [Chapter 3](#Fazit)

### Installation

``` bash
$ npm install gulp --save-dev
```

In package.json

``` json
{
  "name": "hexo-site",
  "version": "0.0.0",
  "private": true,
  "hexo": {
    "version": "3.7.1"
  },
  "dependencies": {
    "hexo": "^3.2.0",
    "hexo-deployer-git": "^0.3.1",
    "hexo-generator-archive": "^0.1.4",
    "hexo-generator-category": "^0.1.3",
    "hexo-generator-index": "^0.2.0",
    "hexo-generator-tag": "^0.2.0",
    "hexo-renderer-ejs": "^0.3.0",
    "hexo-renderer-marked": "^0.3.0",
    "hexo-renderer-stylus": "^0.3.1",
    "hexo-server": "^0.2.0"
  },
  "devDependencies": {
    "gulp": "^3.9.1"
  }
}
```

### Using

### Fazit