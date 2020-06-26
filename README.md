# SosoLaMojo.github.io

# Portfolio

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
https://zcallmez.github.io/

## Pathfinding

![Generation des nodes](SosoLaMojo.github.io/assets/GIF/Nodes.gif)

## Zombies
* Le premier se nomme "Zombie Classique", il a un comportement qu'on peut retrouver dans la majorité des jeux de zombies. Il réagit et attaque dès que le joueur se trouve dans son champ de vision. Tout ceci marche à l'aide de Transform, Trigger et machine d'états.

Voici comment fonctionne sa machine d'états:

Il ne fait rien sauf si le bool isFollowingPlayer passe a true, a ce moment il passera à l'état FOLLOW.

![State IDLE](SosoLaMojo.github.io/assets/GIF/StateMachineIDLEZombieClassique.PNG)



![State FOLLOW](SosoLaMojo.github.io/assets/GIF/StateMachineFOLLOWZombieClassique2.PNG)

![State RETURN_INITIALPOSITION](SosoLaMojo.github.io/assets/GIF/StateMachineRETURN_INITIALPOSITIONZombieClassique.PNG)

![State ATTACK](SosoLaMojo.github.io/assets/GIF/StateMachineATTACKZombieClassique.PNG)

![State DEAD](SosoLaMojo.github.io/assets/GIF/StateMachineDEADZombieClassique.PNG)

![Condition de mort](SosoLaMojo.github.io/assets/GIF/DépartUpdateForStateMachineZombieClassique.PNG)



* Le deuxième se nomme "Zombie Kamikaze", il attaque le joueur dès qu'il est à sa portée et il explose au contact de celui-ci, ce qui cause de gros dégâts. Tout ceci marche à l'aide de Transform, Trigger et machine d'états.

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
