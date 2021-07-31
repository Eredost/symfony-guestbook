FROM php:8.0.9-fpm-alpine3.14

RUN \
    apk update \
    && apk add --no-cache \
    postgresql-dev \
    git \
    zip \
    unzip \
    bash \
    apache2 \
    apache2-proxy \
    openrc \
    && docker-php-ext-install pdo_pgsql

RUN mkdir -p /run/apache2
COPY ./docker/php-fpm/conf.d/* /etc/apache2
COPY ./docker/php-fpm/php-fpm.d/* /usr/local/etc/php-fpm.d

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
    && wget https://get.symfony.com/cli/installer -O - | bash && mv /root/.symfony/bin/symfony /usr/local/bin/symfony

CMD sh -c /usr/sbin/httpd -D FOREGROUND ; /usr/local/sbin/php-fpm -F -R

WORKDIR /var/www/guestbook
