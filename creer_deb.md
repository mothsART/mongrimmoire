# Créer des paquets Debian

Créer un .deb source :

    dpkg-buildpackage -S -us -uc

Créer un .deb :

    dpkg-buildpackage -us -uc

Créer un .deb source pour Rust :

    cargo vendor debian/vendor
    cd debian && tar zcf vendor.tar.gz vendor && rm -Rf vendor && cd ..
    dpkg-buildpackage -S -us -uc
    cd ..
    debsign monfichier.changes
    dput ppa:monpppa monfichier.changes

Créer un .deb pour Rust :

    cargo vendor debian/vendor
    cd debian && tar zcf vendor.tar.gz vendor && rm -Rf vendor && cd ..
    dpkg-buildpackage -us -uc
