# Publishing
There are many ways to publish your map, we are going to cover some of them in this tutorial.

## Method 1
This is the easiest way to share your map with others, you are going to work with just one file.

### How to share:
1. In the **Code Views** unity window, click on **Show Live Generation > Show Advanced > Restart Level And Write Script**;
![Code Views](/Resources/Tutorials/publishing/01_code_views.png)
2.  In your R5 folder, go to `\platform\scripts\vscripts\mp\levels` and select the file `mp_rr_remap.nut`;
3. Now you can share the content of the file or the file itself to anyone!
![File mp_rr_remap](/Resources/Tutorials/publishing/02_mp_rr_remap_file.png)

### How to play:
1. Open the game;
2. Click on **Create Server** tab;
3. In the **Select Playlist** menu, select **Survival Dev**;
4. In the **Select Map** menu, select the corresponding map;

## Method 2
This is a better way to share your map with the whole community, you are going to work with two files and make them part of the *Flowstate Scripts*.

### How to share:
1. Go to `\platform\scripts\vscripts\custom_maps` and create a .nut file;
(For this tutorial we are going to use `_remap_tutorial.nut` for the name).
2. For the content of the new file, use the following template:
```cpp
untyped
globalize_all_functions

void function change_me_precache() {
  // PLACE YOUR PRECACHE PROPS HERE
}


struct {
  // PLACE YOUR CUSTOM VARIABLES HERE
}
file

void function change_me_init() {
  thread change_me_load()
}

void function change_me_load() {
  // PLACE YOUR PROPS ARRAY HERE
}

```
3. Fill the functions with your map props that you can get from the unity **Code Views** window or from the  `mp_rr_remap.nut` file if you went through **Method 1**;
4. Rename all template functions to something that makes sense for your map;
5. Go to `\platform\scripts\vscripts` and open the file `scripts.rson`;
6. Locate the line `//maps`, add a new line and type the name of the file you created on *step 1* 
![Code Views](/Resources/Tutorials/publishing/03_scripts_file.png)
7. Now you can go to [Flowstate Scripts](https://github.com/ColombianGuy/r5_flowstate), click on Fork, add the files you just worked on to your repo and open a PR in the original repo merging your modifications;
8. That's it. After your PR being accept, everyone will be able to play your map!

### How to play:
1. Update your [Flowstate Scripts](https://github.com/ColombianGuy/r5_flowstate);
2. Open the game;
3. Click on **Create Server** tab;
4. In the **Select Map** menu, select the corresponding map;
5. After you get inside the match, open the console (`HOME` key) and type `change_me_init()` function that you created and renamed in *step 2*;
If the map doesn't load, type `sv_cheats 1` in the console and try *step 5* again.
