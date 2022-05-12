FROM php:7-fpm

RUN docker-php-ext-install bcmath && docker-php-ext-enable bcmath

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
	libicu-dev \
	libzip-dev \
	zip \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd

RUN docker-php-ext-install intl mysqli pdo pdo_mysql zip
