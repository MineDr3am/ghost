# Ghost tournant en container Docker avec Nginx ou Traefik

Il s'agit d'un projet permettant de déployer un blog Ghost tournant grâce au proxy nginx et permettant l'automatisation de certificats, le tout tournant sur Docker.
Résultat est présent sur _https://hugolausenazpire.fr_
**Un grand merci à @FredPi17 pour son aide sur ce projet**

## Nouvelles fonctionnalitées
- Ajout du container Let's Encrypt permettant le TLS et donc du https
- Les données sont maintenant persistantes avec un container Mariadb
- Ajout du choix de proxy, soit Nginx soit Traefik

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
Modifier les informations dans le docker-compose.yml:
```
traefik.http.routers.ghost-https.rule: Host(`YOUR_DOMAIN`)
...
url: http://YOUR_DOMAIN

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

## Installation avec Nginx
1. Cloner le projet:
```
git clone https://github.com/MineDr3am/ghost.git
```
Aller dans le dossier:
```
cd ghost/nginx-ghost
```
2. Modifier le fichier d'environnements .env avec ses informations personnelles:
```
vim .env
```
```
DOMAIN_NAME=YOUR_DOMAIN
EMAIL=YOUR_PROJECT
```
3. Prendre en compte le fichier d'environnement en faisant:
```
source .env
```
4. Lancer la commande pour exécuter les containers:
```
docker-compose up -d
```

## TODO list
- [x] Faire le TLS
- [X] Rendre les données persistantes avec MySQL
- [x] Centraliser les variables d'environnements
- [x] Le lancer avec Traefik
- [x] Centraliser nginx et traefik
