# Usa una imagen base de PHP 8.0 con FPM
FROM php:8.0-fpm

# Instala las dependencias necesarias para Laravel
RUN apt-get update && apt-get install -y \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libmagickwand-dev \
    libzip-dev \
    libpq-dev \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    zip \
    unzip \
    locales \
    jpegoptim optipng pngquant gifsicle \
    vim \
    curl \
    unzip \
    nano

RUN pecl install imagick

# Instala extensiones de PHP necesarias para Laravel
RUN docker-php-ext-install pdo_mysql exif gd
RUN docker-php-ext-install zip
RUN docker-php-ext-enable imagick
RUN docker-php-ext-install pdo pdo_pgsql

# Instala Composer
# COPY --from=composer:2.6.3 /usr/bin/composer /usr/bin/composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# RUN docker-php-ext-configure gd --with-freetype --with-jpeg \
#     && docker-php-ext-install -j$(nproc) gd \
#     && docker-php-ext-install pdo pdo_mysql mbstring exif pcntl bcmath xml

# Copia la configuración de PHP personalizada
# COPY php.ini /usr/local/etc/php/php.ini

ENV COMPOSER_ALLOW_SUPERUSER 1

# Establece el directorio de trabajo en la raíz de Laravel
# WORKDIR /var/www
WORKDIR /usr/share/nginx/html

RUN chown -R www-data:www-data /usr/share/nginx/html \
    && chmod -R 755 /usr/share/nginx/html
    # && composer install
    # && chmod -R 755 /usr/share/nginx/html \
    # && chown -R www-data:www-data storage \
    # && chown -R www-data:www-data bootstrap/cache

# Expone el puerto 9000 para PHP-FPM
EXPOSE 9000

# # Usa una imagen base de PHP 8.0 con FPM
# FROM php:8.0-fpm

# # Instala las dependencias necesarias para Laravel
# RUN apt-get update && apt-get install -y \
#     libfreetype6-dev \
#     libjpeg62-turbo-dev \
#     libpng-dev \
#     libonig-dev \
#     libxml2-dev \
#     zip \
#     unzip

# # Instala las extensiones de PHP necesarias
# RUN docker-php-ext-configure gd --with-freetype --with-jpeg \
#     && docker-php-ext-install -j$(nproc) gd \
#     && docker-php-ext-install pdo pdo_mysql mbstring exif pcntl bcmath xml

# # Copia la configuración de PHP personalizada
# # COPY php.ini /usr/local/etc/php/php.ini

# # Establece el directorio de trabajo en la raíz de Laravel
# # WORKDIR /var/www
# WORKDIR /usr/share/nginx/html

# # Expone el puerto 9000 para PHP-FPM
# EXPOSE 9000
