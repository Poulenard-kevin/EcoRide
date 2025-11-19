# EcoRide - Submission

## Démarrage rapide

1. Cloner ce dépôt :
   git clone https://github.com/TON_UTILISATEUR/EcoRide_Submission.git
   cd EcoRide_Submission

2. Lancer les services Docker :
   docker compose -f ecoride-docker/docker-compose.yml up -d

3. Accès :
   - Frontend : http://localhost:3000
   - Backend : http://127.0.0.1:8000
   - phpMyAdmin : http://localhost:8082

4. Import SQL (si nécessaire) : via phpMyAdmin importer le fichier `sql/ecf_dump_sf_EcoRide_with_users.sql`.

### Identifiants de test
- user@example.com / password
- admin@example.com / password
