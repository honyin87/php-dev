FROM php:7.4-apache
RUN apt-get update && apt-get install -y
RUN apt-get install libcurl4-openssl-dev  -y;
RUN apt-get install libonig-dev  -y;
RUN a2enmod rewrite
RUN service apache2 restart

RUN docker-php-ext-install mysqli && docker-php-ext-enable mysqli 
RUN docker-php-ext-install mbstring && docker-php-ext-enable mbstring 
RUN docker-php-ext-install curl && docker-php-ext-enable curl 
RUN pecl install redis && docker-php-ext-enable redis


RUN yes | pecl install xdebug \
    && echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)" > /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_enable=on" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_autostart=off" >> /usr/local/etc/php/conf.d/xdebug.ini