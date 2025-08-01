FROM php:8.2-fpm-alpine

# Install ekstensi PHP yang diperlukan oleh Laravel
RUN apk add --no-cache \
    $PHPIZE_DEPS \
    git \
    mysql-client \
    autoconf \
    libxml2-dev \
    libzip-dev \
    libpng-dev \
    jpeg-dev \
    oniguruma-dev \
    g++ \
    make \
    sqlite-dev \
    postgresql-dev

RUN docker-php-ext-install pdo pdo_mysql pdo_sqlite
RUN docker-php-ext-configure gd --with-jpeg && docker-php-ext-install gd
RUN docker-php-ext-install pcntl opcache zip

# Install Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Atur direktori kerja
WORKDIR /var/www/html

# Ekspos port
EXPOSE 9000

# Jalankan perintah-perintah instalasi
# COPY composer.json composer.lock ./
# RUN composer install --no-dev --optimize-autoloader

CMD ["php-fpm"]
