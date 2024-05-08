FROM php:8.2.1-fpm

RUN apt-get update && apt-get upgrade -y

# Add NodeSource PPA
RUN curl -s https://deb.nodesource.com/setup_21.x | bash

RUN apt-get install -y \
    vim \
    nano \
    wget \
    curl \
    git \
    zip \
    nodejs \
    libicu-dev \
    libgettextpo-dev \
    libzip-dev \
    libmagickwand-dev \
    libpq-dev \
    openssl \
    libbz2-dev \
    libcurl4-openssl-dev \
    zlib1g-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libwebp-dev \
    libxml2-dev \
    libfreetype6-dev \
    supervisor \
    python3-pip \
    libsecp256k1-0 \
    procps \
    cron \
    default-mysql-client \
    libgmp-dev

RUN docker-php-source extract

# Install xdebug
RUN pecl install xdebug && \
    docker-php-ext-enable xdebug

# Install redis
RUN pecl install redis && \
    docker-php-ext-enable redis

# Other PHP Extensions
RUN docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) \
    bcmath \
    bz2 \
    calendar \
    exif \
    gd \
    gettext \
    intl \
    mysqli \
    opcache \
    pcntl \
    pdo \
    pdo_mysql \
    pdo_pgsql \
    soap \
    zip \
    gmp

# Install composer
ENV COMPOSER_ALLOW_SUPERUSER=1
RUN curl -sS https://getcomposer.org/installer | php -- \
    --filename=composer \
    --install-dir=/usr/local/bin

# Cleanup
RUN docker-php-source delete && \
  apt-get autoremove -y && \
  rm -rf /var/lib/apt/lists/*
