FROM php:8.0-fpm

# define env variables
ENV APP_HOME=/var/www/html

USER root

# Set working directory
WORKDIR ${APP_HOME}

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
        git \
        zip \
        unzip \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install mysqli


# Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Copy existing application directory contents
COPY . ${APP_HOME}

# install composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer
RUN chmod +x /usr/bin/composer
ENV COMPOSER_ALLOW_SUPERUSER 1


RUN composer install --working-dir=${APP_HOME} --ignore-platform-reqs

RUN composer dump-autoload --working-dir=${APP_HOME}


RUN chown -R www-data:www-data ${APP_HOME}/storage/
RUN chown -R www-data:www-data ${APP_HOME}/bootstrap/cache/

# Expose port 9000 and start php-fpm server
EXPOSE 9000

CMD ["php-fpm"]
