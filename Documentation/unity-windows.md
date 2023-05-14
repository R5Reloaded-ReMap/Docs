
# Windows In Unity

## Introduction
We use the Unity Engine to develop ReMap, as it is a video game development environment, many things are present but are useless for the basic use of ReMap.

Here are the most useful Unity windows:

## Project Window

This window is used to manipulate all the apex assets and the different levels you will create.

**Attention!** Here only the folder `Levels` and `Prefabs` will be useful, don't look elsewhere, this is used for developers.

![Project Window](/Resources/Documentation/unity-windows/project-window.png)

### `Levels` Folder
Is used to save your maps, to create a new one, go to the folder, right click and click on `Create/Scene`.

### `Prefabs` Folder

This folder contains **95%** of the models of Apex legends in **Season 3**, these folders are arranged by rpak ( files that store the models ), a folder also called `all_models` contains all models

The principle is just drag and drop in your scene to put a model.

![Prefabs Folder](/Resources/Documentation/unity-windows/project-window-prefabs.png)

A folder also contains objects such as
* Doors
* Ziplines
* Buttons
* Triggers
* Jumppads
* Let you discover the rest

![Custom Prefabs Folder](/Resources/Documentation/unity-windows/project-window-prefabs-custom.png)


## Hierarchy Window

This window is used to manage all the objects in your map, you can and should create folders / subfolders to gather parts of your map in one.

To create an empty folder, you can right click on `Create Empty`.

You can also move them inside like in a file explorer.

![Hierarchy Window](/Resources/Documentation/unity-windows/hierarchy-window.png)


## Inspector Window

This window allows you to change the `position` / `angles` / `scale` and the parameters of the object to match your needs in apex.

**Attention!** If you change the scale of objects of type `prop`, apex will only change the `size` of the model and the `collision` will remain the `1:1` scale

![Inspector Window](/Resources/Documentation/unity-windows/inspector-window.png)


## Scene Window

This window is the preview of your map, you with some tools that will be useful to create your map.

### Hand Tool

Use to move your camera across the map.

### Move Tool

Use to move objects.

### Rotate Tool

Use to rotate objects.

### Scale Tool

Use to change the size of the objects.

### Drop To Ground Tool

Places an object on the nearest floor below itself.


![Scene Window](/Resources/Documentation/unity-windows/scene-window.png)
