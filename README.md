# Lets Mod You Some Minecraft

Minecraft is the beloved game by many kids and adults like me for doing almost anything you want in a low res world. The modding community took that idea even further and allowed players to do even more. I love playing modpacks like Feed The Beast that combine a bunch of great mods that give you the ability to cast magic with ruins, travel to other planes, make nuclear reactors, and so much more. Maybe you’ve thought about some cool stuff you’d like to have or do in minecraft to make it even more fun. Well now you can by making your own mod. We’re going to be making our own simple mod, which will set the stage for you to build your own blocks, crafting recipes, tools, armor, mobs, game rules, etc. There’s a lot that we need to do to get to the point of playing our mod and I will guide you step by step in this workshop.

## Zircon Mod
Based on Modding by Kaupenjoe’s [tutorial for v1.19 of Minecraft](https://www.youtube.com/watch?v=LpoSy091wYI&list=PLKGarocXCE1HrC60yuTNTGRoZc6hf5Uvl)

**We're going to jump into the tutorial so we can get everything running and downloading while I give my intro**

Prerequisites:
- Download and install Minecraft - java edition v1.19: use microsoft store
- Download [JDK version 17](https://adoptium.net/temurin/releases/?version=17)
- Download and install either IntelliJ (preferred), Eclipse, or Visual Studio Code
    - If using Eclipse you might need to [install a plugin](https://github.com/sebthom/extra-syntax-highlighting-eclipse-plugin) for editing json files with good syntax highlighting 
- Helpful to know Git for downloading tutorial files
- I would highly suggest a clipboard manager like the built in one to windows or Ditto
## Download Forge 1.19
Different options to get the forge files:
- Git clone from this repo using branch 2-BuildWithGradle
- Download Forge zip from my [google drive](https://drive.google.com/drive/folders/10EA8TrcMEiE2hjJkNC0sB3BwYUyGtYVj?usp=sharing)
- You can download other versions from [Forge](https://files.minecraftforge.net/net/minecraftforge/forge/) directly but it’s very spammy

After you get the files:
1. Unzip, rename, and put in workspace
2. Delete any .txt files
3. Open project with editor of choice (Eclipse needs File > Import > Gradle > Existing Gradle Project)
## Build With Gradle

Gradle might start building when opening project

![Gradle finished building](https://i.imgur.com/uN2mXkB.png)

Eclipse Gradle Build

![Eclipse Gradle Build](https://i.imgur.com/xx5C21y.png)

IntelliJ Gradle Build

![IntelliJ Gradle Tab](https://i.imgur.com/uBOPdai.png)
![GenIntelliJRuns](https://i.imgur.com/v0GXMjc.png)

Can run these from command line as well
```
./gradlew genEclipseRuns or ./gradlew genVSCodeRuns or ./gradlew genIntellijRuns
```

Then run *runClient*. You can hit Play after this instead of *runClient*

![Eclipse Gradle Run Client](https://i.imgur.com/FJOVrcn.png)

**Let's make sure we can get minecraft started before continuing.** This is the default example mod we will be replacing

![Minecraft running with Example Mod](https://i.imgur.com/r3OnICr.png)

## Introduction

- Developer
- Tinkerer
- Gardener
- Climber
- Cyclist
- Player of modded minecraft

Our mod is based on the zircon gem. You can replace that with whatever you'd like and make your own mod.

## Setting up IDE (IntelliJ)

### Check Java version
IntelliJ 
- File > Project Structure
![Project Structure](https://i.imgur.com/DqwbDZY.png)
- File > Settings > Build, Execution, Deployment > Build Tools > Gradle
![Gradle JDK](https://i.imgur.com/OnUD2ww.png)

### Tree Appearance
IntelliJ
- Right click on gear icon in left navigation menu > Tree Appearance > Unclick Flatten Packages and Compact Middle Packages
![Tree Appearance](https://i.imgur.com/nOLFizV.png)

## Building Our Mod
### The build.gradle file
In parent directory
1. Change version number
2. Change the group name
3. Change the Mod Id and ArchiveBaseName. **Mod Id must be all lowercase, can contain numbers, hyphen, and underscore, but no other special characters. Keep it simple!!**
4. Replace "examplemod" with "zirconmod"

### The ExampleMod.java file
In src > main > java > your naming convention > modid > ExampleMod.java
1. Delete lines 37 through 44. We'll be setting up these functions in other classes to have better organization

```
public static final DeferredRegister<Block> BLOCKS = DeferredRegister.create(ForgeRegistries.BLOCKS, MODID);
// Create a Deferred Register to hold Items which will all be registered under the "examplemod" namespace
public static final DeferredRegister<Item> ITEMS = DeferredRegister.create(ForgeRegistries.ITEMS, MODID);

// Creates a new Block with the id "examplemod:example_block", combining the namespace and path
public static final RegistryObject<Block> EXAMPLE_BLOCK = BLOCKS.register("example_block", () -> new Block(BlockBehaviour.Properties.of(Material.STONE)));
// Creates a new BlockItem with the id "examplemod:example_block", combining the namespace and path
public static final RegistryObject<Item> EXAMPLE_BLOCK_ITEM = ITEMS.register("example_block", () -> new BlockItem(EXAMPLE_BLOCK.get(), new Item.Properties().tab(CreativeModeTab.TAB_BUILDING_BLOCKS)));
```

2. Delete blocks and items regsiter
```
// Register the Deferred Register to the mod event bus so blocks get registered
BLOCKS.register(modEventBus);
// Register the Deferred Register to the mod event bus so items get registered
ITEMS.register(modEventBus);
```

3. Change the Mod Id
4. Rename file. Click on file and hit Shift + F6 or Right click > Refactor > Rename
![Renaming File](https://i.imgur.com/pj7J5Bj.png)
5. Change the package name from com.example.examplemod to your package name. Rename packages and delete out old packages

![Renaming Directories](https://i.imgur.com/La05Ir1.png)


### The mods.toml file
In src > main > resources > META-INF > mods.toml
1. Change license. MIT License suggested
2. Change modId
3. Change version
4. Change displayName
5. Come back to this file before you publish this for other people and flesh out the extra details to have better documentation

### Hit Play and Publish
1. Hit Play! You've got your own mod!!!
![Your Mod](https://i.imgur.com/VbAYUMo.png)
2. To build for publishing
    - Gradle tab > Tasks > build > build
    - or put this into the terminal 
```
./gradlew build
```
3. Find jar file in build > libs folder

## Adding our Zircon item
### The ModItems file
1. Add item package under zirconmod
2. Add ModItems.java file and add to git if using that
3. Add DeferredRegister ITEMS
    - Rememeber to hit tab to autofill and auto add imports
4. Register ITEMS on the eventBus
5. Register ModItems on the modEventBus in ZirconMod.java
6. Add RegistryObject ZIRCON
    - Can add more items by copying this line
    - Many many different properties to use to configure your items. We will come back to this
    - ![So many properties](https://i.imgur.com/c9yFidw.png)
7. Add RAW ZIRCON

### Adding asset directories to our Resources
1. Add directories to match this (might be easier to use File Explorer with Ctrl + Shift + N):
    - ![Asset directories](https://i.imgur.com/ayWIIiJ.png)
2. Add en_us.json in lang folder
    - Add zircon and raw zircon's display names
3. Add zircon.json in models > item folder
    - Configure texture
4. Add raw_zircon.json in same folder by copying it (select and hit F5)
5. Add texture files as png's:
    - Use those provided in this repo
    - Can make your own an online editor like [Nova Skin](https://minecraft.novaskin.me/resourcepacks)
    - Or use the External Libraries (Gradle: net.minecraft.client.extra > client-extra.jar > assets > minecraft > textures) and then use Paint, Gimp, etc to edit
        - ![Exteranl Libraries textures](https://i.imgur.com/Aw03Xxc.png)
