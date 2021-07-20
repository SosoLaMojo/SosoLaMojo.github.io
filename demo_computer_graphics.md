# Demo OpenGL System Solar

## Introduction

Dans le cadre du module 5300 à l'école SAE Institute, nous avions pour tâche de créer une demo non jouable avec OpenGL en utilisant plusieurs techniques différentes. Mon choix s'est orienté vers un système solaire.

![Overview Demo](../assets/GIF/Demo1.gif)

# Rendu 3D
## Planètes + Soleil
![SpawnPlanets](../assets/GIF/spawnPlanets.gif)

Le soleil se trouve au centre de la scène (0,0,0) et les planète ses dessine les unes après les autres a partir du centre de cette scène. Les planètes ont chacune une texture color et une normale qui sont appliquées sur une sphère.

![Texture Planet Venus](../assets/Montage_normal_mapping.PNG)


# Asteroids
## Instancing
La technique utilisée pour le soleil et les planètes n'est pas appropriée pour les deux ceintures d'asteroids, dessiner les asteroids les uns aprés les autres serait trop couteux point de vue performances. La solution la plus sensée est d'utiliser l'instancing qui consiste a dessiner plusieurs objets dans un seul drawcall par le GPU sans avoir a communiquer de nouveau avec le CPU pour chaque objet. Dans notre cas cela permet d'envoyer qu'une seule texture pour la couleur et qu'un seul mesh pour tout les asteroides.

![Texture Asteroid](../assets/Montage_Asteroid.PNG)

## Frustum Culling
Le Frustum Culling consiste à dessiner uniquement les objets qui se trouvent dans le champ de vision de la caméra en utilisant un Frustum. Cette technique a été utilisé pour l'instancing des asteroids étant donné qu'il y en a 7000 dans la scène et qu'il ne sont pas forcément tous visibles en même temps.

![FrustumCulling Schema](../assets/FrustumCulling.jpg)

Pour démontrer que le Frustum Culling utilisé fonctionne, la taille du Frustum à été réduite dans l'exemple ci-dessous:

![FrustumCulling Demo](../assets/GIF/FrustumCulling.gif)

## Backface Culling
Le backface culling est une technique qui permet de ne pas rendre ce qui est derrière un objet (les faces non visibles). Avec un objet transparent le backface culling n'est pas recommandé afin de pouvoir voir l'avant et l'arrière de l'objet.
N'ayant pas d'objets transparent dans la scène le backface culling offre un gain de performance pour ne pas afficher les faces se trouvants à l'arrière des planètes, du soleil et des asteroides.

![BackFace Culling](../assets/backfaceCulling.png)

# Light
## Point Light
Pour cette démo juste une seule lumière était indispensable, celle émanent du soleil. Le choix de la point light s'est imposée puisque c'est une lumière proche de celle du soleil. Comme c'est du forward rendering qui a été utilisé dans la scène, il suffit d'envoyer la position de la source umineuse à chaque fragement shader, les calculs de lumière ainsi que son atténuation sont directement calculés dans les shaders. Pour rappel le forward rendering est le fait de rendre chaque objet les uns-après les autres et de calculer individuellement la lumière pour eux. Le modèle de lumière qui est utilisé est celui de Blinn-Phong, il a été choisis pour sa simplicité à être mis en place mais aussi l'avantage d'avoir besoin de moins de textures qu'une solution comme du PBR (Lien pour plus d'information sur ce modèle de lumière ici)

![PointLightSchema](../assets/PointLight.PNG)
![PointLightDemo](../assets/PointLight3.png)

Le soleil a un fragment shader de lumière différent des autres planètes et des asteroids qui ne calcul pas la lumière de facon a ne pas être illuminé. Parce que la point light se trouve au centre du soleil, il avait donc une absence de lumière.

## Normal Mapping
Les planètes sont des objets simples spheres sans reliefs, c'est un avantage et un inconvénients. L'avantage est que c'est plus léger pour la mémoire et donc plus rapide a charger. Le désavantage c'est qu'on perd la profondeur sur les objets (exemple on ne voit pas les cratères).
Une solution a ca c'est le normal mapping. Il consiste a donner une illusion de reliefs sur des objets en utilisant une texture suppléementaire. Cette texture va remplacer les normales du mesh et avoir une plus grande définition et donner cette impression de reliefs lorsque la lumière va créer des zones non illuminées sur l'objet. Cette technique n'a pas été utile pour les asteroids au vu du fait qu'il y avait déja assez de détails dans le mesh.

![Normal mapping compare](../assets/normal_mapping_compare.png)

## Bloom
Pour créer un effet de bloom, les parties claires de la texture diffuse du soleil ont été écrites sur une texture séparée qui a ensuite été floutée avec du mipmapping pour finir par être combiné avec le résultat de la passe finale en passant par le framebuffer.

![Bloom Sun](../assets/Montage_bloom_sun.PNG)

## Tone mapping
Le problème qui survient en rajoutant du bloom, est que par défaut dans le framebuffer les couleurs sont contenus entre 0 et 1, c'est ce qu'on appel du LDR. Pour pallier a ce problème on utilise du HDR pour ne pas limiter les couleurs entre 0 et 1. Par contre comme nos écrans sont en LDR, nous devons repasser en LDR en utilisant du tone mapping, avec par exemple la technique de Reihnard, utilisée dans cette demo.
![Tone Mapping](../assets/hdr_exposure_tone_mapping.png)

# Skybox
## Fond étoilé
Une skybox est un procédé graphique permettant de donner, dans un espace tridimensionnel, l'illusion que cet espace est plus étendu qu'il ne l'est réellement. Pour ce faire nous utilisons une texture qui contient plusieurs faces et les assemblons pour créer une énorme boite qui contiendra les objets de la scène.

![Skybox exemple](../assets/Example_Skybox.png)

# Conclusion
J'ai appris beaucoup durant ce module tel que sité plus haut mais je ne suis pas totalement satisfaite du résultat. Certaines optimisations et techniques auraient pu être faites comme:
* Loader qu'un seul obj sphère pour toutes mes planètes
* Faire un oval avec les ceintures d'asteroides et non des cercles
* Régler la rotation des planètes sur elles-mêmes qui ne sont pas correctes
* Inclure des vaisseaux de Star Wars
* Ajouter du PBR pour un meilleur rendu visuel
* Ajouter du Shadow Map
* Implémenter une caméra plus complexe pour le déplacement automatique

Avec une meilleure comprehension de OpenGL et plus de temps j'aurais certainement réussi a atteindre ses objectifs.

##### [Return to home page](https://sosolamojo.github.io/)
