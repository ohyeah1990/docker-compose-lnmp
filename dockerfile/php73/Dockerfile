# from image
FROM php:7.3-fpm

# extract source
# RUN docker-php-source extract \
#     # do important things \
#     && docker-php-source delete

# update && install dependency
RUN apt-get update && apt-get install -y \
	git \
	libzip-dev \
    zip \
	libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev

# install zip extension
RUN docker-php-ext-configure zip --with-libzip \
	&& docker-php-ext-install zip

# install redis extension
RUN pecl install redis-5.1.1 \
    && docker-php-ext-enable redis

# install redis extension
RUN pecl install swoole \
    && docker-php-ext-enable swoole

# install mysqli extension
RUN docker-php-ext-install mysqli

# install pdo_mysql extension
RUN docker-php-ext-install pdo_mysql

# install gd extension
RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd

# install opcache
RUN docker-php-ext-install opcache

# install composer
ENV COMPOSER_HOME /root/composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
ENV PATH $COMPOSER_HOME/vendor/bin:$PATH