FROM php:7.4-fpm
RUN apt-get update && apt-get install --assume-yes \
        libzip-dev \
        libxml2-dev \
        libxslt-dev \
        libmagickcore-dev \
        libmagickwand-dev \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd \
    && rm -r /var/lib/apt/lists/* \
    && ln -sf /usr/local/etc/php/php.ini-production /usr/local/etc/php/php.ini

RUN docker-php-ext-install pdo_mysql bcmath pcntl sockets sysvsem xmlrpc xsl zip

RUN pecl install redis-5.1.1 \
    && pecl install yaf-3.0.9 \
    && pecl install imagick-3.4.4 \
    && docker-php-ext-enable redis yaf imagick
