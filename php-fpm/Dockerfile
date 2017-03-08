FROM php:7.1.2-fpm-alpine

COPY php-fpm/php.ini /usr/local/etc/php/

RUN apk update && \
    apk add git

# https://sentinelstand.com/article/composer-install-in-dockerfile-without-breaking-cache
RUN curl -sS https://getcomposer.org/installer | \
    php -- --install-dir=/usr/bin/ --filename=composer
COPY app/composer.json /var/www/
COPY app/composer.lock /var/www/
WORKDIR /var/www
RUN composer install --no-scripts --no-autoloader --prefer-dist --no-dev
COPY app /var/www/
RUN composer dump-autoload --optimize

RUN rm ./composer.json ./composer.lock

CMD ["php-fpm"]