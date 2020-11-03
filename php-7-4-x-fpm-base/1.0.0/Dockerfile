FROM php:7.4-fpm-alpine3.12

########################################################################################
############################# Packages Extensions ######################################
########################################################################################

RUN apk --update add --no-cache \
    ${PHPIZE_DEPS} \
    oniguruma-dev \
    libpng-dev \
    openssl-dev \
    nginx \
    supervisor \
    gd \
    nano \
    libxml2-dev \
    git \
    curl \
    && rm -rf /var/cache/apk/*

########################################################################################
############################# Default Extensions #######################################
########################################################################################

RUN docker-php-ext-install \
        pdo_mysql \
        mbstring \
        gd \
        soap \
        xml \
        posix \
        tokenizer \
        ctype \
        pcntl \
        opcache

########################################################################################
############################# PECL Extensions ##########################################
########################################################################################
## Enable extension on $PHP_INI_DIR/conf.d/docker-php-ext-mongodb.ini
## this binary (docker-php-ext-enable) check if extension.so exists on php extension dir (init_get(extension_dir))
RUN pecl install apcu mongodb && docker-php-ext-enable apcu mongodb && chmod -R 755 /usr/local/lib/php/extensions/

########################################################################################
############################# Raw Installation Extensions ##############################
########################################################################################


########################################################################################
############################# Composer #################################################
########################################################################################
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer \
    && chown -R www-data:www-data /var/lib/nginx \
    && mkdir -p /app \
    && chown -R www-data:www-data /app

WORKDIR /app

ENTRYPOINT ["sh", "-c"]