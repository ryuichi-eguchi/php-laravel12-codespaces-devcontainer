FROM php:8.3-fpm

# 必要なパッケージのインストール
RUN apt-get update && apt-get install -y \
    libzip-dev \
    unzip \
    mariadb-client \
    git \
    curl \
    nodejs \
    npm \
 && docker-php-ext-install zip pdo_mysql

# Composer のインストール
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer
