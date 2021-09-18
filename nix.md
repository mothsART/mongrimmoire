Title: Nix
Category: misc
Tags: nix
Date: 2015-12-11 00:00
Modified: 2015-12-11 00:00
Slug: 3D
Authors: Jérémie Ferry
Status: published
Summary:

## Installation

https://nixos.wiki/wiki/Nix_Installation_Guide

curl https://nixos.org/nix/install | sh
echo ". $HOME/.nix-profile/etc/profile.d/nix.sh" >> ~/.bashrc
source ~/.bashrc

echo 'export XDG_DATA_DIRS=$HOME/.nix-profile/share:$HOME/.share:$XDG_DATA_DIRS' >> /etc/profile.d/nix.sh

## Soucis d'installation

unset NIX_REMOTE NIX_PATH

## Liens

===== Installer et utiliser un paquet =====

https://doc.ubuntu-fr.org/nix
https://nixos.org/nixos/packages.html

https://nokomprendo.gitlab.io/posts/tuto_fonctionnel_43/2019-12-23-fr-README.html
https://nokomprendo.gitlab.io/posts/nix_developpeurs/2017-07-06-README.html
https://linuxfr.org/news/nix-pour-les-developpeurs
https://www.blog-libre.org/2018/06/15/nix-ou-la-gestion-des-paquets-en-question/
https://www.lancelotsix.com/posts/2015-03-29-bookmark_nix.html

https://static.domenkozar.com/nixpkgs-manual-sphinx-exp/coding-conventions.xml.html
https://nixcloud.io/tour/?id=1

## Utilitaire

https://github.com/bennofs/nix-index

## paquets installés

lister les paquets installés : nix-env -q

nix-env -i gimp


nix run nixpkgs.gimp -c gimp
nix run nixpkgs.geany -c geany
nix run nixpkgs.inkscape -c inkscape
nix run nixpkgs.broot -c broot
nix run nixpkgs.zola -c zola
nix run nixpkgs.htop -c htop
nix run nixpkgs.sd -c sd // equivalent to sed
nix run nixpkgs.terminator -c terminator

nix-env -iA nixpkgs.guake
nix-env -iA nixpkgs.cypress
nix-env -iA nixpkgs.pidgin
nix-env -iA nixpkgs.flameshot
nix-env -iA nixpkgs.thefuck
nix-env -iA nixpkgs.zola
nix-env -iA nixpkgs.gitAndTools.delta
nix-env -iA nixpkgs.vscode
nix run nixpkgs.youtube-dl -c youtube-dl
nix-env -iA nixpkgs.ripgrep-all

nix-env -iA nixpkgs.atom (marche pas)
nix-env -iA nixpkgs.cypress (marche pas)
nix-env -iA nixpkgs.gcompris (marche pas)


nix run nixpkgs.speedtest-cli -c speedtest

## A tester

firejail # voir https://linuxfr.org/users/psychofox/journaux/podbox-sandboxing-d-applis-avec-podman
wormhole : pas encore intégré

fzf
keychain
ncdu
peco
ranger
ripgrep
vagrant
zsh
virtualbox
bleachbit

youtube-dl (mvp)


Lollypop
strawberry (remplacant de clementine)

blender

## utilisation de NUR

Recherche : https://nix-community.github.io/nur-search/

https://github.com/nix-community/NUR
nix-shell -p nur.repos.mic92.inxi

## Doc ubuntu

https://doc.ubuntu-fr.org/nix

## Voir la liste des paquets installés avec Nix

```sh
nix-env -qa
```

## MAJ du channel

```sh
nix-channel --update && nix-env -u --always
```

## MAJ de ses paquets :

```sh
nix-env -iA nixpkgs.nix
```

nix run nixpkgs.python27Packages.glances -c glance

## Vider les anciens paquets

```sh
nix-collect-garbage -d
```

## Réparer les paquets corrompus

```sh
nix-store --verify --check-contents --repair
nix-store --gc
```

## Supprimer un paquet

nix-env -e guake

## obtenir le sha256 pour le fetchFromGithub

nix-prefetch-url --unpack https://github.com/mothsART/gspeech/archive/0.10.1.tar.gz

nix-prefetch-url --unpack https://github.com/mothsART/fluxboxlauncher/archive/20955f96062a1ff9a8772121925fc67f7f4a59d4.tar.gz
nix-prefetch-url --unpack https://github.com/mothsART/fluxboxlauncher/archive/0.2.1.tar.gz

nix-prefetch-url --unpack https://github.com/maoschanz/drawing/archive/0.4.11.tar.gz

## Participer à Nix

(15:07:30) symphorien: cloner nixpkgs
(15:07:33) symphorien: cd nixpkgs
(15:07:42) symphorien: nix edit -f. guake
(15:07:47) symphorien: nix-build -A guake
(15:07:53) symphorien: ./result/bin/guake

nix build -I nixpkgs=./ nixpkgs.gspeech

## Avantages et inconvénients

+ installation des derniers paquets
+ le moteur de recherche est bien pensé mais il manque des options : fitrage par version, par langage

- plein de paquets non traduits : gimp, geany

- créer un paquet peut s'avérer être un parcours du combatant : on recherche un paquet qui a déjà eu la même problématique et on recopie.

- l'installation de certains programmes reposent sur les systèmes d'installation des langages : softs python s'appui sur pip, setup.py etc.
