FROM php:5-apache

COPY sources.list /etc/apt/sources.list

RUN apt-get update && apt-get install -y \ 
        php5-mysql \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng-dev \
    && docker-php-ext-install -j$(nproc) iconv mcrypt \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install -j$(nproc) mysqli 

COPY timezone.ini /usr/local/etc/php/conf.d/timezone.ini

ADD loganalyzer-4.1.6.tar.gz /tmp
RUN mv /tmp/loganalyzer-4.1.6/src/* /var/www/html
RUN mv /tmp/loganalyzer-4.1.6/contrib/* /var/www/html
RUN rm -rf /tmp/loganalyzer-4.1.6

COPY phpinfo.php /var/www/html/phpinfo.php

WORKDIR /var/www/html

RUN chmod +x configure.sh secure.sh
RUN ./configure.sh
