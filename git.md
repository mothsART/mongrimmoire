# GIT

Suppression de l'index

    git checkout -- unfichier
    git checkout -f // tous les fichiers

Changer des droits sur des fichiers

    git update-index --chmod=+x <file>

Commit vide

    git commit --allow-empty

Clone Avec des sous-modules

    git clone --recursive depot

Ajout/Reset Partiel

    git add -p/git reset -p


Ajout

    git tag montag 1b2e1d63ff (numéro du commit)
    git tag montag mon_nom_de_branch
    git tag montag (ajout du tag sur le commit pointé par le **Head**)
    git push --tags (envoi des commits en remote + les tags)


Suppression

    git tag -d mon_tag
    git push origin :refs/tags/mon_tag #supprime en remote


Reflog

Reflog permet de lister toutes les actions faites sur un dépôt.
A la différence de **git log**, il va lister également les actions de suppression qui ne sont plus présente sur notre historique GIT.
Cette commande est très utile pour récupérer des commits/tags/branches qui ont été supprimé ou pour revenir sur un historique précédent !


Cherry-pick + cherry

**git cherry** permet de lister la différence entre 2 branches

Donne la liste des commits de différence entre les 2 branches

    git cherry branch1 branch2

Log

    git log -n 10 # n'afficher que les 10 derniers commits

Shortlog

    git shortlog -sne --all
    git shortlog -sne --all | wc -l => liste les autheurs sur l'ensemble des dépôts

Remote

On supprime de notre **repository local** toutes les branches remote qui n'existent plus

    git remote prune origin

On compte toutes les branches **remote mergées**

    git branch -r --merged origin/integration | wc -l


Ignore

exclusion globale (dans ~/.gitconfig):
[core]
    excludesfile = ~/.gitignore

exclusion locale : .git/info/exclude

Ignorer un fichier déjà tracké :
git update-index --assume-unchanged <file>
(en savoir + : https://www.kernel.org/pub/software/scm/git/docs/git-update-index.html)
(opération inverse : git update-index --no-assume-unchanged <file>)

    #!bash
    git update-index --no-assume-unchanged 

Cherry

Considérons 2 branches => **master** et **topic**

    #!bash
    git cherry -v topic | grep -e "^+" | grep -v "\[nc\]" | tee /dev/tty | wc -l

donne la liste des commits présent dans la **topic** et non dans la **master**

et son inverse :

    git cherry -v master | grep -e "^+" | grep -v "\[nc\]" | tee /dev/tty | wc -l

donne la liste des commits présent dans la **master** et non dans la **topic**

Diff

    git diff -b (git diff --ignore-space-change)
    git diff -w (git diff --ignore-all-space)
    git diff --color-words=.


juste les fichiers : git diff --stat
git diff --name-status

Amend

    #!bash
    git commit --amend --no-edit

Rajoute au dernier commit tous les fichiers du staging + tous les fichiers non traqués et renome l'intitulé du commit

    #!bash
    git commit -a -u --amend -m "new message"

Stash

    git stash --include-untracked === git stash save -u

réapplique le stash avec l'index originel :

    #!bash
    git stash apply --index

Explication : http://www.git-attitude.fr/2014/09/15/30-options-git-qui-gagnent-a-etre-connues/#stasher-plus efficacement avec save et -u

    git stash save -u 'Nom du stash'
    git stash pop --index

Push

Pousser une branche qui vient d'être créé :

    git push -u origin NomDeLaNouvelleBranche

Suppression d'un commit en remote : http://stackoverflow.com/questions/1338728/delete-commits-from-a-branch-in-git

En local

    git reset --hard HEAD~1

En remote

    git push origin HEAD --force


Sous modules

    J'oubli à chaque fois l'ordre pour mettre à jour un sous-module.
    Mon exemple pour mon plugin **Ace Editor** :

        git clone --recursive https://github.com/mothsART/pelican-plugins.git
        cd ace_editor
        git checkout master
        git pull
        cd ..
        git add -A
        git c -m "..."
        git push

Suppression Branche remote

    git push origin --delete <branchName> (exemple: git push origin --delete 14_79_000_0)
    (ancienne méthode (git < 1.7): git push origin :<branchName>)nch 

Suppression Commit en remote

supprime le dernier commit : git push -f origin HEAD^:ma_Branch_en_remote

Suppression répertoire de travail

    git reset HEAD === git reset HEAD^0

