FROM centos:7
MAINTAINER tanghao <gy1682005@qq.com>

RUN yum install -y epel-release &&\
    yum install -y https://mirror.webtatic.com/yum/el7/webtatic-release.rpm &&\
    yum install -y supervisor caddy \
        php56w php56w-common php56w-cli php56w-fpm php56w-process php56w-tidy php56w-xml php56w-xmlrpc \
        php56w-bcmath php56w-mbstring php56w-mcrypt php56w-gd php56w-pdo php56w-mysqlnd php56w-imap php56w-opcache \
        php56w-pear php56w-pecl-apcu php56w-pecl-geoip php56w-pecl-igbinary php56w-pecl-imagick php56w-pecl-memcached php56w-pecl-redis &&\
    yum clean all

RUN mkdir -p /var/www/html &&\
    echo "<?php phpinfo();?>" > /var/www/html/index.php &&\
    chown -R apache:apache /var/www/html

COPY config/caddy.conf /etc/caddy/caddy.conf
COPY config/supervisord.conf /etc/supervisor/conf.d/supervisord.conf

WORKDIR /var/www/html
EXPOSE 80 8080

CMD ["supervisord", "-c", "/etc/supervisor/conf.d/supervisord.conf"]