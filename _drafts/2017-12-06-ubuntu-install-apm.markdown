---
layout: post
title: Ubuntu 16.04 에서 기본적인 APM(Apache+PHP+MariaDB) 설치하기
date:   2017-12-06 15:11:01 +0900
categories: blog jekyll github
excerpt: Ubuntu 16.04 에서 기본적인 APM(Apache+PHP+MariaDB)를 설치하는 방법을 설명합니다.
author: Lucy
---
## 패키지 설치전
저장소 패키지 목록을 업데이트를 해줍니다.
{% highlight update  %}
$ sudo apt-get update
{% endhighlight %}

기존에 설치되어 있던 패키지를 업데이트 합니다.
{% highlight upgrade  %}
$ sudo apt-get upgrade
{% endhighlight %}

## Apache
웹 서버로 Apache2를 설치합니다.
{% highlight install  %}
$ sudo apt-get install apache2
{% endhighlight %}

Apache 실행
{% highlight install  %}
$ sudo service apache2 start
{% endhighlight %}

Apache 재시작
{% highlight install  %}
$ sudo /etc/init.d/apache2 restart
{% endhighlight %}

루트 기본 디렉토리 변경
{% highlight install  %}
$ sudo vi /etc/apache2/sites-available/000-default.conf    
  =>  DocumentRoot /var/www/html 수정
$ sudo vi /etc/apache2/apache2.conf
  => <Directory /var/www/html> 수정

$ sudo /etc/init.d/apache2 restart
{% endhighlight %}

## MariaDB
RDBMS는 Mariadb로 설치합니다.
{% highlight install  %}
$ sudo apt-get install mariadb-server
{% endhighlight %}

초기설정시 root의 권한을 풀고 비밀번호를 설정                     
{% highlight install  %}
$ sudo mysql -u root
MariaDB [(none)]> use mysql;
MariaDB [mysql]> UPDATE user SET plugin='' WHERE user='root';
MariaDB [mysql]> UPDATE user SET password=PASSWORD('내패스워드') WHERE user='root';
MariaDB [mysql]> FLUSH PRIVILEGES; // 수정사항 적용
{% endhighlight %}

계정 비밀번호 재설정
{% highlight install  %}
$ mysql -u root -p
MariaDB [(none)]> use mysql;
MariaDB [mysql]> update user set password = password('비밀번호') WHERE user='user1';
MariaDB [mysql]> flush privileges;
{% endhighlight %}

## PHP
PHP 버전은 7.0으로 설치합니다.
{% highlight install %}
$ sudo apt-get install php7.0
{% endhighlight %}

PHP와 Apache를 연동시켜줍니다.
{% highlight install %}
$ sudo apt-get install libapache2-mod-php7.0
{% endhighlight %}

## phpMyAdmin
phpMyAdmin을 설치합니다.
{% highlight install  %}
$ sudo apt-get install phpmyadmin
{% endhighlight %}

접속이 안될경우 apache2.conf에 Include /etc/phpmyadmin/apache.conf 를 추가합니다.
{% highlight install  %}
$ sudo vi /etc/apache2/apache2.conf
$ sudo /etc/init.d/apache2 restart
{% endhighlight %}
<br>
<br>
