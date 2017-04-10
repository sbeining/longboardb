FROM php:fpm-alpine

RUN apk --no-cache add icu-dev \
 && docker-php-ext-install intl \
 && apk --no-cache add autoconf gcc g++ libtool make \
 && pecl install xdebug \
 && echo "zend_extension=xdebug.so" > /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
 && echo "extension=apcu.so" /usr/local/etc/php/conf.d/docker-php-ext-apcu.ini \
 && pecl install apcu \
 && apk del autoconf gcc g++ libtool make \
 && php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
 && php composer-setup.php \
 && php -r "unlink('composer-setup.php');"

COPY ./php.ini /usr/local/etc/php/
