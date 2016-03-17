FROM php:7-fpm
RUN apt-get update && apt-get install -y \
        libmcrypt-dev
RUN docker-php-ext-install mcrypt bcmath mbstring
RUN docker-php-ext-configure mbstring
RUN docker-php-ext-enable mbstring
#    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
#    && docker-php-ext-install -j$(nproc) gd \
RUN docker-php-ext-install -j$(nproc) mysqli