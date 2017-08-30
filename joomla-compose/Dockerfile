FROM php:7-fpm

RUN apt-get update && apt-get install -y libpng12-dev libjpeg-dev libmcrypt-dev zip unzip && rm -rf /var/lib/apt/lists/* \
    && docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr \
    && docker-php-ext-install gd
RUN docker-php-ext-install mysqli
RUN docker-php-ext-install mcrypt
RUN docker-php-ext-install pdo pdo_mysql
RUN docker-php-ext-install zip

RUN usermod -u 1000 www-data

EXPOSE 8000

CMD ["php-fpm"]
