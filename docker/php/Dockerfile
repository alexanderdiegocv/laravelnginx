# Usa una imagen base de PHP 8.0 con FPM
FROM php:8.0-fpm

# Instala las dependencias necesarias para Laravel
RUN apt-get update && apt-get install -y \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    zip \
    unzip

# Instala las extensiones de PHP necesarias
RUN docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install pdo pdo_mysql mbstring exif pcntl bcmath xml

# Copia la configuración de PHP personalizada
# COPY php.ini /usr/local/etc/php/php.ini

# Establece el directorio de trabajo en la raíz de Laravel
WORKDIR /var/www

# Expone el puerto 9000 para PHP-FPM
EXPOSE 9000
