# Commandes d'admin sys

Exa (en remplaçant de ls => alias ls=exa) :
    exa --long --header --git

Fd (en remplaçant de find) :
   fd jpeg$

RipGrep (remplaçant de grep) :
    rg -L -u -tc -n -w '[A-Z]+_SUSPEND'

Serveur Http (alias httpserver=Basic-http-server)
    httpserver --addr 127.0.0.1:1234

Bat (remplaçant de cat => alias cat=bat) :
    cat adminsys.md

Hyperfine (remplaçant de time) :
    hyperfine svgcleaner organes.svg organes.svgcleaner.svg
