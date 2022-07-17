# Lets Mod You Some Minecraft

Minecraft is the beloved game by many kids and adults like me for doing almost anything you want in a low res world. The modding community took that idea even further and allowed players to do even more. I love playing modpacks like Feed The Beast that combine a bunch of great mods that give you the ability to cast magic with ruins, travel to other planes, make nuclear reactors, and so much more. Maybe you’ve thought about some cool stuff you’d like to have or do in minecraft to make it even more fun. Well now you can by making your own mod. We’re going to be making our own simple mod, which will set the stage for you to build your own blocks, crafting recipes, tools, armor, mobs, game rules, etc. There’s a lot that we need to do to get to the point of playing our mod and I will guide you step by step in this workshop.

## Zircon Mod
Based on Modding by Kaupenjoe’s [tutorial for v1.19 of Minecraft](https://www.youtube.com/watch?v=LpoSy091wYI&list=PLKGarocXCE1HrC60yuTNTGRoZc6hf5Uvl)

**We're going to jump into the tutorial so we can get everything running and downloading while I give my intro**

Prerequisites:
- Download and install Minecraft - java edition v1.19: use microsoft store
- Download [JDK version 17](https://adoptium.net/temurin/releases/?version=17)
- Download and install either IntelliJ (preferred), Eclipse, or Visual Studio Code
- Helpful to know Git for downloading tutorial files
- I would highly suggest a clipboard manager like the built in one to windows or Ditto
## Download Forge 1.19

-   Download Forge zip from my [google drive](https://drive.google.com/drive/folders/10EA8TrcMEiE2hjJkNC0sB3BwYUyGtYVj?usp=sharing)
-   You can download other versions from [Forge](https://files.minecraftforge.net/net/minecraftforge/forge/) directly but it’s very spammy
- Unzip, rename, and put in workspace
- Delete any .txt files
- Open project with editor of choice (Eclipse needs File > Import > Gradle > Existing Gradle Project)
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
- In parent directory
- Change version number
- Change the group name
- Change the Mod Id and ArchiveBaseName. **Mod Id must be all lowercase, can contain numbers, hyphen, and underscore, but no other special characters. Keep it simple!!**
- Replace "examplemod" with "zirconmod"

### The ExampleMod.java file
- In src > main > java > your naming convention > modid > ExampleMod.java
- Delete lines 37 through 44. We'll be setting up these functions in other classes to have better organization

```
public static final DeferredRegister<Block> BLOCKS = DeferredRegister.create(ForgeRegistries.BLOCKS, MODID);
// Create a Deferred Register to hold Items which will all be registered under the "examplemod" namespace
public static final DeferredRegister<Item> ITEMS = DeferredRegister.create(ForgeRegistries.ITEMS, MODID);

// Creates a new Block with the id "examplemod:example_block", combining the namespace and path
public static final RegistryObject<Block> EXAMPLE_BLOCK = BLOCKS.register("example_block", () -> new Block(BlockBehaviour.Properties.of(Material.STONE)));
// Creates a new BlockItem with the id "examplemod:example_block", combining the namespace and path
public static final RegistryObject<Item> EXAMPLE_BLOCK_ITEM = ITEMS.register("example_block", () -> new BlockItem(EXAMPLE_BLOCK.get(), new Item.Properties().tab(CreativeModeTab.TAB_BUILDING_BLOCKS)));
```

- Delete blocks and items regsiter
```
// Register the Deferred Register to the mod event bus so blocks get registered
BLOCKS.register(modEventBus);
// Register the Deferred Register to the mod event bus so items get registered
ITEMS.register(modEventBus);
```

- Change the Mod Id
- Rename file. Click on file and hit Shift + F6 or Right click > Refactor > Rename
![Renaming File](https://i.imgur.com/pj7J5Bj.png)
- Change the package name from com.example.examplemod to your package name. Rename directories and delete out old directories

![Renaming Directories](https://i.imgur.com/La05Ir1.png)


### The mods.toml file
- In src > main > resources > META-INF > mods.toml
- Change license. MIT License suggested
- Change modId
- Change version
- Change displayName
- Come back to this file before you publish this for other people and flesh out the extra details to have better documentation

### Hit Play and Publish
- Hit Play! You've got your own mod!!!
![Your Mod](https://i.imgur.com/VbAYUMo.png)
- To build for publishing
    - Gradle tab > Tasks > build > build
    - or put this into the terminal 
```
./gradlew build
```
- Find jar file in build > libs folder
