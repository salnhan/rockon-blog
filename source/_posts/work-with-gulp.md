---
title: Working with Gulp
date: 2018-09-04 10:32:24
tags:
 - gulp
 - frontend
categories:
 - frontend
teaser: Install, configure, and run gulp tasks to compile your sass files or synschronize your browser.
---

Gulp is a powerful tool to automate any tasks during the web development like minify css or recompile js or css files automatically if any changes.


## Content
  * [Installation](#Installation)
  * [Gulp component](#Gulp-component)
  * [Using Gulp task](#Using-Gulp-task)
  * [Refresh browser automatically](#Refesh-browser-automatically)
  * [Minify css, js](#Minify-css-js)

### Installation

Run follwing npm task
``` bash
$ npm install gulp --save-dev
```
In package.json gulp with current version  will be inserted.

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

### Gulp component

Gulp tasks will be defined in `Gulpfile.js`
A Gulpfile.js contains following components;
* `gulp.task`: gulp task
* `gulp.src`: source of file
* `gulp.dest`: destination of endfile
* `gulp.watch`: watching the change of file


``` js
gulp.task('task_one', function() {
  gulp.src('./js/*.js')
    .pipe(gulp.dest('dist/js'));

  gulp.src('./css/*.css')
    .pipe(gulp.dest('dist/css'));
});

gulp.task('watch_name', function(){
    gulp.watch('/css/*.css',  ['task_css'])
    gulp.watch('/js/*.js',  ['task_js'])
})

gulp.watch('js/**/*.js', function(event) {
  console.log('File ' + event.path + ' was ' + event.type + ', running tasks...');
});
```
### Using Gulp task

To run a gulp task
``` bash
$ gulp task_one
$ gulp watch_name
```

### Refesh browser automatically

To refresh the browser automatically after recompile the css or js file should the npm package ` browser-sync` be installed

``` bash
npm install browser-sync --save-dev
```

Config in Gulpfile.js

``` js
var gulp = require('gulp');
var browserSync = require('browser-sync').create();

gulp.task('serve', [], function () {
    browserSync.init({
        server: {
            baseDir: '.'
        }
    });
    gulp.watch("*.html").on('change', browserSync.reload);
    gulp.watch(['assets/js/*.js'], browserSync.reload);
    gulp.watch(['assets/css/*.css'], browserSync.reload);
});

gulp.task('default', ['serve']);
```

### Minify css, js

To minify css, js should the package `gulp-minify` and `gulp-minify-css` be installed

``` bash
npm install gulp-minify-css --save-dev
npm install gulp-minify --save-dev
```

Config in Gulpfile.js

``` js
gulp.task('compress', function() {
  /config minify js
  gulp.src('assets/js/*.js') //path to folder of js file
    .pipe(minify({
        exclude: ['tasks'],
        ignoreFiles: ['-min.js'] //ignore files
    }))
    .pipe(gulp.dest('dist/js')); //path to folder to contain js file after minify
  //config minify css
  gulp.src('assets/css/*.css') ///path to folder of css file
    .pipe(minifyCss({compatibility: 'ie8'}))
    .pipe(gulp.dest('dist/css')); //path to folder to contain css file after minify
});
```