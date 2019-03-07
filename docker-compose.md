#Docker-compose

Démarre les services décrits dans mon docker-compose.yml et ne me rend pas la main :
    docker-compose up

Fait la même chose mais me rend la main une fois que les services sont démarrés :
    docker-compose up -d

Reconstruit les services avant de les lancer :
    docker-compose up –build

Stoppe les services :
    docker-compose down

Redémarre l’ensemble des services :
    docker-compose restart

Redémarre un des services (ici nginx) :
    docker-compose restart nginx

Me fournit une console bash au sein du conteneur rails :
    docker-compose exec rails bash

Effectue un rails db:migrate au sein du conteneur rails :
    docker-compose exec rails bin/rails db:migrate

Me retourne l’ensemble des logs des services depuis le dernier démarrage et me rend la main :
    docker-compose logs

Affiche les logs des services et continue à les « écouter » sans me rendre la main :
    docker-compose logs -f

Fait la même chose pour le conteneur rails uniquement :
    docker-compose logs -f rails
