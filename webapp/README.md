# Projet : MadCoffee

## Mise en place de site web Wordpress

**Résponsable**
- Idris BOUZIDI
- Benoit JACQUET

### Description

Ce projet permet de déployer une instance WordPress pour MadCoffee en utilisant Docker et Docker Compose. Il comprend deux répertoires principaux :

-   **`siem`** : Contient la configuration et le déploiement pour les outils de surveillance.
-   **`webapp`** : Contient la configuration et le déploiement pour l'instance WordPress.

### Structure du Projet

**Racine du projet :**
~~~~
├── siem
│   ├── config
│   │   ├── grafana-datasources.yml
│   │   ├── loki.yaml
│   │   └── promtail.yaml
│   └── docker-compose.yaml
└── webapp
    ├── config
    │   └── promtail.yaml
    ├── docker-compose.yaml
    ├── nginx
    │   ├── default.conf
    │   └── Dockerfile
    └── README.md` 
~~~~
### Démarrage

Ajoutez la ligne suivante au fichier `hosts` de la machine hôte pour la redirection :

-   `2a03:5840:111:1024:58:87ff:fe9b:1d95 wordpress.local`

Accédez au site WordPress via : [wordpress.local](http://wordpress.local/)

Connectez-vous avec :

-   **Utilisateur** : `user0`
-   **Mot de passe** : `P@ssw0rd`

### Contenu des Répertoires

-   **`siem`** :
    
    -   `config/grafana-datasources.yml` : Configuration des sources de données pour Grafana.
    -   `config/loki.yaml` : Configuration de Loki pour la collecte des logs.
    -   `config/promtail.yaml` : Configuration de Promtail pour l'envoi des logs à Loki.
    -   `docker-compose.yaml` : Configuration Docker Compose pour le déploiement des outils de surveillance.
-   **`webapp`** :
    
    -   `config/promtail.yaml` : Configuration de Promtail pour l'envoi des logs à Loki.
    -   `docker-compose.yaml` : Configuration Docker Compose pour le déploiement de l'instance WordPress.
    -   `nginx/default.conf` : Configuration du serveur web Nginx.
    -   `nginx/Dockerfile` : Dockerfile pour la construction de l'image Nginx.

### Commandes Docker

**Déploiement :**

-   `docker ps -a` : Liste tous les conteneurs Docker.
-   `docker compose up -d` : Démarre les conteneurs Docker.
-   `docker compose down -v` : Arrête les conteneurs Docker et supprime les volumes associés.
-   `docker image prune -a` : Supprime toutes les images Docker inutilisées (y compris les images intermédiaires).
-   `docker volume prune` : Supprime tous les volumes Docker inutilisés.

**Commandes auxiliaires :**

-   `docker rmi $(docker images -f "dangling=true" -q)` : Supprime toutes les images Docker intermédiaires ("dangling images").
-   `docker system prune` : Supprime tous les objets Docker inutilisés.
