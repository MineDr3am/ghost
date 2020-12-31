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
