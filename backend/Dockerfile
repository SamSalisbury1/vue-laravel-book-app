# Use the official PHP image
FROM php:8.1-fpm

# Set the working directory
WORKDIR /app

# Install PHP dependencies
RUN apt-get update \
    && apt-get install -y libzip-dev zip \
    && docker-php-ext-configure zip \
    && docker-php-ext-install zip pdo_mysql

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Copy the Composer files
COPY composer.json composer.lock ./

# Set composer to super user
ENV COMPOSER_ALLOW_SUPERUSER=1

# Update composer packages
Run composer update

# Install PHP dependencies
RUN composer install --no-scripts --no-autoloader

# Copy the rest of the application code
COPY . .

# Expose the port the app will run on
EXPOSE 3303

# Command to run your app using CMD
CMD ["php", "artisan", "serve", "--host=0.0.0.0", "--port=3303"]

