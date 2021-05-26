# Design Patterns par la pratique

# Objectif

Nous voulons simuler le pilotage d’un portail. Pour cela nous allons exploiter des "Design Patterns".

Dans notre système nous avons :

* un portail ;
* un rail où est posé le portail ;
* un moteur ;
* une télécommande avec 1 bouton ;
* une ampoule ;
* deux capteurs ;
* une console.

# Règles de fonctionnement

## Les objets

* Le portail peut être déplacé vers la gauche ou la droite. Pour cela il faut utiliser la
  commande `Deplace(VersLaGauche)`. Si le paramètre `VersLaGauche` est à `vrai`, le déplacement est vers la gauche sinon
  vers la droite.
* Le rail est un élément statique qui permet de définir la position du portail.
* Le moteur
    * peut tourner vers la gauche ou vers la droite ;
    * il permet de faire déplacer le portail ;
    * il est commandé par une télécommande ;
    * il utilise 2 capteurs pour déterminer si le portail est à gauche ou à droite ;
    * il signale qu'il est en fonctionnement en allumant une ampoule.
* La télécommande envoie un signal au moteur lorsque le bouton est utilisé.
* L'ampoule peut être allumée ou éteinte avec la commande `Interrupteur(Bool On)`. Quand le paramètre `on` est à `vrai`
  alors la lampe est allumée, sinon elle est éteinte. Lorsque l'ampoule est allumée elle clignote toutes les 2 secondes.
* Un capteur indique si le portail est à son niveau. Il y en a un à chaque extrémité du rail pour délimiter la 
  le parcours du portail. 
* La console permet d'afficher des messages de maintenance. 

## Fonctionnement

* Au démarrage le moteur est à l'arrêt. Le portail est positionné au centre du rail, entre les deux capteuts.  
* L'utilisation du bouton provoque une commande dans le cycle ci-après :
    * démarrage du moteur vers la gauche [&#10559;] ;
    * arrêt du moteur [&#x26D4;] ;
    * démarrage vers la droite [&#10558;] ;
    * arrêt du moteur [&#x26D4;].
* L'ampoule doit être allumée lorsque le moteur fonctionne.
* Le programme du moteur doit assurer que le portail ne sorte pas de la zone définie par les capteurs.
