FROM php:fpm

# Linux libraries
RUN apt-get update
RUN apt-get install -y \
    git \
    zip \
    curl \
    unzip \
    libicu-dev

# Fix permissions for PHP user
RUN usermod -u 1000 www-data

# PHP Extensions
RUN docker-php-ext-install \
    mysqli \
    intl

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Custom php.ini
RUN mv "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini"
COPY ./.docker/php/php-overrides.ini "$PHP_INI_DIR/conf.d/php-overrides.ini"
