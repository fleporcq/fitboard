FROM php:5.6-apache
 
# zlib1g package and zip php extension is for composer
# libicu is for intl
RUN apt-get update && apt-get install -y \
    libicu-dev \
    zlib1g-dev

RUN docker-php-ext-install \
    zip \ 
    pdo \
    pdo_mysql \ 
    intl \
    mbstring

# Workaround for write permission on write to MacOS X volumes
# See https://github.com/boot2docker/boot2docker/pull/534
RUN usermod -u 1000 www-data

# Add www-data to root group 
# Workaround to clear Symfony cache as root 
# and to have cache folder always writable for www-data
RUN usermod -a -G root www-data

# Copy additionals php.ini params
COPY php.ini /usr/local/etc/php/

# Copy project's virtualhost and enable it 
COPY vhost.conf /etc/apache2/sites-available/
RUN a2ensite vhost

# Enable Apache mod_rewrite
RUN a2enmod rewrite

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
