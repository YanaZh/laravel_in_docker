FROM php:8.2-fpm-alpine

WORKDIR /var/www/html

RUN apk update && apk add --no-cache \
    git \
    postgresql-dev \
    oniguruma-dev \
    libzip-dev \
    libpng-dev \
    less \
    $PHPIZE_DEPS

RUN docker-php-ext-install pdo pdo_pgsql pdo_mysql mbstring zip pcntl intl bcmath

COPY --from=composer:latest /usr/bin/composer /usr/local/bin

RUN addgroup -g 1000 -S www && \
    adduser -u 1000 -S www -G www

USER www

EXPOSE 9000

CMD ["php-fpm"]