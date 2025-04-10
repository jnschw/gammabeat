---
author: Jürgen Schwarz
layout: post
title: Web analytics with Piwik
categories: Web
---

###Web analytics


Piwik is an open source web analytics software. It provides detailed reports 
on the website traffic, including popular reports such as which search engines 
and keywords visitors used to find a page, the language they speak, the 
most popular pages and other analytical reports.

<!-- more -->

#### Step 1: Setup a web server with apache

This is straightforward. Piwik and jekyll run with apache, nginx or 
lighthttpd.


#### Step 2: Install Piwik

I followed the instructions here to install Piwik using the debian package: 
<http://piwik.org/blog/2014/04/piwik-debian-package/>


Piwik requires some additional packages: 
{% highlight console %}
user@localhost:~/#sudo apt-get install php5-curl php5-cli php5-gd php5-geoip php5-mysql
{% endhighlight %}

And a database such as mysql. Create database, add user and grant privileges: 

{% highlight console %}
user@localhost:~/Downloads/#mysql -u root -p
{% endhighlight %}
{% highlight sql %}
mysql>CREATE DATABASE piwikdb;
mysql>CREATE USER 'piwik'@'localhost' IDENTIFIED BY 'password';
mysql>GRANT ALL PRIVILEGES ON piwikdb.* TO 'piwik'@'localhost';
{% endhighlight %}


Set the permissions in the piwik directory:
{% highlight console %}
user@localhost:/usr/share/piwik#sudo chown -R www-data:www-data config tmp
{% endhighlight %}


#### Step 3: Configure blog

Add the tracking code to the default template of the jekyll site by pasting
it before the end of the body tag:
 
{% highlight console %}

user@localhost:~site#nano /_layouts/default.html
 
{% endhighlight %}

Now update jekyll

{% highlight console %}

user@localhost:~/site#jekyll build --watch
 
{% endhighlight %}


#### Step 4: Modify apache.conf


{% highlight bash %}

#
# Piwik - Logs
Alias /piwik /usr/share/piwik
<Directory /usr/share/piwik>

    Order allow,deny
    Allow from all
    AllowOverride None
    Options Indexes FollowSymLinks

#    RewriteEngine On
#    RewriteCond %{REQUEST_FILENAME} !-d
#    RewriteCond %{REQUEST_FILENAME} !-f
#    RewriteRule .* index.php [L,QSA]

</Directory>
{% endhighlight %}

