# Blog Ghost + Nginx + Let's Encrypt seulement sur Docker

Il s'agit d'un projet permettant de déployer un blog Ghost tournant grace au proxy nginx et permettant l'automatisation de certificats, le tout tournant sur Docker.
Résultat est présent sur _https://hugolausenazpire.fr_
**Un grand merci à [Fred](https://github.com/FredPi17) pour son aide sur ce projet**

## Nouvelles fonctionnalitées
- Ajout du container Let's Encrypt permettant le TLS et donc du https

## Installation
1. Cloner le projet:
```
git clone https://github.com/MineDr3am/ghost.git
```
Aller dans le dossier:
```
cd ghost
```
2. Modifier le fichier d'environnements .env avec ses informations personnelles:
```
vim .env
```
```
#Dans ghost
      url: {YOUR_URL}
      VIRTUAL_HOST: {YOUR_URL}
      LETSENCRYPT_HOST: {YOUR_URL}
      LETSENCRYPT_EMAIL: {YOUR_EMAIL}
```
```
  DEFAULT_EMAIL: {YOUR_EMAIL}
```
3. Modifier le fichier nginx.conf présent dans le dossier nginx:
```
vim /nginx/nginx.conf
```

```
server {

  listen 80;
  server_name {YOUR_URL};
```
```
  location / {
    return 301 https://{DOMAIN_NAME};
  }
```
```
  server_name {DOMAIN_NAME};
  ssl_certificate /etc/letsencrypt/live/{DOMAIN_NAME}/fullchain.pem;
  ssl_certificate_key /etc/letsencrypt/live/{DOMAIN_NAME}/privkey.pem;
  location / {
      proxy_pass http://ghost:2368/;
      proxy_set_header Host "{DOMAIN_NAME}";
      proxy_set_header    Host                "{DOMAIN_NAME}";
      proxy_set_header    X-Real-IP           "$remote_addr";
      proxy_set_header X-Forwarded-Proto https;
      proxy_set_header    X-Forwarded-For     "$proxy_add_x_forwarded_for";
}
```
4. Lancer la commande pour exécuter les containers:
```
docker-compose up -d
```

## TODO list
- [x] Faire le TLS
- [ ] Rendre les données persistantes avec MySQL
- [ ] Centraliser les variables d'environnements
