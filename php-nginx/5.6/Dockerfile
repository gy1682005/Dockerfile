FROM gy1682005/php-fpm:5.6
MAINTAINER tanghao <gy1682005@qq.com>

RUN yum install -y nginx && yum clean all

RUN mkdir -p /var/www/html &&\
    echo "<?php phpinfo();?>" > /var/www/html/index.php &&\
    chown -R apache:apache /var/www/html

COPY config/nginx.conf /etc/nginx/
COPY config/nginx.ini /etc/supervisord.d/

WORKDIR /var/www/html
EXPOSE 80 8080