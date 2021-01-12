# Исходный образ, он будет использован как основа
FROM php:7.4-fpm

# RUN выполняет идущую за ней команду в контексте нашего образа.
# В данном случае мы установим некоторые зависимости и модули PHP.
# Для установки модулей используем команду docker-php-ext-install.
# На каждый RUN создается новый слой в образе, поэтому рекомендуется объединять команды.
RUN apt-get update && apt-get install -y \
        apt-utils \
        curl \
        wget \
        git \
        zip \
        unzip \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
	    libpng-dev \
	    libonig-dev \
	    libzip-dev \
	    libmcrypt-dev \
	    libicu-dev \
    && pecl install mcrypt-1.0.3 \
	&& docker-php-ext-enable mcrypt \
    && docker-php-ext-install -j$(nproc) \
#        iconv \
        mysqli \
        pdo_mysql \
        zip \
	&& docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd

# xdebug
RUN pecl install xdebug

# phpunit
RUN wget https://phar.phpunit.de/phpunit-6.5.phar && \
        chmod +x phpunit-6.5.phar && \
        mv phpunit-6.5.phar /usr/local/bin/phpunit

# codecept
RUN wget http://codeception.com/codecept.phar && \
        chmod +x codecept.phar && \
        mv codecept.phar /usr/local/bin/codecept

# Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer --version=2.0.8

# Добавить свой php.ini
#ADD php.ini /usr/local/etc/php/conf.d/40-custom.ini

ENV COMPOSER_ALLOW_SUPERUSER 1

# Указываем рабочую директорию для PHP
WORKDIR /var/www/html

# Запускаем контейнер
CMD ["php-fpm"]