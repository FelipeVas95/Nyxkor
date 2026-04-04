# Usamos la imagen oficial de WordPress con Apache
FROM wordpress:latest

# 1. Instalamos librerías de PHP y herramientas útiles
RUN apt-get update && apt-get install -y \
    libbz2-dev \
    git \
    nano \
    vim \
    curl \
    sudo \
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

# 3. Gestión de usuario y permisos
# Añadimos al usuario adm-wb al grupo sudo para que puedas administrar si es necesario
RUN useradd -m -G www-data -s /bin/bash adm-wb

RUN usermod -d /var/www/html adm-wb
RUN usermod -s /bin/rbash adm-wb


# Ajustamos permisos iniciales
RUN chown -R adm-wb:www-data /var/www/html
RUN git config --system --add safe.directory /var/www/html
WORKDIR /var/www/html

# 5. (Opcional) Cambiar el usuario por defecto para VS Code
# Si quieres que al abrir la terminal siempre seas adm-wb:
USER adm-wb




# chmod 750 /home
#chmod 700 /root
#find /ruta/a/tu/codigo -type d -exec chmod 755 {} +
#find /ruta/a/tu/codigo -type f -exec chmod 644 {} +