FROM php:7.4.9-fpm-alpine

ARG UID
ARG GID

RUN addgroup -g $GID -S web-app \
  && adduser -u $UID -S -G web-app web-app

# Необходимые инструменты (описание что и зачем в README.md)
RUN apk add --update --no-cache \
bash \
curl \
wget \
rsync \
openssl \
ca-certificates \
openssh \
git \
tzdata \
openntpd \
libxrender \
fontconfig \
libc6-compat \
mysql-client \
gnupg \
binutils-gold \
autoconf \
g++ \
gcc \
libgcc \
linux-headers \
make \
freetype \
libpng \
libjpeg-turbo \
freetype-dev \
libpng-dev \
libjpeg-turbo-dev \
zlib-dev \
libzip-dev

# Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer \
    && chmod 755 /usr/bin/composer

# Install PHP extensions
RUN  docker-php-ext-install \
bcmath \
pdo_mysql \
gd \
zip \
&& pecl install xdebug && docker-php-ext-enable xdebug

