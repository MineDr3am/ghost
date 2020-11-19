# Blog Ghost + Nginx + Let's Encrypt seulement sur Docker

Il s'agit d'un projet permettant de déployer un blog Ghost tournant grace au proxy nginx et permettant l'automatisation de certificats, le tout tournant sur Docker.
Résultat est présent sur _https://hugolausenazpire.fr_
**Un grand merci à [Fred](https://github.com/FredPi17/blog-ghost) pour son aide sur ce projet**

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
2. Modifier le fichier docker-compose.yml avec ses informations personnelles:
```
vim docker-compose.yml
```
