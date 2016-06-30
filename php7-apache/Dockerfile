FROM php:apache

RUN a2enmod rewrite
RUN service apache2 restart

RUN apt-get update && apt-get install -y \
	libmcrypt-dev \
	libpng-dev

RUN docker-php-ext-install \
	bcmath \
	mbstring \
	mcrypt \
	mysqli \
	pdo_mysql \
	gd

RUN docker-php-ext-configure \
	mbstring

RUN docker-php-ext-enable \
	mbstring

RUN rm -r /var/lib/apt/lists/*