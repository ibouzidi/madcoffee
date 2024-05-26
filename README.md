# Projet : MadCoffee

## Mise en place de site web Wordpress

**Résponsable**
- Idris BOUZIDI
- Benoit JACQUET

### Déscription

Ce projet permet de déployer une instance WordPress pour MadCoffee avec Docker et Docker Compose. Il comprend trois conteneurs :

- `db` : conteneur MySQL pour la base de données WordPress.
- `wordpress` : conteneur WordPress avec PHP 8.0 FPM et Alpine Linux.
- `nginx` : conteneur Nginx pour le serveur web.

### Démarrage

Ajout d'une nouvelle ligne sur le fichier `host` de la machine hôte pour une redirection : 

- `2a03:5840:111:1024:58:87ff:fe9b:1d95 wordpress.local`

- Accès au site wordpress : [wordpress.local](http://wordpress.local/)

**Structure:**
~~~
root@wordpress:~/madcoffee# tree
.
├── docker-compose.yml
├── nginx
│   └── default.conf
└── README.md
~~~

-   `docker-compose.yml`  : fichier de configuration pour le déploiement de l'instance WordPress pour MadCoffee avec Docker et Docker Compose.
-   `nginx/default.conf`  : fichier de configuration pour le serveur web Nginx.
- `.env` (caché) : contient les informations d'authentification de la base de données MySQL et du site Wordpress.
-   `README.md`  : fichier de documentation pour le projet, contenant des informations sur le déploiement de l'instance WordPress pour MadCoffee avec Docker et Docker Compose.

### Commandes Docker

**Déploiement:**

-   `docker ps -a`  : Liste tous les conteneurs Docker
-   `docker compose up -d`  : démarre les conteneurs Docker
-   `docker compose down -v`  : arrête les conteneurs Docker et supprime les volumes associés.
-   `docker image prune -a`  : supprime toutes les images Docker inutilisées (y compris les images intermédiaires).
-   `docker volume prune`  : supprime tous les volumes Docker inutilisés.

**Commande auxiliaire :**
-   `docker rmi $(docker images -f "dangling=true" -q)`  : supprime toutes les images Docker intermédiaires (aussi appelées "dangling images"). La commande  `docker images -f "dangling=true" -q`  récupère les ID d'images intermédiaires, qui sont ensuite passés en tant qu'arguments à la commande  `docker rmi`.
- `docker system prune` : Supprime tous les objets sur docker.
