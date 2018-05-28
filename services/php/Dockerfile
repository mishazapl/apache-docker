FROM php:7.2-apache

RUN apt-get update && apt-get install -y libpq-dev \
        curl \
        wget \
        git \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
    && docker-php-ext-install -j$(nproc) iconv mbstring zip \
    && docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql \
    && docker-php-ext-install pdo pdo_pgsql pgsql
    
# Куда же без composer'а.
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN composer global require "laravel/installer"

# Раскоментировать после git clone.
#RUN cd /var/www && composer update

# Указываем рабочую директорию для PHP
WORKDIR /var/www

