FROM php:apache

RUN a2enmod rewrite
RUN service apache2 restart

RUN apt-get update && apt-get install -y --no-install-recommends \
	libmcrypt-dev \
	libpng-dev \
	libfreetype6-dev \
	libjpeg62-turbo-dev \
	libpng12-dev

RUN docker-php-ext-install -j$(nproc) \
	bcmath \
	iconv \
	mbstring \
	mcrypt \
	mysqli \
	pdo_mysql

RUN docker-php-ext-configure \
	gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/

RUN docker-php-ext-configure \
	mbstring

RUN docker-php-ext-enable \
	mbstring

RUN docker-php-ext-install -j$(nproc) \
	gd

RUN rm -r /var/lib/apt/lists/*