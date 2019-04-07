FROM php:7.2.10

RUN apt-get update && apt-get install -y \
    libicu-dev \
    git \
    wget \
    zip \
    curl \
    libcurl4-openssl-dev \
    libmcrypt-dev \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libpq-dev \
    librabbitmq-dev \
    sqlite


# PHP extensions
RUN docker-php-ext-install curl zip

# amqp
RUN pecl install amqp \
    && echo "extension=amqp.so" > $PHP_INI_DIR/conf.d/amqp.ini

RUN  docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql \
    && docker-php-ext-install pdo pdo_pgsql pdo_mysql pgsql mysqli

RUN pecl install xdebug && docker-php-ext-enable xdebug

# Create a user that will have ID 1000
RUN useradd sf --shell /bin/bash --home /home/sf \
    && mkdir /home/sf \
    && chown sf:sf /home/sf

# Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

USER sf
WORKDIR "/var/www/sources"
