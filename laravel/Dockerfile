# Use the official PHP 8.2 Apache image
FROM php:8.2-apache

# Install system dependencies

RUN apt-get update && apt-get install -y \
    git \
    unzip \
    libzip-dev \
    curl \
    libexif-dev \  
    libjpeg-dev \  
    libpng-dev \   
    && docker-php-ext-install gd zip pdo_mysql exif \
    && apt-get install -y nodejs 

RUN docker-php-ext-install bcmath
# Install Composer globally
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN curl -fsSL https://deb.nodesource.com/setup_18.x | bash - \
    && apt-get install -y nodejs

# Set working directory
WORKDIR /var/www/html

# Install MySQL client

# Configure Apache document root to /public directory of Laravel
RUN sed -i -e 's!/var/www/html!/var/www/html/public!g' /etc/apache2/sites-available/000-default.conf

# Enable Apache rewrite for .htaccess support
RUN a2enmod rewrite

# Set permissions to storage folder to make it writable
#RUN chown -R www-data:www-data /var/www/html/storage /var/www/html/bootstrap/cache

# Expose port 80 within the container (default HTTP port)
EXPOSE 80

# Start Apache server (entry point)
CMD ["apache2-foreground"]

