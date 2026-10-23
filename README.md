# Jeu de l'oie - atelier IA générative

Pour jouer : ouvrir `jeu_de_l_oie_modulaire_le_jardin_des_oies.html` dans un navigateur.

## Fonctionnalités attendues

- Choisir le nombre d'équipes (entre 2 et 10) et leur donner un nom
- Chaque équipe a un pion d'une couleur différente
- Bouton pour lancer la partie
- Afficher le plateau de 63 cases avec la position des pions et leurs déplacements
- Lancer les dés à tour de rôle, afficher à qui c'est le tour
- Il faut tomber pile sur la case 63 pour gagner, sinon on recule du surplus
- Des cases spéciales avec des actions (avancer, reculer, rejouer, passer son tour...)
- Des cartes Chance piochées sur certaines cases
- Des cartes Action que l'équipe garde en main (3 max) et joue quand elle veut pendant son tour, comme au Mille Bornes
- Un historique de ce qui s'est passé dans la partie
- Afficher le gagnant et pouvoir relancer une nouvelle partie

## Conditions techniques

- Programme en HTML / CSS / JavaScript, tout dans un seul fichier
- S'exécute en local dans un navigateur, pas besoin de serveur ni d'installation
- Marche sur n'importe quel OS (Windows, Mac, Linux)
- Il faut internet au lancement (le style Tailwind et les polices sont chargés en ligne)

## Aspect graphique

- Ambiance jardin : fond clair, couleurs terracotta, ocre, vert, bleu
- Plateau en spirale, les cases spéciales ont une icône et une couleur selon leur effet (vert = bonus, rouge = malus...)
- Un pion par équipe, celui qui doit jouer est animé
- Sur le côté : les dés, les cartes en main, la liste des équipes et l'historique
- Image du plateau : `plateau jeu oie.png`

## Vérifications

- Le jeu se lance sans erreur
- On peut choisir de 2 à 10 équipes, chaque équipe a bien sa couleur
- Plusieurs parties à la suite à 10 équipes : il y a bien un gagnant à chaque fois, pas de bug
- On ne peut pas relancer les dés pendant que les dés tournent
- Le rebond sur la case 63 marche
- Chaque nouvelle action a été testée (voir ci-dessous)

## Modifications demandées à l'IA

1. Passer de 2-6 joueurs à 2-10 équipes, en gardant le reste du jeu pareil (boutons, couleurs, limites, pions qui tiennent sur une case).
2. Ajouter des nouvelles actions en respectant le format `registerGooseAction` du programme d'origine :

| Action | Effet |
|---|---|
| Aspiration | On rejoint la case de l'équipe juste devant (10 cases max) |
| Coup de vent | Toutes les autres équipes reculent de 2 cases |
| Embouteillage | On recule d'autant de cases qu'il y a d'équipes |
| Pickpocket | On vole une carte Action à l'équipe en tête |

## Fonctions à faire coder par l'IA

| Fonction | Entrée | Sortie |
|---|---|---|
| creerEquipes | nombre d'équipes, noms | liste des équipes |
| genererPlateau | % de cases spéciales | les 63 cases |
| lancerDes | nombre de dés | total |
| deplacer | position, total des dés | nouvelle position (avec rebond) |
| appliquerAction | équipe, action | nouvel état du jeu + message |
| tirerCarteChance | - | une action |
| jouerCarte | équipe, carte | nouvel état du jeu |
| equipeSuivante | état du jeu | équipe qui joue |
| verifierVictoire | état du jeu | gagnant ou rien |

## Bilan

J’ai utilisé Claude pour faire les modifications. C’est allé vraiment vite, en quelques minutes le jeu marchait avec 10 équipes et les nouvelles actions, avec peu de bug.

Mais du coup j’ai pas écrit grand chose moi-même. Le fichier fait plus de 2500 lignes et honnêtement je saurais pas le modifier tout seul sans tout relire. Je comprends ce que veut dire le sujet : on s’adapte à ce que l’IA fait au lieu de l’inverse, et on peut vite perdre la main sur son propre programme.

J’ai aussi vu qu’il faut tout vérifier, par exemple la limite à 6 joueurs était écrite à plusieurs endroits dans le code et il fallait penser à tous les changer.

Pour garder le contrôle, je pense qu’il faudrait d’abord faire soi-même l’algorithme et la liste des fonctions, et après demander à l’IA de coder fonction par fonction en testant à chaque fois.
