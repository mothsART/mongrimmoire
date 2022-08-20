#APT

Recherche et installation de paquets :

    sudo apt search [paquet](rechercher un paquet)
    sudo apt install [paquet](installer un paquet)
    sudo apt install -f (permet de régler des éventuels problèmes de dépendances manquantes avec dpkg)

Mises à jour :

    sudo apt update (rechercher les mises à jour)
    sudo apt ugrade (installer les mises à jour)
    apt list --upgradable (Affichez les paquets pour lesquels une mise à jour est disponible)
    sudo apt full-upgrade (supprimer/installer et mettre à jour les paquets)
    sudo apt dist-upgrade (effectue la fonction upgrade en améliorant la gestion des dépendances pour les nouvelles versions de paquets)

Suppression de paquets et nettoyage :

    sudo apt remove [paquet] --purge (désinstaller un paquet et purger ses fichiers de configuration)
    sudo apt autoremove [paquet] (désinstaller un paquet et les dépendances inutilisées) (peut être associé à --purge)
    sudo apt autoclean (supprime les paquets périmés dans le cache apt)

Informations paquets et dépendances :

    sudo apt -l (lister les paquets installés) (>> fichier.txt peut rediriger le résultat dans un fichier)
    apt --version (afficher la version d'apt)
    sudo apt show [paquet] (afficher les détails d'un paquet)
    sudo apt depends [paquet] (lister les dépendances d'un paquet) 

Gestion des sources :

    sudo apt edit-sources (permet de modifier les sources .list)

Figer une version précise :

    sudo apt-mark hold Firefox

Aide :

    man apt (afficher le manuel d'apt)
    apt --help (afficher l'aide d'apt)
