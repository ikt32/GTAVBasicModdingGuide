# Quick start guide to modding Grand Theft Auto V
-------------------------------------------------

This is a quick and simple guide to the basics of installing and playing with mods on Grand Theft Auto V for Single Player. It won't cover MP mods like [FiveM](https://fivem.net/), or [script hooks that start the game with a custom launcher](https://ragepluginhook.net/). Modding GTA:O is not welcome here and will not be discussed. Neither is modding for consoles, the only supported platform is PC.

# Table of Contents
<!-- TOC depthFrom:1 depthTo:2 orderedList:false updateOnSave:true withLinks:true -->

- [Quick start guide to modding Grand Theft Auto V](#quick-start-guide-to-modding-grand-theft-auto-v)
- [Table of Contents](#table-of-contents)
- [Setting things up](#setting-things-up)
- [Must-haves](#must-haves)
- [Downloading mods](#downloading-mods)
- [Installing mods](#installing-mods)
    - [Resource replacement mods (peds, vehicles, maps)](#resource-replacement-mods-peds-vehicles-maps)
    - [Resource add-on mods (peds, vehicles, maps)](#resource-add-on-mods-peds-vehicles-maps)
    - [.oiv files](#oiv-files)
    - [Scripts: .asi](#scripts-asi)
    - [Scripts: .dll, .cs, .vb](#scripts-dll-cs-vb)
- [Updating mods](#updating-mods)
- [Updating game](#updating-game)
    - [Disabling all mods](#disabling-all-mods)
    - [Reverting the update (downgrade game)](#reverting-the-update-downgrade-game)
    - [Updating your mods](#updating-your-mods)
- [Troubleshooting](#troubleshooting)
    - [Common problems:](#common-problems)
    - [Things to pay attention to:](#things-to-pay-attention-to)
- [Credits and authors](#credits-and-authors)
- [Contributing](#contributing)

<!-- /TOC -->

# Setting things up  
For a fresh start, you'll need the following things:  
* An updated, clean, unmodded, legit copy of Grand Theft Auto V (both Steam/Social Club are fine) that works normally
* An internet connection
* An archive manager. I recommend [7-Zip](http://www.7-zip.org/)
* Enable showing file extensions in Explorer
* Patience. Read the manuals!

It's best to start out with an unmodded game, to prevent things from conflicting or having other instabilities. If you've tampered with the files, it's best to either re-install the game or to let Steam or RGSC verify your files before continuing. If you also had script mods installed and don't remember what to delete, just start out clean.

For reference, the following files enable loading and running mods from the normal launcher:

* dinput8.dll - ASI loader
* ScriptHookV.dll - Script hook
* OpenIV.asi - OpenIV archive loader

If you recognize any of these and don't exactly know why these are there, start out from scratch.

# Must-haves
GTA V mods roughly exist in two distinct categories: resource mods and scripts. You'll need a couple of things to get this to work!

* [ScriptHookV](http://www.dev-c.com/gtav/scripthookv/) enabled scripts for GTA V.
* [OpenIV](http://openiv.com/) enables modifying archives and adding archives.
* [ScriptHookVDotNet](https://github.com/crosire/scripthookvdotnet/releases) enables scripts written in .NET languages. It relies on ScriptHookV.

Download the archives or installers from the websites.

Installation: Basically just follow the instructions!
* ScriptHookV: Open the archive, extract the files inside the bin folder to your GTA V root.
* ScriptHookVDotNet: Open the archive, extract `ScriptHookVDotNet.asi` and `ScriptHookVDotNet2.dll` to your GTA V root.
* OpenIV: Run the installer. 

ScriptHookVDotNet has its scripts inside a separate folder inside the GTA V root folder, so create a `scripts` folder in there. `.dll` and `.cs` scripts you download will go in here.

OpenIV needs some additional setup. Run the program and point it to your GTA V directory if necessary. Go to Tools -> ASI Manager and install `ASI Loader` and `OpenIV.ASI` if they aren't installed already. You'll also want to [set up a `mods` folder](http://openiv.com/?p=1132). This keeps your original game files clean! As a start, put your `update.rpf` in the mods folder. You'll need to edit it anyway.

# Downloading mods 
It's a good idea to only download mods from trusted websites, especially script mods. Remember that scripts are just libraries and can execute any code. Mods that change textures, vehicles and the like are less risky, but always do your research before downloading mods from random websites.

Good resources are:
* [GTA5-Mods.com](https://www.gta5-mods.com/)
* [dev-c.com](http://www.dev-c.com/gtav/)
* [openiv.com](http://openiv.com/)

# Installing mods

## Resource replacement mods (peds, vehicles, maps)

If you download a mod that replaces an original resource, like a vehicle mod that replaces a default vehicle, you'll need to use OpenIV. The mod you download should have come with instructions with which file to replace in which exact folder and archive. __FOLLOW THOSE INSTRUCTIONS__.

## Resource add-on mods (peds, vehicles, maps)

If you download a mod that's marked as an add-on, it means it doesn't replace existing resources. They are added as DLCs. In general they follow the following set-up:  
* The data files are placed in `GTAV_root/mods/update/x64/dlcpacks/<mod name>/dlc.rpf`
* The entry is added to `dlclist.xml`. The exact location is `GTAV_root/mods/update/update.rpf/common/data/dlclist.xml`. This entry looks like `<Item>dlcpacks:\<mod name>\</Item>`

When adding an entry to `dlclist.xml`, take care to keep the opening and closing tags being __exactly__ `Item`. If they are different, the file is invalidated. 

Some mod authors also tell you to change `extratitleupdatedata.meta`, but this is __NOT__ necessary! 

Additionally, you'll want to replace `GTAV_root/mods/update/update.rpf/common/data/gameconfig.xml` with a version that supports more add-on mods. These can be [obtained on GTA5-Mods.com](https://www.gta5-mods.com/search/gameconfig). Just take care to pick the correct game version files.

## .oiv files

If you download a mod that ends with `.oiv`, this means the mod author prepared a nice package for you. If you installed OpenIV properly, you can just double click the file, after which an OpenIV pacakge installation prompt will open. Check any information in the description window and press install. These mods can add files and/or __replace files__, so be sure to double-check if you've got the correct package.

## Scripts: .asi

Scripts ending with the `.asi` extension are ScriptHookV scripts and __ALWAYS__ go in the GTA V root directory. If the script came with configuration files, follow the installation instructions for that script. Usually the archives are made so you just select the asi and the additional folder or the additional config files and put those directly in your game root directory.

## Scripts: .dll, .cs, .vb

Scripts ending with the `.dll`, `.cs` and `.vb` extensions are ScriptHookVDotNet mods and __ALWAYS__ go in `GTAV_root/scripts/`. As with `.asi` mods, you want to follow the instructions.

# Updating mods

For most resource mods, you should just reinstall the mod completely by using the new files.

For scripts, you should take note of the changelog or other comments the author had. Usually it suffices to just replace the `.asi`/`.dll`/`.cs`, but sometimes the configuration files also need replacement.

# Updating game

Rockstar releases new DLC from time to time. Some mods keep working, other break. Here's a basic guide of steps to take to prevent this, or to get back up and running quickly!

## Disabling all mods
Moving or renaming `dinput8.dll` will stop ScriptHookV, ScriptHookVDotNet and OpenIV from loading. If you properly used OpenIV's mod folder, this disables all mods and you should be able to play the unmodded game and even join a GTA:O session.

## Reverting the update (downgrade game)
__BEFORE__ a new DLC update drops, Rockstar hypes it up. Once a new DLC is announced, ensure you have a backup of the following files

* `GTAV_root/update/update.rpf`
* `GTAV_root/GTA5.exe`
* `GTAV_root/GTAVLauncher.exe`
* `steam_api64.dll`

It's smart to label these. I put them in a folder with the executable version. For Smuggler's Run, this is `v1.0.1180.2`. When the next update drops and you want to revert, back up the new files and replace them with your old backups.

## Updating your mods
You can also choose to update your mods. In general it's a good idea to wait until some core resources (ScriptHookV, ScriptHookVDotNet) have been updated to the new game version.

### Resource mods
Each update, you'll need to update your `GTAV_root/mods/update/update.rpf` to match the version of `GTAV_root/update/update.rpf`. You can then transplant your changes from your old modded `update.rpf` to the new `update.rpf`.

Things to pay attention to:
* The new `dlclist.xml` probably has a new entry, so take care copy-pasting your modded `dlclist.xml`.
* `gameconfig.xml` is very version-dependent. If you use add-on mods, it's __very__ likely you'll need to wait for a new updated `gameconfig.xml` that supports add-ons.
* Some replacement mods might not work after updating. In this case, the new update package overwrites old changes. (Rockstar sometimes fixes old models)

### Script mods
__Most__ scripts rely on ScriptHookV and just use natives. These will work after ScriptHookV gets updated for the new update, and won't need updating themselves.

ScriptHookVDotNet uses offsets for peds and vehicles, so it's wise to wait until ScriptHookVDotNet gets an update to support the new update. __Most__ ScriptHookVDotNet scripts don't need updating themselves.

If a script crashes after an update, just disable it and keep an eye on the mod page. The author might update the script in the coming hours/days/weeks/months/years. It might help to notify the script author.


# Troubleshooting

Outside of the common update woes, things can of course go wrong. Here are a few common things that go wrong:

## Common problems:

### Infinite loading screen
You probably installed a mod pack with many vehicles or manually installed many vehicles. This is related to `gameconfig.xml` and you should find [a replacement `gameconfig`](https://www.gta5-mods.com/search/gameconfig).

### Crashing upon full screen
If you're crashing whilst attempting to full screen your game or exiting full screen, this is mostly caused by Reshade not being configured correctly, and thus will be set to inject into the wrong DX version (should be 11). If the reshade ```.dll``` name is anything other than ```dxgi.dll``` , ```d3d11.dll``` or ```ReShade.dll```, you're targeting the wrong version of DirectX, even if in-game you're running DX9 or 10. To fix this download the [Reshade Binary](https://reshade.me/) and target ```GTA5.exe``` with DX version 11. After this to ensure compatibility with Boris Vorontsov's ENB, change the ```ProxyLibrary``` value in ```enblocal.ini``` to reflect the respective ReShade dll which has just been created in the root game directory. 

### `ERR_FIL_PACK_1`
GTA V throws this error when game memory allocation runs out, specifically when attempting to load too many DLC packs. You can fix this by, if you haven't already, installing a custom ```gameconfig.xml``` , or else use [Heap Adjuster](https://www.gta5-mods.com/tools/heap-limit-adjuster-600-mb-of-heap). If however you have already used both these methods. you can remove some, or [merge dlc's (guide)](https://forums.gta5-mods.com/topic/222/tutorial-vehicles-weapons-how-to-do-add-on-s-replacer-s).

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

A small note about "Redux": This is mainly composed of resources stolen from various mod authors. You won't find much support for an unstable game with Redux. Be a nice person and avoid that stolen mess :)

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

# Credits and authors

* ikt
* Eddlm
* ReNNie

# Contributing
Suggestions in any form are welcome :) You can make a [pull request on the repo](https://github.com/E66666666/GTAVBasicModdingGuide) or just comment.
