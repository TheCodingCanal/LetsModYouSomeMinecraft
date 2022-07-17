# Lets Mod You Some Minecraft
Minecraft is the beloved game by many kids and adults like me for doing almost anything you want in a low res world. The modding community took that idea even further and allowed players to do even more. I love playing modpacks like Feed The Beast that combine a bunch of great mods that give you the ability to cast magic with ruins, travel to other planes, make nuclear reactors, and so much more. Maybe you’ve thought about some cool stuff you’d like to have or do in minecraft to make it even more fun. Well now you can by making your own mod. We’re going to be making our own simple mod, which will set the stage for you to build your own blocks, crafting recipes, tools, armor, mobs, game rules, etc. There’s a lot that we need to do to get to the point of playing our mod and I will guide you step by step in this workshop.
## Zircon Mod
Based on Modding by Kaupenjoe’s [tutorial for v1.19 of Minecraft](https://www.youtube.com/watch?v=LpoSy091wYI&list=PLKGarocXCE1HrC60yuTNTGRoZc6hf5Uvl)

Prerequisites:

-   Download and install Minecraft - java edition v1.19: use microsoft store
    
-   Download [JDK version 17](https://adoptium.net/temurin/releases/?version=17)
    
-   Download and install either IntelliJ (preferred), Eclipse, or Visual Studio Code
## Download Forge 1.19
-   Download Forge zip from my [google drive](https://drive.google.com/drive/folders/10EA8TrcMEiE2hjJkNC0sB3BwYUyGtYVj?usp=sharing)
    
-   You can download other versions from [Forge](https://files.minecraftforge.net/net/minecraftforge/forge/) directly but it’s very spammy
    
-   Unzip, rename, and put in workspace
    
-   Open project with editor of choice
## Build With Gradle
Eclipse Gradle Build

![Eclipse Gradle Build](https://i.imgur.com/xx5C21y.png)

IntelliJ Gradle Build

![IntelliJ Gradle Tab](https://i.imgur.com/uBOPdai.png)
![GenIntelliJRuns](https://i.imgur.com/v0GXMjc.png)

Can run these from command line as well

    ./gradlew genEclipseRuns or ./gradlew genVSCodeRuns or ./gradlew genIntellijRuns

Then run *runClient*. You can hit Play after this instead of *runClient*

![Eclipse Gradle Run Client](https://i.imgur.com/FJOVrcn.png)

//TODO show screenshot of minecraft starting