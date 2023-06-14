FROM php:8.2-apache

COPY . / /var/www/html/

COPY --from=composer:2.5 /usr/bin/composer /usr/bin/composer

ENV APACHE_DOCUMENT_ROOT /var/www/html/public

RUN docker-php-ext-install pdo_mysql && \
    docker-php-ext-enable pdo_mysql

RUN sed -ri -e 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/sites-available/*.conf
RUN sed -ri -e 's!/var/www/!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/apache2.conf /etc/apache2/conf-available/*.conf