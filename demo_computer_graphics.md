# Demo OpenGL System Solar

## Introduction

Dans le cadre du module 5300 à l'école SAE Institute, nous avions pour tâche de créer une demo non jouable avec OpenGL en utilisant plusieurs techniques de rendus différents. Mon choix s'est orienté vers un système solaire.

![Overview Demo](../assets/GIF/Demo1.gif)

## Planètes
### Normal Mapping

## Sun
### Point Light
Pour cette démo juste une seule lumière était indispensable, celle émanent du soleil. Le choix de la point light s'est imposée. Une point light est très similaire à une directionnal light, la différence est qu'on ne donne pas une direction au vertex shader mais une position et que le vertex shader doit calculer la direction de la lumière pour chaque vertex de la scène. Pour le fragment shader la petite différence qu'il reçoit une direction de lumière interpolée. Le type de lumière qui a été utilisée dans cette demo est le Blinn-Phong.
![PointLightSchema](../assets/PointLight.PNG)
![PointLightDemo](../assets/PointLight3.png)

### Bloom
Pour créer un effet de bloom, les parties claires de la texture diffuse du soleil ont été écrites sur une texture séparée qui a ensuite été floutée pour finir par être combiné avec le résultat de la passe finale en passant par le framebuffer.

![Bloom Sun](../assets/Sun2.PNG)
![Bloom Sun](../assets/Sun1.PNG)

## Asteroids

### Instancing
### Frustum Culling
Le frustum Culling consiste à créer uniquement les objet qui se trouve dans le champ de vision de la caméra en utilisant un frustum. Cette technique a été utilisé pour l'instancing des asteroids étant donné qu'il y en a 7000 dans la scène et qu'il ne sont pas forcément tous visibles en même temps.

![FrustumCulling Schema](../assets/FrustumCulling.jpg)

Pour démontrer que le Frustum Culling utilisé fonctionne, la taille du Frustum à été réduite dans l'exemple ci-dessous:

![FrustumCulling Demo](../assets/GIF/FrustumCulling.gif)

## Fond étoilé
### Skybox
Une skybox est un procédé graphique permettant de donner, dans un espace tridimensionnel, l'illusion que cet espace est plus étendu qu'il ne l'est réellement. Pour ce faire nous utilisons une texture qui contient plusieurs faces et les assemblons pour créer une énorme boite qui contiendra les objets de la scène.

![Skybox exemple](../assets/Example_Skybox.png)

# Conclusion

##### [Return to home page](https://sosolamojo.github.io/)
