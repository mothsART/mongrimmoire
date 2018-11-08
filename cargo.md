# Cargo

vendor : rasembler l'ensemble des librairies à un moment x et les mettre pré-compilés dans un sous-dossier
    cargo vendor debian/vendor
    cd debian && tar zcf vendor.tar.gz vendor && rm -Rf vendor && cd ..

Graphe :
    cargo graph
