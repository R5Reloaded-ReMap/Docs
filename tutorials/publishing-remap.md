# Publishing
There are many ways to publish your map, we are going to cover some of them in this page.

## Method 1: Quick Share
This is the easiest way to share your map with others, requiring you to work with just one file. This method is quick and straightforward, ideal for sharing with friends or small groups.

### How to share:
1. In the **Code Views** unity window, click on **Show Live Generation > Show Advanced > Restart Level And Write Script**;  
![Code Views](/Resources/Tutorials/publishing/01_code_views.png)  
2. In your R5 folder, go to `\platform\scripts\vscripts\mp\levels` and select the file `mp_rr_remap.nut`;  
![File mp_rr_remap](/Resources/Tutorials/publishing/02_mp_rr_remap_file.png)  
3. Now you can share the content of the file or the file itself to anyone!  

### How to play:
1. Open the game;  
2. Click on **Create Server** tab;  
3. In the **Select Playlist** menu, select **Survival Dev**;  
4. In the **Select Map** menu, select the corresponding map;  

## Method 2: Community Share
This method is ideal for sharing your map with the whole community. It involves working with four files and integrating them into the Flowstate Scripts repository, making your map available to the entire playerbase.

### How to share:
1. Go to `\platform\scripts\vscripts\custom_maps` and create a .nut file for your map;  
(For this tutorial we are going to use `_remap_tutorial.nut` as the name.)
2. For the content of the new file, use the following template:  
```cpp
untyped
global function change_me_init


void function change_me_precache() {
  // PLACE YOUR PRECACHE PROPS HERE
}


struct {
  // PLACE YOUR CUSTOM VARIABLES HERE
}
file

void function change_me_init() {
  AddCallback_OnClientConnected( change_me_player_setup )
	AddCallback_EntitiesDidLoad( change_meEntitiesDidLoad )
  change_me_precache()
}

void function change_meEntitiesDidLoad()
{
	thread change_me_load()
}

void function change_me_player_setup() {
  // SETUP THE PLAYERS AND INITIALIZE THEIR VARIABLES HERE 
}

void function change_me_load() {
  // PLACE YOUR PROPS ARRAY HERE
}

```
3. Fill the functions with your map props that you can get from the unity **Code Views** window or from the  `mp_rr_remap.nut` file if you went through **Method 1**;  
4. Rename all template functions to something that makes sense for your map;  
5. Go to `\platform\scripts\vscripts` and open the file `scripts.rson`;  
6. Locate the line `//maps`, add a new line and type `custom_maps/` followed by the name of the file you created on *step 1* (for example: `custom_maps/_remap_tutorial.nut`);  
![Code Views](/Resources/Tutorials/publishing/03_scripts_file.png)  
7. Go to `\platform\scripts\vscripts` and open the file `_mapspawn.gnut`;  
8. Locate the line `switch( GetCurrentPlaylistName()` and add this new line inside in the bottom of the switch structure (Don't forget to change the placeholder names to the ones for your map.):  
```
case "fs_changememovementpractice":
change_me_init()
break
```
![Map Spawn file](/Resources/Tutorials/publishing/04_mapspawn_file.png)  
9. Now go to `\platform` folder and open the file `playlist_r5_patch.txt`;  
10. Locate the line `fs_mantlejumppractice` and create a new line below the closing curly bracket of it to paste the following code:  
```
		fs_changememovementpractice
		{
			inherit fs_survival
			vars
			{
				name                                           "Change Me Movement Map [Practice Map]"
				visible                                        1

				// Skip intros:
				waiting_for_players_spawning_enabled           1
				waiting_for_players_countdown_seconds          0
				waiting_for_players_timeout_seconds            1
				character_select_time_max                      0.0
				character_select_time_min                      0.0
				survival_enable_gladiator_intros               0
				jump_from_plane_enabled                        0
				survival_shields							                 1
				survival_infinite_ammo						             1

				// No circle:
				sur_circle_start_paused                        1

				is_practice_map								                 1
				// Can change loadouts:
				dev_loadout_changeable_at_any_time             1
				sur_dev_unrestricted_character_changes         1

				// Bots:
				sur_bots_spawn_with_random_weapons             1
				match_ending_enabled                           0
				max_team_size								                   120
				max_players                                    120
				min_players                                    1
				enable_nessies                                 0

			}
			gamemodes { survival { maps {
				mp_rr_desertlands_64k_x_64k                    	1
				mp_rr_desertlands_64k_x_64k_nx                 	1
				mp_rr_desertlands_64k_x_64k_tt                 	1
				
			} } }
		}
```
![Playlist](/Resources/Tutorials/publishing/08_playlist.png)  
11. Change the first line to the one you used in step 8 and the value of the `name` to something that makes sense to your map;  
12. Create a [GitHub account](https://github.com/signup) if you don't have one;  
13. Go to the Flowstate Script repository and [fork it](https://github.com/ColombianGuy/r5_flowstate/fork);  
14. Deselect the `Copy the r5_flowstate branch only` option and click and `create fork`;  
15. Wait for it to redirect you to your fork and create a new workspace by following the screenshot:  
![Fork](/Resources/Tutorials/publishing/05_fork.png)  
16. Replicate the modifications you did on your machine to your workspace;  
17. You will notice that the there is no `playlist_r5_patch.txt`, we will handle that later (step 21);  
18. Click on the "Source Control" icon, then on the top "+" icon to stage all the changes, type something then click on "commit", the button will change to "Sync Changes", click on it;  
![Workspace](/Resources/Tutorials/publishing/06_workspace.png)  
19. Now you can go to the Flowstate Scripts repo and create a new [Pull Request](https://github.com/ColombianGuy/r5_flowstate/compare);  
20. Click on `compare across forks` to enable your fork, select the `IndevNew` for the base option, select your repo for the head option and select the `IndevNew` of your fork;  
21. Then click on `Create Pull Request` and two new options will show up;  
22. For "title" you can change to something like "Add my new movement map";  
23. For the description, you gotta add the content of what you changed in the `playlist_r5_patch.txt` during step 10 so the owner can make this necessary change himself;  
24. That's it. After your PR being accept, everyone will be able to play your map!  

### How to play:
1. Make sure your Pull Request was merged and your R5Reloaded is up to date;  
2. Open the game;  
3. Click on **Create** tab;  
4. In the **Select Map** menu, select the corresponding map;  
5. In the **Select Playlist** menu, select your map;  
6. Click in **Start Game** ;  
7. That's it. Now you and the whole R5R community have access to your map;  
