# Objectifs: 
Concevoir un fichier html unique, permettant la gestion de tournoi UNSS en futsal 
# Description des besoins de l’application : 
* Un onglet pour futsal et un onglet pour futsal féminin
* choix de la catégorie : benjamins/minimes qui donnera lieu à un sous onglet que ceoist pour futsal ou futsal féminin
* Choix des établissements avec liste déroulante parmi : 
   - Joliot Curie
   - Lamartine
   - Chabroux
   - Jaurès
   - Bertrand Tavernier
   - Monod
   - Rosset
* Pour chaque établissement, je veux pouvoir choisir le nombre d'équipes engagées en : 
   - benjamins ou benjamines suivant si futsal ou futsal féminin
   - Minimes G ou Minimes F suivant si futsal ou futsal féminin
* Je veux pouvoir créer plusieurs tournois avec continuité des résultats.
* Je veux pouvoir aussi supprimer le tournoi
* Je veux pouvoir renommer un tournoi existant

# Comportement
* Je veux pouvoir choisir le nombre de poules (1 à 6 poules)
* Si plusieurs poules, je veux pouvoir choisir qui est dans quelle poule
* je veux que cela m'organise les matchs pour que tout le monde se rencontre dans une poule
* si choix de deux poules : 
    - je veux que cela m'organise les matchs de poule
    - les demis finales / finales
          - avec le premier de la poule 1 contre le 2ème de la poule 2
          - avec le premier de la poule 2 contre le 2ème de la poule 1
          - finale entre les 2 vainqueurs
          - match de classement entre les 2 perdants (case à cocher pour savoir is ces matchs là se feront)
          - MAtch de classement de dernier de chaque poule qui s'affronte
          - Match de classement des 3ème de chaque poule qui s'affrontent (si poule de 4)
* Je veux pouvoir choisir la durée du match avec un chrono (lisible et grand) qui puisse être déclenché et qui soit topujours visible
* je veux que dans les équipes qui ne jouent pas, une équipe soit nommée à l'arbitrage
* Je veux que pour chaque match joué, un tableau de bord s'affiche pour le match où je puisse enregistrer les buts marqués par chaque équipe, par un clic sur le nom de l'équipe avec le chrono du match
* Je veux un classement qui s'actualise à chaque rencontre : 
     - Victoire = 4 points
     - Match nul = 2 points
     - Défaite = 1 point
* Dans établissements et équipes engagées, 
     - je veux que le clic passe automatiquement à la ligne suivante 
     - je veux que par défault, la cellule soit vide
* Configuration des matchs :
     - indiquer le nombre d'équipes présentes en fonction des équipes inscrites pour chaque établissement
     - Choix du nombre de poule
     - répartition des équipes par poule (soit manuellement, soit par un bouton réaprtir automatiquement)
     - choix de la durée des matchs (si plusieurs poules, choix de durée par poule) :indiquer le temps total nécessaire pour faire l'ensemble des matchs alors
     - Si plusieurs popules, choix de faire amtch en aller retour ou pas
     - choix du mode de phase finale : demi-finales croisées  avec finale ou même rang (1er contre 1er, 2e contre 2e, etc...)
     - Bouton générer les matchs
# Design
* Le titre de la page s'appelle : UNSS Gestion tournoi futsal
* Je veux que tous les tableaux aient des colonnes de couleurs différentes (sauf du vert, du marron)
* Je veux un design clair, moderne et attractif et orienté sport
* Je veux que ce soit utilisable sur un écran d'ordinateur, ou un ipad
* Je veux que la mise en page s'adapte à une tablette pour que l'ensemble des informations soit visible d'un écran de tablette
* Je veux une présentation où davantage d'information soit lisible sur l'écran, soit avoir besoin à scroller
* Je veux que les colonnes soient optimisées, que la largeur de la colonne s'adapte au nom le plus long

# Synchronisation multi-appareils
* Je veux accéder à l'application depuis la tablette ou l'ordinateur avec toujours les données les plus à jour
* Les données sont stockées localement (navigateur) et sauvegardées dans un Google Sheet partagé via une application Web Google Apps Script
* À l'ouverture de l'application, elle récupère automatiquement les dernières données disponibles en ligne si elles sont plus récentes que les données locales
* À chaque modification, les données sont automatiquement envoyées vers le Google Sheet (après un court délai pour regrouper les modifications rapprochées)
* Un indicateur dans l'en-tête affiche l'état de la synchronisation (synchronisé / en cours / hors ligne / non configuré)
* Un bouton permet de forcer une synchronisation manuelle à tout moment
* En cas de perte de connexion, l'application continue de fonctionner avec les données locales et se resynchronise automatiquement dès que la connexion revient (prochaine ouverture ou synchronisation manuelle)
* En cas de conflit (modifications sur deux appareils), la version la plus récente (horodatage) est conservée
* Je veux pouvoir utiliser le tournoi hors connexion (pas de wifi/4G disponible au gymnase) : une fois l'application ouverte au moins une fois avec une connexion, elle doit continuer à s'ouvrir et fonctionner normalement sans connexion internet