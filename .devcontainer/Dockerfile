FROM php:8.3-fpm

RUN apt-get update && apt-get install -y \
    libzip-dev \
    unzip \
    mariadb-client \
    git \
 && docker-php-ext-install zip pdo_mysql

# Composer のインストール（必要な場合）
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer
