# Technical Document *Scene Exporter* Tool

## Introduction
Le tool Scene Exporter a été crée dans le cadre du module 5100. L'objectif est de créer un outil pour aider les étudiants en Games Programming de 3ème année dans le développement de leur projet de jeu AerRacer.
Ce tool a été conçu en binôme avec mon camarade de classe William.[https://worgaros.github.io/](https://worgaros.github.io/)

## But de tool
Le but de cet outil est d'exporter les GameObjects contenus dans leurs scènes Unity. Ces GameObjects seront exportés avec certains de leurs composants au format Json afin d'utiliser ce fichier dans le NekoEngine.

## Fonctionnement

To open the SceneExporter tool window press Tools on the taskbar and then Scene Exporter. You can then place it wherever you want in the Unity interface.
Nous avons utilisé les fonctions EditorUnity pour créer la fenêtre, les boutons et les labels. La fenêtre contient trois boutons: **Ignore object**, **Allow object** et **Export to Json**.
![Open_Window_Tool](SosoLaMojo.github.io/assets/GIF/Open_Window.gif)

Le bouton **Ignore object** ajoute à une liste de string les noms des objets ignorés.

Le bouton **Allow object** Remove les objets de la liste d'objets à ignorer.

Le bouton **Export to Json** exporte les GameObjects en format Json, comportant les variables demandées des components voulus.
![Design_Window_Tool](SosoLaMojo.github.io/assets/PNG/Tool_Scene_Exporter/Design_Window.PNG)

