FROM php:8.0.9-fpm-alpine3.14

RUN apk update \
    && apk add --no-cache git zip unzip bash postgresql-dev openrc \
    && docker-php-ext-install pdo_pgsql

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
    && wget https://get.symfony.com/cli/installer -O - | bash && mv /root/.symfony/bin/symfony /usr/local/bin/symfony

WORKDIR /var/www/guestbook
