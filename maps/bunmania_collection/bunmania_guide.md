# Bunmania Guide
-------------------------------

# Config
![img7_config](https://user-images.githubusercontent.com/27341392/53293796-cdd0e980-3815-11e9-9716-167938b57f6e.png)

### Hotkeys
- (1) Reduce time left before map change
- (2) Increase time left before map change
- (3/4) Select next map when map change occurs.
- (0) Refresh map folder

- Menu + Item + Boost: Quick load autosave
- Menu + Item + Magic Left: Quick restart level
- Menu + Up + Jump + Item: Disconnect / Exit Bunmania mode
- Menu + F1: Spectator mode

### Other Stuff

#### Switching maps
- To switch maps, press menu, then use (3/4) to choose the next map. Then hold (1) until the map change timer goes to 0.

#### Preventing map auto switch
- There is currently no way to disable map auto switch. To prevent map auto switch from interrupting your game, press menu, then hold (2) to add a bunch of time to the map change timer.


---------------------------------

# How to Start Bunmania (With images!)

### Step 1
In Steam, right click Rabi-Ribi -> Properties -> BETAS -> Switch to `beta - Netplay BETA v27`.

![steam_beta](https://user-images.githubusercontent.com/27341392/53293943-8b5cdc00-3818-11e9-834d-489a17ab60e8.png)

### Step 2
Press F5/F6 on Title screen to select a custom map.

![img1_mapselect](https://user-images.githubusercontent.com/27341392/53293790-cc9fbc80-3815-11e9-8107-fad5ada76680.png)

### Step 3
Start a new game (any mode, any difficulty).

![img2_startgame](https://user-images.githubusercontent.com/27341392/53293791-cc9fbc80-3815-11e9-8d78-de0261c09ce6.png)

### Step 4
Press F3 in game to open Network Mode menu.

![img3_networkmode](https://user-images.githubusercontent.com/27341392/53293792-cd385300-3815-11e9-96ef-7ff1fc71c25a.png)

### Step 5
Select HOST, then set MODE to BUNMANIA.

![img4_selectbunmania](https://user-images.githubusercontent.com/27341392/53293793-cd385300-3815-11e9-8071-7e7d58f8bbb4.png)

### Step 6
Press jump to start.

![img5_bunmaniastart](https://user-images.githubusercontent.com/27341392/53293794-cd385300-3815-11e9-9794-f392fae2f52b.png)

![img6_levelclear](https://user-images.githubusercontent.com/27341392/53293795-cd385300-3815-11e9-96e4-eedd86bcad2c.png)



---------------------------------


# Making Bunmania Maps

[**How to Make Rabi-Ribi Custom Maps**](https://wcko87.github.io/rabiribi-map-editing/)

## Bunmania Restrictions
- Only area0.map may be used.
- No custom tilesets, dialogue etc can be used.

## Bunmania Map Metadata
![bunmania_metadata_display](https://user-images.githubusercontent.com/27341392/53294776-e26aad00-3828-11e9-879a-e74e5b45d635.png)

In the latest version of the [rbrb-map-coverter](https://ci.appveyor.com/project/wcko87/rbrb-map-converter/build/artifacts), Bunmania metadata can be set in Custom Properties in your map. (using the Tiled map editor)

![custom_properties](https://user-images.githubusercontent.com/27341392/53293945-8bf57280-3818-11e9-900b-2dab298bceb9.png)

- bunmania (bool): Check to save Bunmania metadata into map.
- bm_name (string): Map name. Max 32 char, ASCII only.
- bm_author (string): Author's name. Max 16 char, ASCII only.
- bm_par1 (float): Par time (rainbow), in seconds.
- bm_par2 (float): Par time (platinum), in seconds.
- bm_par3 (float): Par time (gold), in seconds.
- bm_par4 (float): Par time (silver), in seconds.
- bm_par5 (float): Par time (bronze), in seconds.
- bm_difficulty (int): Difficulty rating (1-5 stars)
- bm_fullexp (bool): Check to start with full hammer exp.
- bm_numeggs (int): Number of hidden easer eggs in map.

Make sure to tick "bunmania" so that your custom properties will be saved.

![custom_properties_2](https://user-images.githubusercontent.com/27341392/53294041-48036d00-381a-11e9-8b83-f23f0fd3a390.png)

If you have an existing map in Tiled which does not have abovementioned the custom properties, you can add the above custom properties on your own. Make sure that the name and type of the custom property matches those in the list above.

#### Encoding map metadata manually

If you are not using rbrb-map-converter to automatically set the metadata for you, you can also encode the map metadata manually.

The metadata is encoded into the events layer. Use event ids 5000+ to encode metadata. For example:
- To encode an int of value 39, use event `5039`.
- To encode the letter "A" (ascii ID 65), use event `5065`.

```
LINE 1 : Map Name (max 32 char, ASCII only)
LINE 2 : AUTHOR (max 16 char, ASCII only)
LINE 3-7 : Par time (bronze - rainbow). Three numbers - minutes, seconds, milliseconds, each 0-59.
LINE 8 : Starting Hammer Exp 9999 (5001) Exp 0 (5002)
LINE 9 : Difficulty 1 - 5 (1 star if empty) 
LINE 10 : Num of Easter Eggs on map (If you want to tell player there is secret in map), not visible if empty
```

![manual_metadata](https://user-images.githubusercontent.com/27341392/53294777-e26aad00-3828-11e9-984c-0f09b8c6b57b.png)
