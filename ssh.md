# Générez la clé ssh

ssh-keygen -t rsa -b 4096

# Recopiez votre clé publique :

sudo apt-get install xclip
xclip -sel clip < ~/.ssh/id_rsa.pub

# Ouvrez votre navigateur et allez dans les paramètres de votre compte. Sélectionnez Settings / SSH GPG Keys.

# Entrez une nouvelle clé en appuyant sur le bouton [New SSH key] dans la partie key

# Chargez votre clé dans l’agent ssh :

ssh-add ~/.ssh/id_rsa
