# SosoLaMojo.github.io

# Portfolio

# Game Design Document PongSoso

## Introduction

Dans le cadre du module 5100 nous devons créer un jeu multijoueur en ligne à l'aide du moteur de jeu NekoEngine, moteur de jeu interne à l'école SAE Institute Genève. Ce jeu doit comporter au minimum un niveau jouable et une interface pour la connexion d'au moins deux joueurs.

## Pitch

Le jeu PongSoso est une reproduction du jeu Pong imaginé par Nolan Bushnell et développé par Allan Alcorn en 1972. Ce jeu est inspiré du tennis de table en vue du dessus.

## Gameplay

Deux joueurs s'affrontent en déplacant verticalement la raquette représentés par un trait de couleur rouge ou bleu pour frapper la balle. **Le but** est que chaque joueur atteigne le score de **11 points avant l'adversaire**; des points qui sont gagnés lorsque l'un des joueurs ne parvient pas à renvoyer la balle à l'autre. Le joueur peut changer la direction de la balle en fonction de l'endroit où celle-ci tape sur la raquette, alors que la vitesse augmente graduellement au cours de la manche. Un score est affiché pour la partie en cours et un bruitage accompagne la frappe de la balle sur les raquettes. Des murs sont présent en haut et en bas de l'écran afin que la balle ne puisse pas sortir de l'écran par ses extrémités.

![LevelDesign](SosoLaMojo.github.io/assets/Pong_Soso.jpg)

## Controls



# Blogpost Moteur Physique

## Mise en contexte

Dans le cadre de fin de module 4400 nous devions créer un moteur physique 2D sur les bases du Neko Engine créé par nos professeurs en implémentant les matrices, vecteurs, collisions, rebonds, rigidbody, AABB etc...

## Quad-tree

Les quadtrees sont des arbres utilisés pour stocker efficacement des données de points sur un espace bidimensionnel. Dans cet arbre, chaque node a au plus quatre enfants.
Nous pouvons construire un quad-treee à partir d'une zone bidimensionnelle en utilisant les étapes suivantes:

* Divisez l'espace bidimensionnel actuel en quatre cases.
* Si une boîte contient un ou plusieurs points, créez un objet enfant en y stockant l'espace bidimensionnel de la boîte
* Si une boîte ne contient aucun point, ne créez pas d'enfant pour elle
* Recurse pour chacun des enfants.

Voici un exemple d'implémentation des quatre cases à créer:

![Quad-tree](SosoLaMojo.github.io/assets/GIF/Quad-Tree.PNG)

## Conclusion

Ce fut un demi-module très difficile, n'ayant pas le background en maths et physique requis pour créer un moteur physique 2D. Mes objectifs pour ce module ne sont clairement pas atteints.

# Blogpost du jeu Dungeon Survivor

## Mise en contexte

Le jeu Dungeon Survivor à été crée dans le cadre du module 4400 en Games Programming de l'école SAE Institute Genève dans le but nous évaluer sur l'implémentation d'une génération procédurale et d'une intelligence artificielle en binôme.

## Pitch

On incarne un humain armé d'un pistolet qui se trouve dans un donjon qui contient des zombies et le but est de parcourir ce donjon tout en survivant afin de trouver le coffre qui se trouve en fin de parcours pour gagner la partie.

## Répartition des tâches

Nous nous sommes diviser le travail en plusieurs tâches.

Bryan: Chargé des 3C(camera, controls, character) et la génération procédurale du donjon.

Solange: Chargé des ennemis (IA et state machine), level design, animations et UI.

## 3C
En ce qui concerne le joueur, il peut se déplacer et tirer et il peut se faire attaquer et ainsi perdre de la vie. Il se déplace avec les touches WASD et sa rotation suit la position de la souris. Pour tirer, il faut appuyé sur le clique gauche. La caméra suit en permanence le joueur.

## Génération procédurale
En ce qui concerne la génération procédurale, on a opté pour un système de salle pré-fabriqué. Chaque salle possède plusieurs points de spawn pour les ennemies et les objects de soins qui sont générés en même temps.

Je vous met le lien du blogpost technique de mon binome Bryan qui c'est lui-même chargé de l'implémentation de la génération procédurale:
[https://zcallmez.github.io/](https://zcallmez.github.io/)

## Pathfinding

Voici un rendu visuel qui montre comment se placent les nodes sur la map afin que les zombies puissent trouver leur chemin

![Generation des nodes](SosoLaMojo.github.io/assets/GIF/Nodes.gif)

## Zombies
* Le premier se nomme "Zombie Classique", il a un comportement qu'on peut retrouver dans la majorité des jeux de zombies. Il réagit et attaque dès que le joueur se trouve dans son champ de vision. Tout ceci marche à l'aide de Transform, Trigger et machine d'états.

![ZombieClassique](SosoLaMojo.github.io/assets/GIF/ZombieClassique.gif)

Voici comment fonctionne sa machine d'états:

Etat IDLE:

Il ne fait rien sauf si le bool isFollowingPlayer passe a true, a ce moment il passera à l'état FOLLOW.

![State IDLE](SosoLaMojo.github.io/assets/GIF/StateMachineIDLEZombieClassique.PNG)

Etat FOLLOW:

Il va récupérer le script du pathfinding afin de trouver son chemin jusqu'au joueur et utiliser la fonction MoveCharacter() qui lui permet de se déplacer. Si le joueur sort de sa zone de détéction il passera à l'état RETURN_INITIALPOSITION, autrement si le bool isAttack passe a true en entrant en collision avec le joueur il passera à l'état ATTACK.

![State FOLLOW](SosoLaMojo.github.io/assets/GIF/StateMachineFOLLOWZombieClassique2.PNG)

Etat RETURN_INITIALPOSITION:

Il va récupérer le script du pathfinding afin de trouver son chemin jusqu'a sa position initiale et utiliser la fonction MoveCharacter() qui lui permet de se déplacer. Quand sa position initiale est atteinte il va retourner a l'état IDLE, mais lors de son déplacement si il détécte le joueur il passera à l'état ATTACK.

![State RETURN_INITIALPOSITION](SosoLaMojo.github.io/assets/GIF/StateMachineRETURN_INITIALPOSITIONZombieClassique.PNG)

Etat ATTACK:

Il va activer son animation d'attaque au contact du joueur mais si son bool isAttack passe a false il va arreter son animation d'attaque et retourner à l'état IDLE pour autant que le joueur ne soit pas dans son chant de détéction.

![State ATTACK](SosoLaMojo.github.io/assets/GIF/StateMachineATTACKZombieClassique.PNG)

Etat DEAD:

Avant le début de la state machine il va tout le temps contrôler si la vie du zombie est isAlive ou non, si sa vie tombe a zero il passera a n'importe quel moment en état DEAD.

![Condition de mort](SosoLaMojo.github.io/assets/GIF/DépartUpdateForStateMachineZombieClassique.PNG)

Si il entre en état DEAD il va alors jouer son animation de mort puis se détruire.

![State DEAD](SosoLaMojo.github.io/assets/GIF/StateMachineDEADZombieClassique.PNG)

* Le deuxième se nomme "Zombie Kamikaze", il attaque le joueur dès qu'il est à sa portée et il explose au contact de celui-ci, ce qui cause de gros dégâts. Tout ceci marche à l'aide de Transform, Trigger et machine d'états.

Il fonctionne de la même manière que le zombie classique à une différence près:

Quand il entre en collision avec le joueur il joue son animation d'explosion et fait plus de dégats au joueur que le zombie classique puis se détruit. Il se déplace aussi bien plus rapidement.

![State ATTACK](SosoLaMojo.github.io/assets/GIF/StateMachineATTACKZombieKamikaze.PNG)

* Le dernier se nomme "Zombie Tank", il se déplace autour des coffres qui permet de gagner la partie et possède un nombre de points de vie assez élévé. Sa particularité est qu'au contact du joueur, celui-ci perd de la vie et est directement téléporter au début du niveau. Tout ceci marche à l'aide de Transform et de Trigger.

## Conclusion

Ce fut très compliqué pour nous de réussir à rendre ce projet dans les délais impartis au vu de nos situations personnelles.
Notre jeu n'est clairement pas aboutit malgré notre envie de bien faire. J'ai tout de même été très contente de travailler avec Bryan qui est un très bon binôme, nous avone eu une très bonne communication.
En ce qui concerne l'implémentation de la génération procédurale et le pathfinding j'ai été complétement perdue et n'ai pas réussi à atteindre mes objectifs.


# Post-mortem S.O.S : Save Our Souls

## Points Positifs
* Première utilisation de la tilemap sur Unity, ce qui m'a beaucoup appris
* Bonne communication avec mon binôme Vincent
* Le jeu fonctionne et correspond à mes attentes dans le temps qui nous a été impartit
* Collaboration avec un Gameart de la SAE

## Points Négatifs
* Manque de temps à consacré au jeu au début du développement du a la maladie
* Reçu des assets assez tardif, il nous en manque
