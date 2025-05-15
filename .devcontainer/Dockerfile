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

# GitHub CLI (gh) のインストール
RUN curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg && \
    chmod go+r /usr/share/keyrings/githubcli-archive-keyring.gpg && \
    echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" > /etc/apt/sources.list.d/github-cli.list && \
    apt-get update && \
    apt-get install -y gh

# MySQLクライアントの文字化け対策
RUN echo "[client]\ndefault-character-set=utf8mb4" > /root/.my.cnf

# Composer のインストール
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer
