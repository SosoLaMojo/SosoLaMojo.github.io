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

![Quad-tree](../assets/GIF/Quad-Tree.PNG)

## Conclusion

Ce fut un demi-module très difficile, n'ayant pas le background en maths et physique requis pour créer un moteur physique 2D. Mes objectifs pour ce module ne sont clairement pas atteints.




##### [Return to home page](https://sosolamojo.github.io/)
