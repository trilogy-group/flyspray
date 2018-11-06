FROM php:5-apache-jessie

RUN apt-get update && apt-get install -y unzip curl libpng-dev zlib1g-dev && \
    docker-php-ext-install mysql mysqli gd
