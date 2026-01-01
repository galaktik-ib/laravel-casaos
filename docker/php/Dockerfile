FROM php:8.3-fpm

# Install dependency sistem
RUN apt-get update && apt-get install -y \
    git curl zip unzip \
    libpng-dev libonig-dev libxml2-dev \
    mariadb-client nodejs npm \
    && docker-php-ext-install \
        pdo pdo_mysql mbstring bcmath gd

RUN echo "upload_max_filesize=30M" > /usr/local/etc/php/conf.d/uploads.ini \
 && echo "post_max_size=30M" >> /usr/local/etc/php/conf.d/uploads.ini \
 && echo "memory_limit=256M" >> /usr/local/etc/php/conf.d/uploads.ini

# Install Composer
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

WORKDIR /var/www