FROM php:8.1-cli

WORKDIR /var/www/html

# Installer les dépendances système et extensions PHP courantes pour Symfony 5.4
RUN apt-get update && apt-get install -y --no-install-recommends \
    git unzip libzip-dev zlib1g-dev libicu-dev libxml2-dev libonig-dev \
    libpng-dev libjpeg-dev libfreetype6-dev ca-certificates \
  && docker-php-ext-configure gd --with-freetype --with-jpeg \
  && docker-php-ext-install -j$(nproc) pdo_mysql zip intl xml mbstring gd opcache \
  && pecl install apcu || true \
  && docker-php-ext-enable apcu || true \
  && rm -rf /var/lib/apt/lists/*

# Installer composer (depuis l'image officielle composer)
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

# Copier le projet (le code hôte sera monté par docker-compose en dev, mais on laisse copy pour build si besoin)
COPY . /var/www/html

# Exposer le port de développement
EXPOSE 8000

# Commande par défaut : tenter composer install puis lancer le serveur PHP intégré
CMD ["sh", "-c", "export COMPOSER_ALLOW_SUPERUSER=1; composer install --no-interaction --prefer-dist || true; php -S 0.0.0.0:8000 -t public"]
