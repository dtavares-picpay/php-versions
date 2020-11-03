FROM php:7.4.0-fpm-alpine3.10

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

#### New Relic
RUN mkdir -p /etc/default \
    && curl -sS "https://download.newrelic.com/php_agent/archive/9.12.0.268/newrelic-php5-9.12.0.268-linux.tar.gz" | tar -C /tmp -zx \
    && export NR_INSTALL_USE_CP_NOT_LN=1 \
    && export NR_INSTALL_SILENT=1 \
    && /tmp/newrelic-php5-*/newrelic-install install \
    && cp /etc/newrelic/newrelic.cfg.template /etc/newrelic/newrelic.cfg \
    && mkdir /lib64 \
    && ln -s /lib/libc.musl-x86_64.so.1 /usr/lib/ld-linux-x86-64.so.2 \
    && ln -s /lib/libc.musl-x86_64.so.1 /lib64/ld-linux-x86-64.so.2


########################################################################################
############################# Composer #################################################
########################################################################################
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer \
    && chown -R www-data:www-data /var/lib/nginx \
    && chown -R www-data:www-data /var/tmp/nginx \
    && mkdir -p /app \
    && chown -R www-data:www-data /app

RUN php -m
RUN php -i | grep apcu
RUN php -i | grep newrelic

WORKDIR /app

ENTRYPOINT ["sh", "-c"]