# SosoLaMojo.github.io

# Portfolio

# Blogpost du jeu Dungeon Survivor

## Introduction

Le jeu Dungeon Survivor à été crée dans le cadre du module 4400 en Games Programming de l'école SAE Institute Genève dans le but nous évaluer sur l'implémentation d'une génération procédurale et d'une intelligence artificielle en binôme.
On incarne un humain armé d'un pistolet qui se trouve dans une salle avec une horloge et le but est de parcourir un dongeon rempli de zombies afin de trouver une clé permettant d'ouvrir l'horloge et pouvoir s'échapper.

Nous nous sommes diviser le travail en plusieurs tâches.
Bryan: Chargé des 3C(camera, controls, character), la génération procédurale du donjon et l'IA.
Solange: Chargé des ennemis, level design, animations, sons, menu et IA.

## 3C
En ce qui concerne le joueur, il peut se déplacer et tirer et il peut se faire attaquer et ainsi perdre de la vie. Il se déplace avec les touches WASD et sa rotation suit la position de la souris. Pour tirer, il faut appuyé sur le clique gauche. La caméra suit en permanence le joueur.

## Pathfinding

![Generation des nodes](C:\Users\Solange\Videos\DungeonSurvivor\Nodes.gif)

## Zombies
* Le premier se nomme "Zombie Classique", il a un comportement qu'on peut retrouver dans la majorité des jeux de zombies. Il réagit et attaque dès que le joueur se trouve dans son champ de vision. Tout ceci marche à l'aide de Transform et de Trigger.

* Le deuxième se nomme "Zombie Kamikaze", il attaque le joueur dès qu'il est à ça porter et il explose au contact de celui-ci, ce qui cause de gros dégâts. Tout ceci marche à l'aide de Transform et de Trigger.

* Le dernier se nomme "Zombie Tank", il se déplace autour des coffres qui contiennent les clés qui permettent d'activer l'horloge pour s'évader du donjon et ainsi compléter le jeu et possède un nombre de point de vie assez élévé. Sa particularité est qu'au contact du joueur, celui-ci perd de la vie et est directement téléporter au début du niveau. Tout ceci marche à l'aide de Transform et de Trigger.

## Génération procédurale
En ce qui concerne la génération procédurale, on a opté pour un système de salle pré-fabriqué. Chaque salle possède plusieurs points de spawn pour les ennemies et les objects de soins qui sont générés en même temps.

Le processus se déroule de la manière suivante :

* Toutes les salles ont une forme rectangulaire sauf la salle de départ qui possède 4 sorties ouvertes, les autres salles possèdent entre 1 ou 2 sorties ouvertes.

* Chaque salle vérifie si dans chacune de ses directions, il y a déjà une salle et si ce n'est pas le cas, elle en génère une. Ensuite, une fois que cette salle est génèrée, elle regarde dans quelle direction elle peut y aller, et s'il n'y a pas de salle dans la direction dans laquelle elle est, elle en génère une. Et ainsi de suite.

* Dès que 10 salles sont générées, la probabilité qu'une salle ait une sortie diminue et ainsi provoque la fin de la génération procédurale et boucle la map.

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
