FROM php:8.0-fpm

WORKDIR /var/www
COPY . .

RUN apt-get update && apt-get install -y libpng-dev libjpeg-dev libfreetype6-dev
RUN docker-php-ext-configure gd --with-freetype --with-jpeg
RUN docker-php-ext-install gd

COPY . /var/www
RUN composer install

EXPOSE 9000
CMD ["php-fpm"]