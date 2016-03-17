FROM php:apache

RUN apt-get update && apt-get install -y \
#        libfreetype6-dev \
#        libjpeg62-turbo-dev \
#        libpng12-dev \
#        php5-mysql \
#        php5-curl \
#        php5-imap \
#        php5-cli \
#        php7.0-mysql \
        libmcrypt-dev
RUN docker-php-ext-install mcrypt bcmath mbstring
RUN docker-php-ext-configure mbstring
RUN docker-php-ext-enable mbstring #\
#    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
#    && docker-php-ext-install -j$(nproc) gd \
RUN docker-php-ext-install -j$(nproc) mysqli