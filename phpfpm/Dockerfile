FROM php:5.6-fpm

RUN apt-get update  && \
    curl -sSL https://deb.nodesource.com/setup_6.x | bash - && \
    apt-get install -y --no-install-recommends libssl-dev nodejs && \
    apt-get clean && \
    apt-get install -y git && \
    rm -rf /var/lib/apt/lists/* && \
    docker-php-ext-install bcmath mbstring && \
    docker-php-ext-enable opcache && \
    # Install php mongo driver with pecl
    pecl install mongo && \
    echo 'extension=mongo.so' > /usr/local/etc/php/conf.d/mongo.ini && \
    # Install composer
    curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer && \
    # Set higher memory limit due to the need of SF2
    echo "memory_limit=1024M" > /usr/local/etc/php/conf.d/memory_limit.ini && \
    # Reset ownership
    chown -R www-data:www-data /var/www/

EXPOSE 9000

USER www-data
