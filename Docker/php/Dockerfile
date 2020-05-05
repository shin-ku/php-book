FROM php:7.2-apache

# modify apache web root
ENV APACHE_DOCUMENT_ROOT /var/www/html/app/webroot
RUN sed -ri -e 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/sites-available/*.conf \
&& sed -ri -e 's!/var/www/!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/apache2.conf /etc/apache2/conf-available/*.conf \
&& a2enmod rewrite

# install extra package
RUN apt-get update && apt-get install -y libicu-dev zip unzip \
&& docker-php-ext-install -j$(nproc) intl \
&& docker-php-ext-install -j$(nproc) pdo_mysql

# modify timezone
RUN ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime

# copy host data to /var/www/html
COPY . /var/www/html

# composer setting
ENV COMPOSER_ALLOW_SUPERUSER 1
COPY --from=composer:1.7 /usr/bin/composer /usr/bin/composer

RUN cd ./app && composer install --no-dev -o