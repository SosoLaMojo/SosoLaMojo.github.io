# Demo OpenGL System Solar

## Introduction

Dans le cadre du module 5300 à l'école SAE Institute, nous avions pour tâche de créer une demo non jouable avec OpenGL. Mon choix s'est orienté vers un système solaire.

![Overview Demo](../assets/GIF/Demo1.gif)

## Samples utilisés
Voici la liste des samples utilisés pour ce projet

* Skybox
* Normal Mapping
* Instancing
* Frustum Culling
* Point Light
* Bloom

## Planètes
### Normal Mapping

## Sun
### Point Light
Pour cette démo juste une seule lumière était indispensable, celle émanent du soleil. Le choix de la point light s'est imposée. Une point light est très similaire à une directionnal light, la différence est qu'on ne donne pas une direction au vertex shader mais une position et que le vertex shader doit calculer la direction de la lumière pour chaque vertex de la scène. 
![PointLight](../assets/PointLight.PNG)

Pour le fragment shader la petite différence qu'il reçoit une direction de lumière interpolée.

### Bloom
Pour créer un effet de bloom, les parties claire de la texture diffuse du soleil ont été écrites sur une texture séparée qui a ensuite été floutée pour finir par être combiné avec le résultat de la passe finale en passant par le framebuffer.

![Bloom Sun](../assets/Sun2.PNG)
![Bloom Sun](../assets/Sun1.PNG)

## Asteroids

### Instancing
### Frustum Culling

## Fond étoilé
### Skybox

# Conclusion

##### [Return to home page](https://sosolamojo.github.io/)
