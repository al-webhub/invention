FROM php:8.0.8-fpm

USER root

WORKDIR /var/www

RUN apt-get update && apt-get install -y  libonig-dev libpq-dev \
    build-essential \
    git \
    curl \
    zip \
    unzip \
    locales \
    libzip-dev \
    libonig-dev \
    libpng-dev \
    libjpeg62-turbo-dev \
    libwebp-dev libpng-dev libxpm-dev \
    libfreetype6 \
    libfreetype6-dev \
    libxml2-dev

RUN apt-get clean && rm -rf /var/lib/apt/lists/*

RUN docker-php-ext-install pdo_mysql mbstring zip exif pcntl gd
RUN docker-php-ext-configure gd --with-freetype --with-jpeg --with-webp

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin/ --filename=composer

COPY . /var/www

USER www-data

EXPOSE 9000
CMD ["php-fpm"]

