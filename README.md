# projet2024-docker

[![Docker Pulls](https://img.shields.io/docker/pulls/abesesr/projet2024.svg)](https://hub.docker.com/r/abesesr/projet2024/)

Configuration docker 🐳 pour déployer le site web https://projet2024.abes.fr  
Le code source et le contenu du site est disponible ici : https://github.com/abes-esr/projet2024

## URLs

Les URLs correspondantes aux déploiements en local, dev, test et prod sont les suivantes :

- local :
  - http://127.0.0.1:16080/
  - http://127.0.0.1:3000/ (c'est l'URL par défaut lorsque l'on démarre docusaurus en mode développement)
- dev (branche develop du [code source](https://github.com/abes-esr/projet2024)):
  - https://projet2024-dev.abes.fr
  - http://diplotaxis2-dev.v212.abes.fr:16080/
- test (branche main du [code source](https://github.com/abes-esr/projet2024))
  - https://projet2024-test.abes.fr
  - http://diplotaxis2-test.v202.abes.fr:16080/
- prod (dernier tag/version git du [code source](https://github.com/abes-esr/projet2024))
  - https://projet2024.abes.fr
  - http://diplotaxis1-prod.v102.abes.fr:16080/

## Prérequis

Disposer de :
- ``docker``
- ``docker-compose``

## Installation

Déployer la configuration docker dans un répertoire :
```bash
# adaptez /opt/pod/ avec l'emplacement où vous souhaitez déployer l'application
cd /opt/pod/
git clone https://github.com/abes-esr/projet2024-docker.git
```

Configurer l'application depuis l'exemple du [fichier ``.env-dist``](./.env-dist) (ce fichier contient la liste des variables avec des explications et des exemples de valeurs) :
```bash
cd /opt/pod/projet2024-docker/
cp .env-dist .env
# personnaliser alors le contenu du .env
```

Démarrer l'application :
```bash
cd /opt/pod/projet2024-docker/
docker-compose up -d
```

## Démarrage et arrêt

```bash
# pour démarrer l'application (ou pour appliquer des modifications 
# faites dans /opt/pod/projet2024-docker/.env)
cd /opt/pod/projet2024-docker/
docker-compose up -d
```

Remarque : retirer le ``-d`` pour voir passer les logs dans le terminal et utiliser alors CTRL+C pour stopper l'application

```bash
# pour stopper l'application
cd /opt/pod/projet2024-docker/
docker-compose stop


# pour redémarrer l'application
cd /opt/pod/projet2024-docker/
docker-compose restart
```

## Supervision

```bash
# pour visualiser les logs de l'appli
cd /opt/pod/projet2024-docker/
docker-compose logs -f --tail=100
```

Cela va afficher les 100 dernière lignes de logs générées par l'application et toutes les suivantes jusqu'au CTRL+C qui stoppera l'affichage temps réel des logs.


## Configuration

Pour configurer l'application, vous devez créer et personnaliser un fichier ``/opt/pod/projet2024-docker/.env`` (cf section [Installation](#installation)). Les paramètres à placer dans ce fichier ``.env`` et des exemples de valeurs sont indiqués dans le fichier [``.env-dist``](https://github.com/abes-esr/projet2024-docker/blob/develop/.env-dist)

## Sauvegardes

Les éléments suivants sont à sauvegarder:
- ``/opt/pod/projet2024-docker/.env`` : contient la configuration spécifique de notre déploiement

### Restauration depuis une sauvegarde

Réinstallez l'application projet2024 depuis la [procédure d'installation ci-dessus](#installation) et récupéré depuis les sauvegardes le fichier ``.env`` et placez le dans ``/opt/pod/projet2024-docker/.env`` sur la machine qui doit faire repartir projet2024.

