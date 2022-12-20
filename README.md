# Quick start guide to modding Grand Theft Auto V
-------------------------------------------------

This is a quick and simple guide to the basics of installing and playing with mods on Grand Theft Auto V for Single Player. It won't cover MP mods like [FiveM](https://fivem.net/). 

Modding GTA:O or console games is not welcome here and will not be discussed.

Contents:

* [Setting things up](#setting-things-up)
* [Essentials](#essentials)
* [Downloading mods](#downloading-mods)
* [Installing mods](#installing-mods)
  * [Resource replacement mods (peds, vehicles, maps)](#resource-replacement-mods-peds-vehicles-maps)
  * [Resource add-on mods (peds, vehicles, maps)](#resource-add-on-mods-peds-vehicles-maps)
  * [.oiv files](#oiv-files)
  * [Scripts](#scripts)
* [Updating mods](#updating-mods)
* [Updating game](#updating-game)
  * [Backup / Reverting the update (downgrade game)](#backup--reverting-the-update-downgrade-game)
  * [Updating your mods](#updating-your-mods)
* [Disabling mods](#disabling-mods)
* [Troubleshooting](#troubleshooting)
  * [Common problems:](#common-problems)
  * [Things to pay attention to:](#things-to-pay-attention-to)
* [Contributing](#contributing)
* [Changelog](#changelog)

# Setting things up  
For a fresh start, you'll need the following things:  
* An updated, clean, unmodded, legit copy of Grand Theft Auto V (both Steam/Social Club are fine) that works normally
* An internet connection
* An archive manager. I recommend [7-Zip](http://www.7-zip.org/)
* Enable showing file extensions in Explorer
* Patience. __Read the manuals!__

It's best to start out with a clean, unmodded game, to prevent conflicts and instabilities. If you've tampered with the files, it's best to either re-install the game or to let Steam or Social Club verify your files before continuing. If you also had script mods installed and don't remember what to delete, just start out clean.

For reference, the following files enable loading and running mods from the normal launcher:

* dinput8.dll - ASI loader
* ScriptHookV.dll - Script hook
* OpenIV.asi - OpenIV archive loader

If you recognize any of these and don't exactly know why these are there, start out from scratch.

From now on, I'll refer to the GTA V installation folder as "`GTAV_root`". Where it's installed depends on where you got the game and your installation preferences. For example, the default folder for an install on Steam is `C:\Program Files (x86)\Steam\steamapps\common\Grand Theft Auto V`.

Finding it on Steam: `Library` -> Right-click Grand Theft Auto V -> `Manage` -> `Browse local files`
Rockstar Games and Epic Games sadly don't have an installation folder shortcut, so you'll need to find these on your own.

# Essentials
GTA V mods roughly exist in two distinct categories: resource mods and scripts. You'll need a couple of things to get this to work!

* [ScriptHookV](http://www.dev-c.com/gtav/scripthookv/) enables scripts for GTA V.
* [OpenIV](http://openiv.com/) enables modifying archives and adding archives.
* Optional: [ScriptHookVDotNet](https://github.com/crosire/scripthookvdotnet/releases) enables scripts written in .NET languages. It relies on ScriptHookV.
* Optional: [RAGE Plugin Hook](https://ragepluginhook.net/) is like ScriptHookVDotNet, but works standalone and uses a custom launcher for the game.

Download the archives or installers from the websites.

Installation: Follow the READMEs!
* ScriptHookV: Open the archive, extract the files inside the bin folder to your GTA V root.
* ScriptHookVDotNet: Open the archive, extract `ScriptHookVDotNet.asi` and `ScriptHookVDotNet2.dll` to your GTA V root.
* OpenIV: Run the installer. 

ScriptHookVDotNet has its scripts inside a separate folder inside the GTA V root folder, so create a `scripts` folder in there. `.dll` and `.cs` scripts you download will go in here.

OpenIV needs some additional setup. Run the program and point it to your GTA V directory if necessary. Go to Tools -> ASI Manager and install `ASI Loader` and `OpenIV.ASI` if they aren't installed already. You'll also want to [set up a `mods` folder](http://openiv.com/?p=1132). This keeps your original game files clean! As a start, put your `update.rpf` in the mods folder. You'll need to edit it anyway.

# Downloading mods 
It's a good idea to only download mods from trusted websites, especially script mods. Remember that scripts are just libraries and can execute any code. Mods that change textures, vehicles and the like are less risky, but always do your research before downloading mods from random websites.

Good resources are:
* [GTA5-Mods.com](https://www.gta5-mods.com/)
* [LCPDFR.com](https://www.lcpdfr.com/downloads/)
* [dev-c.com](http://www.dev-c.com/gtav/)
* [openiv.com](http://openiv.com/)

# Installing mods

## Resource replacement mods (peds, vehicles, maps)

If you download a mod that replaces an original resource, like a vehicle mod that replaces a default vehicle, you'll need to use OpenIV. The mod you download should have come with instructions with which file to replace in which exact folder and archive. __FOLLOW THOSE INSTRUCTIONS__.

## Resource add-on mods (peds, vehicles, maps)

If you download a mod that's marked as an add-on, it means it doesn't replace existing resources. They are added as DLCs. In general they follow the following set-up:  
* The data files are placed in `GTAV_root/mods/update/x64/dlcpacks/<mod name>/dlc.rpf`
* The entry is added to `dlclist.xml`. The exact location is `GTAV_root/mods/update/update.rpf/common/data/dlclist.xml`. This entry looks like `<Item>dlcpacks:\myCoolModName\</Item>`

When adding an entry to `dlclist.xml`, take care to keep the opening and closing tags are __exactly__ `Item`. If they are different, the file is invalidated. 

Some mod authors also tell you to change `extratitleupdatedata.meta`, but this is __NOT__ necessary! 

You also need to install the following tools, as they are required to make the game deal with loading more resources:

* [gameconfig.xml](https://www.gta5-mods.com/search/gameconfig) (Recommended: [pnwparkfan's version](https://github.com/pnwparksfan/gameconfig))
* [Heap Adjuster](https://www.gta5-mods.com/tools/heapadjuster)
* [Packfile Limit Adjuster](https://www.gta5-mods.com/tools/packfile-limit-adjuster)

### What version am I running?

There are two versions, the GTA: Online version and the executable version. ScriptHookV, ScriptHookVDotNet, RagePluginHook and most version-dependent mods (scripts) use the executable version. You can find this by right-clicking the `GTA5.exe` file and checking the Details Tab -> File Version. As of writing, the version is `1.0.2802.0`.

Some scripts only work for specific game versions. After the game updates, you might need to check back on the mod page for possibly updates.

## .oiv files

If you download a mod that ends with `.oiv`, this means the mod author prepared a nice package for you. If you installed OpenIV properly, you can just double click the file, after which an OpenIV pacakge installation prompt will open. Check any information in the description window and press install. These mods can add files and/or __replace files__, so be sure to double-check if you've got the correct package.

**Be aware** that `.oiv` don't have an uninstall option, so check if the mod you want to install has its own uninstaller or uninstall instructions. In the worst case, you can open the `.oiv` archive with something like 7-zip, and check `assembly.xml` for the files that are replaced.

## Scripts

Scripts add various extra functionality to the game, like missions, expanded or new functionality, trainers and much more. Scripts need their respective library to load properly. If you download a script, it will usually say for which library it is made.

Some scripts come with additional configuration files. Extract these files according to the readme of the script.

### ScriptHookV: .asi files

Scripts ending with the `.asi` extension are ScriptHookV scripts and go in the main GTA V folder.

Note: Some `.asi` files do not require ScriptHookV, like `OpenIV.asi`. `dinput8.dll` can load them without `ScriptHookV.dll`.

### ScriptHookVDotNet: .dll, .cs, .vb

Scripts ending with the `.dll`, `.cs` and `.vb` extensions are usually ScriptHookVDotNet mods and go in the `GTAV_root/scripts/` folder.

### RAGEPluginHook: .dll

RAGEPluginHook go in the `GTAV_root/Plugins/` folder.

# Updating mods

For most resource mods, you should just reinstall the mod completely by using the new files.

For scripts, you should take note of the changelog or other comments the author had. Usually it suffices to just replace the `.asi`/`.dll`/`.cs`, but sometimes the configuration files also need replacement.

# Updating game

Rockstar releases new DLC from time to time. Some mods keep working, others break. Here are some basic steps to prepare for, and prevent your game from breaking, or to get back up and running quickly!

## Backup / Reverting the update (downgrade game)
__BEFORE__ a new DLC update drops, Rockstar announces it on their social media and news channels. Once a new DLC is announced, ensure you have a backup of the following files:

* `GTAV_root/update/update.rpf`
* `GTAV_root/update/update2.rpf`
* `GTAV_root/GTA5.exe`
* `GTAV_root/GTAVLauncher.exe`

It's smart to label these. I put them in a folder with the executable version. For Smuggler's Run, this is `v1.0.1180.2`. When the next update drops and you want to revert, back up the new files and replace them with your old backups.

## Updating your mods
You can also choose to update your mods. In general it's a good idea to wait until some core resources (ScriptHookV, ScriptHookVDotNet) have been updated to the new game version.

### Resource mods
Each update, you'll need to update your `GTAV_root/mods/update/update.rpf` to match the version of `GTAV_root/update/update.rpf`. You can then transplant your changes from your old modded `update.rpf` to the new `update.rpf`.

Things to pay attention to:
* The new `dlclist.xml` probably has a new entry, so take care copy-pasting your modded `dlclist.xml` if you want to play with the new DLC content. Some mods also require new DLC content.
* `gameconfig.xml` is very version-dependent. If you use add-on mods, it's __very__ likely you'll need to update `gameconfig.xml` that supports add-ons.
* Some replacement mods might not work after updating. In this case, the new update package overwrites old changes. (Rockstar sometimes fixes older content)

### Script mods
__Most__ scripts rely on ScriptHookV and just use natives. These will work after ScriptHookV gets updated for the new update, and won't need updating themselves.

ScriptHookVDotNet uses offsets for peds and vehicles, so it's wise to wait until ScriptHookVDotNet gets an update to support the new update. __Most__ ScriptHookVDotNet scripts don't need updating themselves.

If a script crashes after an update, just disable it and keep an eye on the mod page. The author may update the script in the (near) future. It may help to notify the script author, though they usually are aware already.

# Disabling mods

GTA5-Mods.com does not support playing GTA: Online on a modded installation, and this is prohibited by Rockstar.

That being said, if you installed resource mods using the `mods` folder feature from OpenIV, you can quickly disable all mods.

Moving or renaming `dinput8.dll` to something else, will stop all `.asi` files from loading. This means all scripts, ScriptHookV, ScriptHookVDotNet and OpenIV won't load, and you should be able to load into GTA: Online, provided you are running the latest game version and no original files have been changed.

*Be aware that visual mods like ENB, Reshade come with `d3d11.dll`, which may be blocked. Also rename this `d3d11.dll` to something else for a "clean" install.*

# Troubleshooting

Outside of the common update woes, things can of course go wrong. Here are a few common things that go wrong:

## Common problems:

### DLC Vehicles disappear when spawning
Rockstar disables MP cars in SP. Most trainers will fix this after an update.

* [Add-On Vehicle Spawner](https://www.gta5-mods.com/scripts/add-on-vehicle-spawner) automatically enables MP vehicles in SP.
* [Enhanced Native Trainer](https://www.gta5-mods.com/scripts/enhanced-native-trainer-zemanez-and-others) also does this.
* [Simple Trainer](https://www.gta5-mods.com/scripts/simple-trainer-for-gtav) also works, but needs to be updated after each patch.
* [Menyoo](https://github.com/MAFINS/MenyooSP/releases) also works, but needs to be updated after each patch.

### Infinite loading screen or crash during loading
You probably installed a mod pack with many vehicles or manually installed too many vehicles. This is related to `gameconfig.xml` and you should find [a replacement `gameconfig`](https://www.gta5-mods.com/search/gameconfig). Also don't forget the heap adjuster!

### Crashing upon full screen
If you're crashing whilst attempting to full screen your game or exiting full screen, this is mostly caused by Reshade not being configured correctly, and thus will be set to inject into the wrong DX version (should be 11). If the reshade `.dll` name is anything other than `dxgi.dll` , `d3d11.dll` or `ReShade.dll`, you're targeting the wrong version of DirectX, even if in-game you're running DX9 or 10. To fix this download the [Reshade Binary](https://reshade.me/) and target `GTA5.exe` with DX version 11. After this to ensure compatibility with Boris Vorontsov's ENB, change the `ProxyLibrary` value in `enblocal.ini` to reflect the respective ReShade dll which has just been created in the root game directory. 

### Vanilla vehicle spawning upon replacing said vehicle
A simple solution to fix replacement of vanilla vehicles, especially for old mods, is to use the search function in OpenIV (`CTRL+F3`) and search for the respective vehicle yft, and consequently replace the one in the most recent dlcpack. If you are not sure about the order in which some DLC packs were added, you can sort them by date modified.

### `ERR_FIL_PACK_1`
GTA V throws this error when game memory allocation runs out, specifically when attempting to load too many DLC packs. You can fix this by, if you haven't already, installing a custom `gameconfig.xml` , or else use [Heap Adjuster](https://www.gta5-mods.com/tools/heap-limit-adjuster-600-mb-of-heap). If however you have already used both these methods. you can remove some, or [merge dlc's (guide)](https://forums.gta5-mods.com/topic/222/tutorial-vehicles-weapons-how-to-do-add-on-s-replacer-s).

### `ERR_STR_FAILURE_3`
GTA V throws this error in most cases upon spawning an object which references a null entry or when the engine is told to stream an object greater than the max value. As this is mostly a problem when trying to spawn vehicles, you can fix this by reducing the total poly count for the vehicle, modifying the base value of the vehicle in Zmodeler3 or reducing the amount of materials that the car has. Also getting rid of any embedded textures on the yft can sometimes solve this issue.

### `ERR_MEM_EMBEDALLOC_GUARD_1'`
GTA V throws this error when the engine's memory allocator cannot provide enough memory to store a singular or multiple objects. As this is mostly a problem with script mods, you can attempt to fix this by ensuring that said script is not creating too many entities.

### Crashing on entering a vehicle
There's a wrong reference to the vehicle handling and/or layout. Check `vehicles.meta` for the correct references. 

### Crash on startup with error on corrupt files
You're not using a mods folder and/or referring to non-imported files in `content.xml`. As OpenIV.asi disables the checking of game file integrity, any message referring to corrupt game files means that either Scripthook V or OpenIV.asi is missing.

### Others
You might want to [check this thread](https://forums.gta5-mods.com/topic/4949/readme-frequently-asked-questions-installation-help-troubleshooting).

## Things to pay attention to:

### Mod packs
Mod packs can add lots of resources. Usually when installing mod packs, it's necessary to get a `gameconfig` that allows many add-ons. Examples of big mod packs:  
* [Realism Dispatch Enhanced](https://www.gta5-mods.com/misc/realism-dispatch-enhanced)
* [IVPack](https://www.gta5-mods.com/vehicles/ivpack-gtaiv-vehicles-in-gtav)
* [VanillaWorks Extended](https://www.gta5-mods.com/vehicles/vanillaworks-extended-pack-add-on-oiv-tuning-liveries-vanillaworks-and-other-modders)

A small note about "Redux": This is/was mainly composed of resources taken without permission from various mod authors. The community will be hesitant or unwilling to support games with a Redux installation.

### LODs  
[Level of detail](https://en.wikipedia.org/wiki/Level_of_detail) is important for performance and appearance. Some vehicle mods have no good LODs, thus will either require a lot of performance even at a distance, or have a disappearing body. Take care installing these mods, especially if they are replacements. Your framerate can suffer significantly, no matter how good your computer is!

### Scripts  
Scripts can be unstable, either due to updates or due to how they are written. If the script crashes, this will usually be caught by the hook or runtime.

A ScriptHookV crash will show an error window before closing the game. Write down the crashing script and contact the author. If you do, please provide logs: 
* `ScriptHookV.log`
* Any other logs the script might have generated

A ScriptHookVDotNet script crash is silent. The script just doesn't work any more. As with ScriptHookV scripts, report this to the author. Provide:  
* `ScriptHookVDotNet2.log`
* Any other logs the script might have generated

# Contributing
Suggestions are welcome! You can make an [issue on this repository](https://github.com/E66666666/GTAVBasicModdingGuide), or poke me on the GTA5-Mods.com Discord server.

# Changelog
2020-05-21: Removed broken "MP Vehicles in SP" and add Sjaak's TrainerV.
2021-03-12: Added "What's my game version?"
2021-04-17: Clarified "GTAV_root"
2021-04-19: Added required tools for add-ons
2022-12-20: Added Packfile Limit Adjuster to tools, and LCPDFR as safe website