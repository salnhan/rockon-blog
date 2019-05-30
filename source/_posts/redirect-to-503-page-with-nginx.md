---
title: Redirect to maintenance page with nginx
date: 2019-05-30 12:16:31
tags:
 - nginx
 - 503
 - redirect
categories:
 - infrastructure
teaser: Redirecting to a Custom Nginx Maintenance Page temporarily
---

**Scenario:** you want to inform clients that the website temporary out of service because of down for maintenance, here’s the (not entirely intuitive) way to do that in Nginx.

{% img logo-icon http://nginx.org/nginx.png 352 72 nginx logo %}

&nbsp;

**Gain:** With following solution,  whenever you need to take your site offline, simply create the file 503 Service Unavailable HTML Page in the root diretory. If the file exists, Nginx will serve it with a 503 status code, if not, it will proceed as usual.

#### I. Create a custom 503 Service Unavailable HTML Page

First, you need to create a custom http 503 page at website root directory

``` bash
vi /var/www/htdocs/mysite/maintenance.html
```

``` html
<html>
  <head>
    <title>Error 503 Service Unavailable</title>
  </head>
  <body>
    <h1>503 Service Unavailable</h1>
    Our apologies for the temporary inconvenience. The requested URL generated 503 "Service Unavailable" error due to overloading or maintenance of the server. 
  </body>
</html>
```
&nbsp;

#### II. Update Nginx Configuration

Edit `/etc/nginx/config/nginx.conf`

``` bash
vi /etc/nginx/config/nginx.conf
```

Update configuration as follows

``` bash
server {
        listen        80;
        server_name   mysite.com;
        root          /var/www/htdocs/mysite/;

        location / {
            if (-f $document_root/maintenance.html) {
                return 503;
           }
            ... # the rest of your config goes here
         }

        error_page 503 @maintenance;
        location @maintenance {
                rewrite ^(.*)$ /maintenance.html break;
        }
}
```
Finally reload the nginx web server

``` bash
# reload instead of restart
$ service nginx reload
```