FROM php:8.1-fpm-alpine
RUN apk update \
    && apk add --no-cache --update linux-headers ${PHPIZE_DEPS} \
    && apk add libzip-dev curl-dev \
       freetype-dev \
       libjpeg-turbo-dev \
       libpng-dev \
&& docker-php-ext-install \
       exif \
       mysqli \
       pdo \
       pdo_mysql \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install opcache
    
RUN docker-php-ext-install exif
RUN docker-php-ext-install curl
RUN docker-php-ext-install zip
RUN docker-php-ext-install pcntl
RUN docker-php-ext-enable mysqli
RUN docker-php-ext-enable gd
