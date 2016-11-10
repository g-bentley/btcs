FROM php:5.6.26-fpm

# Originally from rkit/docker-phpstack
# --- SOFT --- #

RUN apt-get update && apt-get install -y \
    openssh-client \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libmcrypt-dev \
    libpng12-dev \
    zlib1g-dev \
    libssl-dev \
    g++ \
    libmemcached-dev \
    imagemagick \
    libmagickwand-6.q16-dev --no-install-recommends \
    wget \
    git \
    ruby \
    nodejs \
    npm

RUN ln -s /usr/lib/x86_64-linux-gnu/ImageMagick-6.8.9/bin-Q16/MagickWand-config /usr/bin

RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ && \
    docker-php-ext-install gd && \
    docker-php-ext-install opcache && \
    docker-php-ext-install zip && \
    docker-php-ext-install pdo_mysql && \
    docker-php-ext-install mysqli && \
    docker-php-ext-install mbstring

RUN pecl channel-update pecl.php.net && \
    pecl install redis && \
    pecl install mongo && \
    pecl install memcache && \
    pecl install memcached && \
    pecl install xdebug && \
    pecl install imagick

RUN echo "extension=mongo.so" > /usr/local/etc/php/conf.d/ext-mongo.ini && \
    echo "extension=redis.so" > /usr/local/etc/php/conf.d/ext-redis.ini && \
    echo "extension=memcache.so" > /usr/local/etc/php/conf.d/ext-memcache.ini && \
    echo "extension=memcached.so" > /usr/local/etc/php/conf.d/ext-memcached.ini && \
    echo "extension=imagick.so" > /usr/local/etc/php/conf.d/ext-imagick.ini && \
    echo "zend_extension=xdebug.so" > /usr/local/etc/php/conf.d/ext-xdebug.ini

# --- COMPOSER --- #

RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer

# --- ICU --- #

RUN apt-get install tzdata && \
    wget http://download.icu-project.org/files/icu4c/55.1/icu4c-55_1-src.tgz -O icu4c-55_1-src.tgz && \
    tar -zxvf icu4c-55_1-src.tgz && \
    mkdir -p build && \
    cd build && \
    CPPFLAGS="-DU_CHARSET_IS_UTF8=1" ../icu/source/runConfigureICU Linux && \
    make install && \
    apt-get install -y libicu-dev && \
    pecl install intl && \
    echo "extension=intl.so" > /usr/local/etc/php/conf.d/ext-intl.ini

# --- PREPARE --- #

EXPOSE 9000

CMD ["php-fpm", "--allow-to-run-as-root"]
