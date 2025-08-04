FROM php:8.4-apache

# Instala git, unzip e Composer
RUN apt-get update && apt-get install -y git unzip curl \
    && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Instala a extensão sockets (usada pelo php-amqplib)
RUN docker-php-ext-install sockets

WORKDIR /var/www/html

RUN a2enmod rewrite

EXPOSE 80