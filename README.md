# Projet : MadCoffee

## Mise en place de site web WordPress et de la plateforme de surveillance SIEM

**Responsables**
- Idris BOUZIDI
- Benoit JACQUET

### Description

Ce projet permet de déployer une instance WordPress pour MadCoffee ainsi qu'une plateforme de surveillance SIEM en utilisant Docker et Docker Compose. Le projet est divisé en deux parties principales :

- **`webapp`** : Contient la configuration et le déploiement de l'instance WordPress.
- **`siem`** : Contient la configuration et le déploiement des outils de surveillance (Grafana, Prometheus, Loki, etc.).

### Services et Ports 
| Machine | Service | Port | SSL | Domaine | 
| --- | --- | --- | --- | --- | 
| SIEM | Grafana | 3000 | Non | grafana.alderson.projet.filiere.info | 
| SIEM | Loki | 3100 | Non | N/A | 
| SIEM | Promtail | 9080 | Non | N/A | 
| SIEM | Prometheus | 9090 | Non | N/A | 
| SIEM | Alertmanager | 9093 | Non | N/A | 
| SIEM | Node-Exporter | 9100 | Non | N/A | 
| SIEM | cAdvisor | 8080 | Non | N/A | 
| WebApp | WordPress | 9000 | Oui | madcoffee.alderson.projet.filiere.info | 
| WebApp | Nginx (SSL) | 443 | Oui | madcoffee.alderson.projet.filiere.info | 
| WebApp | Nginx (HTTP) | 80 | Non | madcoffee.alderson.projet.filiere.info | 

### Démarrage

Ajoutez les lignes suivantes au fichier `hosts` de la machine hôte pour la redirection :

-   `2a03:5840:111:1024:58:87ff:fe9b:1d95 madcoffee.alderson.projet.filiere.info`
-   `2a03:5840:111:1024:9b:eff:feae:a039 grafana.alderson.projet.filiere.info`

Accédez aux services via les domaines configurés :

-   **WordPress** : [https://madcoffee.alderson.projet.filiere.info](https://madcoffee.alderson.projet.filiere.info)
-   **Grafana** : [https://grafana.alderson.projet.filiere.info](https://grafana.alderson.projet.filiere.info)

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
