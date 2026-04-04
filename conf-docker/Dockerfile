# Usamos la imagen oficial de WordPress con Apache
FROM wordpress:latest

# 1. Instalamos librerías de PHP y herramientas útiles
RUN apt-get update && apt-get install -y \
    libbz2-dev \
    git \
    nano \
    vim \
    curl \
    wget \
    unzip \
    zip \
    cron \
    net-tools \
    iproute2 \
    rsync \
    bash-completion \
    && docker-php-ext-install bz2 \
    && rm -rf /var/lib/apt/lists/*

# 2. Configuración de PHP para permitir archivos más grandes
RUN echo "upload_max_filesize = 64M \npost_max_size = 64M" > /usr/local/etc/php/conf.d/uploads.ini

# 3. Permisos: Aseguramos que el servidor pueda escribir en el volumen
# Esto ayuda a evitar el error de "Operation not permitted" en el arranque
RUN chown -R www-data:www-data /var/www/html

WORKDIR /var/www/html