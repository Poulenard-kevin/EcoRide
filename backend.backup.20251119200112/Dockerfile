FROM php:8.2-cli

WORKDIR /var/www/html

# Installer dépendances système et extensions PHP utiles (pdo_mysql, zip, intl...)
RUN apt-get update && apt-get install -y \
    git unzip libzip-dev libicu-dev zlib1g-dev libonig-dev \
  && docker-php-ext-install pdo_mysql intl zip \
  && rm -rf /var/lib/apt/lists/*

# Récupérer composer depuis l'image officielle Composer
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

# Exposer le port de développement
EXPOSE 8000

# Commande par défaut : installer les dépendances et lancer le serveur PHP intégré (dev)
CMD ["sh", "-c", "composer install --no-interaction --prefer-dist || true && php -S 0.0.0.0:8000 -t public"]
