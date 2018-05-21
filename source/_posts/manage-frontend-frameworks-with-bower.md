---
title: Using bower
tags: [bower, frontend]
categories: [frontend, bower]
teaser: Install and manage frontend packages by using bower. Web sites are made of lots of things frameworks, libraries, assets, and utilities. Bower manages all these things for you.
date: 2018.02.01
---

![bower logo](https://bower.io/img/bower-logo.svg "Logo Bower")

Web sites are made of lots of things — frameworks, libraries, assets, and utilities. Bower manages all these things for you.
Keeping track of all these packages and making sure they are up to date (or set to the specific versions you need) is tricky. Bower to the rescue!
Bower can manage components that contain HTML, CSS, JavaScript, fonts or even image files. Bower doesn’t concatenate or minify code or do anything else - it just installs the right versions of the packages you need and their dependencies.


### Install bower

**Prerequisite**
 node muss be installed

```bash
# bower muss be installed globally
$ npm install -g bower
```

### Create file bower.json

in your project's folder run following command complete the requisitions (you can press enter):

```bash
$ bower init
```

File bower.json will be created in your project's folder like:

```json
{
  "name": "hexo-theme-rockon-blog",
  "description": "",
  "main": "",
  "authors": [
    "salnhan <mascit10@gmail.com>"
  ],
  "license": "MIT",
  "homepage": "https://github.com/salnhan/hexo-theme-rockon-blog",
  "ignore": [
    "**/.*",
    "node_modules",
    "bower_components",
    "test",
    "tests"
  ]
}
```

### configure your current working directory in .bowerrc

you can define in `.bowerrc`, in which directory the installed packages will be stored

```json
{
	"directory" : "source/components"
}
```

More configuration in .bowerrc can be found [hier](https://bower.io/docs/config/)

### Install new package and save it to bower.json

**If you want to install the newest version of package**

```bash
# install bootstrap with current version (4.1.1)
$ bower install bootstrap --save
```

Now have a look to file bower.json:

```json
{
  "name": "hexo-theme-rockon-blog",
  "description": "",
  "main": "",
  "authors": [
    "salnhan <mascit10@gmail.com>"
  ],
  "license": "MIT",
  "homepage": "https://github.com/salnhan/hexo-theme-rockon-blog",
  "ignore": [
    "**/.*",
    "node_modules",
    "bower_components",
    "test",
    "tests"
  ],
  "dependencies": {
    "bootstrap": "^4.1.1"
  }
}
```

**If you want to install the specify version of package**

```bash
# install bootstrap with version 3.0.0
$ bower install bootstrap#3.0.0 --save
```

**useful frontend packages can be install via bower**

```bash
# install jquery with current version
$ bower install jquery --save
# install bootstrap with current version
$ bower install bootstrap --save
# install fontawesome with current version
$ bower install fontawesome --save
# install parallax.js with current version
$ bower install parallax.js --save
```

### Install all packages in bower.json

To install all packages in bower.json, just run:

```bash
$ bower install
```

### Uninstall package and remove it from bower.json

To uninstall a package and remove it from the bower.json, just run:

```bash
$ bower uninstall bootstrap --save
```

### Clear bower cache

Bower uses cache to save installed packages. This means, bower will download packages at the first time. At the next install will bower use the package in cache instead of connection to source

```bash
# first install of jquery (version 3.3.1)
$ bower install jquery#3.3.1 --save
bower jquery#3.3.1            cached https://github.com/jquery/jquery-dist.git#3.3.1
bower jquery#3.3.1            validate 3.3.1 against https://github.com/jquery/jquery-dist.git#3.3.1
bower jquery#3.3.1            install jquery#3.3.1
```
If you want to clear bower cache

```bash
$ bower cache clear
```

***Links:***
* [Bower Homepage](https://bower.io/)
* [Bower Configuration](https://bower.io/)
