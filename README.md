# As of 1/31/2025 this repository is archived
Gorilla Tag has released an update that
- A. Breaks this repository
- B. Adds official custom gamemode support

Though the custom gamemodes they have are confined to the virtual stump I said that I would stop updating this when they added custom gamemodes and I want to move away from this game and it's community ASAP.

If you need an alternative, I'd recommend [Dev's fix of the original Utilla](https://github.com/Developer9998/Utilla).

#
![378217004-09f8e32f-22f7-422b-be3c-4cf276b1527b](https://github.com/user-attachments/assets/1736c692-0d27-46ca-b862-9eae41d56b7a)

Original mod by [legoandmars](https://github.com/legoandmars/Utilla).

# Newtilla
A stable rewrite of Utilla that updates dynamically using mostly harmony patches, this version should be less prone to breaking and is much simpler.

# Installation
First, download [Newtilla](https://github.com/Loafiat/Newtilla/releases) and put that in your plugins. Optionally, you can download the original [Utilla](https://github.com/legoandmars/Utilla) aswell, I'd recommend it as most mods won't work without it. Your done, enjoy!

# Examples:

Mod support example:
```cs
using BepInEx;
using Newtilla;

public class TestMod : BaseUnityPlugin
{
    void Start()
    {
        //These events will run when a modded is joined or left.
        Newtilla.Newtilla.OnJoinModded += OnModdedJoined;
        Newtilla.Newtilla.OnLeaveModded += OnModdedLeft;
    }

    void OnModdedJoined(string modeName)
    {
        //Run mod init
    }

    void OnModdedLeft(string modeName)
    {
        //Run mod deinit
    }
}

```

Custom game mode example:
```cs
using BepInEx;
using Newtilla;

public class TestMod : BaseUnityPlugin
{
    void Start()
    {
        //This creates and adds the mode to the mode selector, OnModeJoined and OnModeLeft aren't required.
        Newtilla.Newtilla.AddGameMode("TESTMODE", "TESTMODE", BaseGamemode.HUNT, false, OnModeJoined, OnModeLeft);
    }

    void OnModeJoined()
    {
        //Run mode init stuff
    }

    void OnModeLeft()
    {
        //Run mode deinit stuff
    }
}
```
Advanced game mode example:
```cs
using BepInEx;
using Newtilla;

public class TestMod : BaseUnityPlugin
{
    void Start()
    {
        //This creates and adds the mode to the mode selector, the base gamemode is replaced with "GHOST" here.
        //This is because it's a temporary gamemode so it's not included by default to avoid issues in the future
        //currently "AMBUSH" works too.
        Newtilla.Newtilla.AddGameMode("TESTMODE", "TESTMODE", "GHOST", false, OnModeJoined, OnModeLeft);
    }

    void OnModeJoined()
    {
        //Run mode init stuff
    }

    void OnModeLeft()
    {
        //Run mode deinit stuff
    }
}
```
