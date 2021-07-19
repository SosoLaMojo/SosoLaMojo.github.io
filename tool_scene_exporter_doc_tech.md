# Technical Document *Scene Exporter* Tool

## Introduction
The Scene Exporter tool was created as part of the 5100 module. The objective is to create a tool to help 3rd year Games Programming students in the development of their AerRacer game project.
This tool was designed in tandem with my classmate William.[https://worgaros.github.io/](https://worgaros.github.io/)

## Goal of tool
The goal of this tool is to export the GameObjects contained in their Unity scenes. These GameObjects will be exported with some of their components in Json format in order to use this file in the NekoEngine.

## How it works

To open the SceneExporter tool window press Tools on the taskbar and then Scene Exporter. You can then place it wherever you want in the Unity interface.
We used the EditorUnity functions to create the window, buttons and labels. The window contains three buttons: **Ignore object**, **Allow object** and **Export to Json**.
![Open_Window_Tool](../assets/GIF/Open_Window.gif)

The button **Ignore object** adds to a string list the names of the ignored objects.

The button **Allow object** removes objects from the ignore list.

The button **Export to Json** exports the GameObjects in Json format, with the requested variables of the desired components. This button calls the SaveHierarchy() function.
![Design_Window_Tool](../assets/PNG/Tool_Scene_Exporter/Design_Window.PNG)

The function **SaveHierarchy()** retrieves the name of the active scene, the list of tags and the list of layers. 

Then it will call the functions **GetAllObjectsOnlyInScene()** to ignore the hidden GameObjects contained in the scene. 

Then it will call the function **CheckHierarchy()** which will browse the whole Hierarchy of the active scene to retrieve for each GameObject and their children: name, instanceID, if the object is active or not, the associated layer and tag as well as all the variables of the desired components by using functions **Populate()** that each component class contains. 

The function **CheckHierarchy()** remembers itself in a loop for each child of the GameObject. 

The function **SaveHierarchy()** will finally call the function **WriteToFile()** which will create the Json file.

![Diagramme](../assets/PNG/Tool_Scene_Exporter/Diagramme.png)


## Challenges

For this project the challenges were:
* Learn how to use Unity's GUI for window creation, buttons and labels
* Learn how to format a Json
* Learn how to make the right Json format with the project's JsonValidator



##### [Return to home page](https://sosolamojo.github.io/)
