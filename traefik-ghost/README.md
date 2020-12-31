
## Installation avec Traefik
1. Cloner le projet:
```
git clone https://github.com/MineDr3am/ghost.git
```
Aller dans le dossier:
```
cd ghost/traefik-ghost
```

2. Modifier les fichiers avec ses informations personnelles
```
vim .env
```
```
MYSQLUSER=YOUR_MYSQL_USER
MYSQLPASSWORD=YOUR_MYSQL_PASSWORD
MYSQLDB=YOUR_MYSQL_DATABASE
```
Changer les informations personnelles dans les fichiers config.production.json et traefik.yml:
```
vim conf/config.production.json
```
```
"url": "https://YOUR_DOMAIN",
```
```
vim conf/traefik.yml
```
```
email: YOUR_EMAIL
```
3. Donner des droits spécifiques au dossier acme.json:
```
chmod 600 conf/acme.json
```
4. Prendre en compte le fichier .env:
```
source .env
```
5. Exécuter les containers:
```
docker-compose up -d
```
