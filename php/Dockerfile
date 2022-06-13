# FROM phpdockerio/php:7.4-fpm
# ENV PHP_MEMORY_LIMIT=2G
# RUN apt-get update \
#     && apt-get -y --no-install-recommends install \
#     php7.4-memcached \
#     php7.4-memcache \
#     php7.4-mbstring \
#     php7.4-mysql \
#     php7.4-intl \
#     #php7.4-xdebug \
#     php7.4-interbase \
#     php7.4-soap \
#     php7.4-gd \
#     php7.4-imagick \
#     php7.4-opcache \
#     php7.4-zip \
#     php-pear php7.4-dev libmcrypt-dev gcc make autoconf libc-dev pkg-config \
#     && pecl install mcrypt-1.0.4 \
#     && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*
# # DO NOT install php7.4-xdebug package for site running in production! It will slow it down significantly.

# COPY ./php.ini /etc/php/7.4/fpm/conf.d/90-php.ini
# COPY ./php.ini /etc/php/7.4/cli/conf.d/90-php.ini
# #COPY ./php.ini /usr/local/etc/php/php.ini

# RUN usermod -u 1000 www-data

# WORKDIR "/var/www/"

# CMD ["php-fpm"]

# EXPOSE 9000


FROM phpdockerio/php:7.4-fpm
# https://github.com/bitrixdock/bitrixdock/blob/master/php74/Dockerfile

RUN apt-get update \
    && apt-get -y --allow-downgrades --no-install-recommends install \
    php7.4-memcached \
    php7.4-memcache \
    php7.4-mbstring \
    php7.4-mysql \
    php7.4-intl \
    php7.4-interbase \
    php7.4-soap \
    php7.4-gd \
    php7.4-imagick \
    php7.4-opcache \
    php7.4-zip \
    php-pear php7.4-dev libmcrypt-dev gcc make autoconf libc-dev pkg-config \
    msmtp \
    msmtp-mta \
    sudo \
    cron \
    && pecl install mcrypt-1.0.4 \
    && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

# msmtp to allow email sending
# msmtp-mta to allow sendmail usage with msmtp
# sudo to allow create logfile with www-data user
# cron to run cronjobs in a separate container
COPY ./php.ini /etc/php/7.4/fpm/conf.d/90-php.ini
COPY ./php.ini /etc/php/7.4/cli/conf.d/90-php.ini
RUN usermod -u 1000 www-data
RUN groupmod -g 1000 www-data
WORKDIR "/var/wwww/"
EXPOSE 9000