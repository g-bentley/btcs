FROM php:5.6-fpm

# Originally from rkit/docker-phpstack
# --- SOFT --- #

RUN apt-get update && apt-get upgrade -y

RUN apt-get install -y \
    curl 
###	    openssh-client \
###	    libfreetype6-dev \
###	    libjpeg62-turbo-dev \
###	    libmcrypt-dev \
###	    libpng12-dev \
###	    zlib1g-dev \
###	    libssl-dev \
###	    g++ \
###	    libmemcached-dev \
###	    imagemagick \
###	    libmagickwand-6.q16-dev --no-install-recommends \
###	    wget \
###	    git \
###	    ruby \
###	    nodejs \
###	    npm

###	RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ && \
###	    docker-php-ext-install gd && \
###	    docker-php-ext-install opcache && \
###	    docker-php-ext-install zip && \
###	    docker-php-ext-install pdo_mysql && \
###	    docker-php-ext-install mysqli && \
###	    docker-php-ext-install mbstring

###	RUN pecl channel-update pecl.php.net && \
###	    pecl install redis && \
###	    pecl install mongo && \
###	    pecl install memcache && \
###	    pecl install memcached && \
###	    pecl install xdebug && \
###	    pecl install imagick

###	RUN echo "extension=mongo.so" > /usr/local/etc/php/conf.d/ext-mongo.ini && \
###	    echo "extension=redis.so" > /usr/local/etc/php/conf.d/ext-redis.ini && \
###	    echo "extension=memcache.so" > /usr/local/etc/php/conf.d/ext-memcache.ini && \
###	    echo "extension=memcached.so" > /usr/local/etc/php/conf.d/ext-memcached.ini && \
###	    echo "extension=imagick.so" > /usr/local/etc/php/conf.d/ext-imagick.ini && \
###	    echo "zend_extension=xdebug.so" > /usr/local/etc/php/conf.d/ext-xdebug.ini

# --- COMPOSER --- #

RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer

# --- PREPARE --- #

EXPOSE 9000

CMD ["php-fpm", "--allow-to-run-as-root"]
