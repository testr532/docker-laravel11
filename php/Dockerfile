FROM php:8.2.10-apache

RUN apt update \
        && apt install -y \
            g++ \
            libicu-dev \
            libpq-dev \
            libzip-dev \
            zip \
            zlib1g-dev \
            npm \
            nodejs \
            vim \
        && docker-php-ext-install \
            intl \
            opcache \
            pdo \
            pdo_pgsql \
            pgsql \
            pdo_mysql \
            mysqli

# debian系でmod_rewriteを有効にする
RUN a2enmod rewrite

WORKDIR /var/www/

#RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

#Composerのインストール: マルチステージビルド
COPY --from=composer:2.7.6 /usr/bin/composer /usr/bin/composer

