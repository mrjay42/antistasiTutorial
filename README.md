# How to install Antistasi The Mod on Linux dedicated server

The version of Antistasi we're talking about are those ones:

**Antistasi The Mod** 

- [Official Antistasi Community Edition Wiki - Antistasi Guide documentation](https://official-antistasi-community.github.io/A3-Antistasi-Docs/index.html)

- [GitHub - official-antistasi-community/A3-Antistasi: Antistasi Community Version](https://github.com/official-antistasi-community/A3-Antistasi)

- [Steam Workshop::Antistasi - The Mod](https://steamcommunity.com/sharedfiles/filedetails/?id=2867537125)

**Antistasi PLUS**

- https://github.com/igorkis-scrts/A3-Antistasi-Plus/releases/

# Introduction

**This tutorial assumes you know your way around Linux**

This tutorial assumes you'll be using LGSM to install Arma 3 server

*LGSM is linked below in the first chapter*

Also this is a MANUAL installation, I won't be using the Steam Workshop

## Plan

1. First you need a running Arma 3 server ->

2. Second we'll install Antistasi

3. Third we'll make it run on your gaming computer

This has been tested on Ubuntu 20.04 and Debian

# Installing Arma 3 dedicated server on Linux

The easiest thing to do is to follow the tutorial here:

The tutorial I use:

[ARMA 3 | LinuxGSM_](https://linuxgsm.com/servers/arma3server/)

*Another one, that I like less, but just in case, there you go:*

*[Arma 3 - LinuxGSM_](https://docs.linuxgsm.com/game-servers/arma-3)*

### Correcting a mistake in the LGSM Arma 3 Server tutorial

In the LGSM ([ARMA 3 | LinuxGSM_](https://linuxgsm.com/servers/arma3server/)) tutorial the authors tell you to edit this file:

`nano lgsm/config-lgsm/arma3server/common.cfg`

Which is a mistake: because at that point, that file does not exist yet!!

At that point, instead you should do this:
`./arma3server install`

Follow the instructions AND the install IS GONNA CRASH, telling you that you MUST set your Steam credentials and NOW and only NOW you can edit the aforementioned file, because NOW the file exists!

So only NOW you can actually do:

`nano lgsm/config-lgsm/arma3server/common.cfg`

My `common.cfg` file looks like this:
```
##################################
######## Common Settings #########
##################################
# PLACE GLOBAL SETTINGS HERE
## These settings will apply to all instances.
steamuser="mySteamLogin"
steampass='mySteamPassword'
stats="on"

startparameters="-ip=${ip} -port=${port} -cfg=${networkcfgfullpath} -config=${servercfgfullpath} -mod=${mods} -servermod=${servermods} -bepath=${bepath} -loadmissiontomemory -cpuCount=4 -enableHT"
```
Obviously you're supposed to replace `mySteamLogin` and `mySteamPassword` with the correct values

---

Basically at the end of the LinuxGSM tutorial, you should have a "arma3server" user on your Linux machine.

In the `/home/arma3server/` folder you should have a bunch of files and directories:

```bash
-rwxrwxr-x  1 arma3server arma3server 19088 Feb 22 00:26 arma3server*
drwx---r-x  2 arma3server arma3server  4096 Jan  1  2022 .cache/
drwx------  4 arma3server arma3server  4096 Feb 21 16:47 .config/
-rw-------  1 arma3server arma3server    41 Feb 27  2022 .lesshst
drwxrwxr-x  9 arma3server arma3server  4096 Jan  1  2022 lgsm/
-rwxrwxr-x  1 arma3server arma3server 18646 Oct  3  2021 linuxgsm.sh*
drwxrwxr-x  3 arma3server arma3server  4096 Oct  3  2021 .local/
drwxrwxr-x  4 arma3server arma3server  4096 Oct  3  2021 log/
-rw-r--r-x  1 arma3server arma3server   807 Oct  3  2021 .profile*
drwxr-xr-x 23 arma3server arma3server  4096 Apr 30 17:26 serverfiles/
drwxrwxr-x  5 arma3server arma3server  4096 Apr 28 19:23 .steam/
```

I removed on purpose useless files and directories from this list, but you surely will have other random stuff that is part of any modern Linux user directory (such as: `.bashrc`, etc.)

# How to install Antistasi The Mod On Linux

In this tutorial I'm doing a FULLY manual install of the mod.

You can, if you want, find your way around with subscription system on Steam, but it's not covered in this tutorial; reason is: if you know how to do things manually, you're always more free than someone relying on automated mechanisms.

## Where do I download the mod?

First get the Antistasi The Mod files, as we are doing a manual install, we're gonna download the latest release from the mod's Github:

Go there: [Releases · official-antistasi-community/A3-Antistasi · GitHub](https://github.com/official-antistasi-community/A3-Antistasi/releases)

Scroll down and you should see, for the latest release (always at the top of the page), the "Assets" section, there, there should be an archive file. At the date of writing this tutorial the latest release is available at this address: https://github.com/official-antistasi-community/A3-Antistasi/releases/download/3.1.0/@Antistasi.-.The.Mod.rar

### To Download Antistasi Plus 

- https://github.com/igorkis-scrts/A3-Antistasi-Plus/releases/

## How to download the mod

**Starting from here, the names of the downloaded files may vary, please rely on Linux autocompletion and your own judgment to adapt the command lines written below to your own case**

To do the whole thing in the command line you can do like this

Let's assume you're now in `/home/arma3server`

Let's create a new directory called antistasiSource: 

`mkdir antistasiSource`

Let's enter the directory

`cd antistasiSource`

Let's download the rar file

`wget https://github.com/official-antistasi-community/A3-Antistasi/releases/download/3.1.0/@Antistasi.-.The.Mod.rar`

So you'll have a .rar file, let's see in the next section what to do with it 

### For Antistasi Plus

`wget https://github.com/igorkis-scrts/A3-Antistasi-Plus/releases/download/v2.3.2/A3A-Plus.zip`

Note: this link is pointing to the latest version available at the date of writing this tutorial


## Renaming and extracting the mod

Ok you have your .rar file

### Extracting

#### If you have a rar file

On linux to extract your rar file I invite you to install the package called `rar` (probably something akin to `sudo apt install rar`, if you type `rar`in your Linux command and you get an error message, I suggest that you simply look up on the internet "*Linux how to extract rar file*")

If everything is in place then you should do

`rar x @Antistasi.-.The.Mod.rar`

#### if you have a zip file

`unzip yourFile.zip -d @antistasi`

if you don't have unzip -> `sudo apt install zip`

#### if you have a 7z file

`7za x yourfile.7z`

if you don't have unzip -> `sudo apt install p7zip-full`

### Renaming

Let's rename the newly created folder into:

`mv @Antistasi\ -\ The\ Mod/ @antistasi`

So now you should have a directory in `/home/arma3server/antistasiSource/` that is called`@antistasi`

*You may wonder: why did we renamed the directory? The reason is simple, Arma 3 on Linux does not like spaces and capital letters in folder names. And now you may wonder why people knowing this would continue to release their mod with spaces and capital letter and there...I have to say that I wonder the same.*

## Installing the mod

Let's create a mods directory in serverfiles:

`mkdir /home/arma3server/serverfiles/mods`

Now, let's copy the files

`cp -r /home/arma3server/antistasiSource/ /home/arma3server/serverfiles/mods`

Let's place the key(s) in the right place

`cp -r /home/arma3server/serverfiles/mods/@antistasi/Keys/* /home/arma3server/serverfiles/keys`

*Notice the change in the capital letters of the keys folder? It's not a mistake, it's on purpose*

### Choosing the map

In this file

`vim /home/arma3server/serverfiles/cfg/arma3server.server.cfg`

Add this at the end of it:

```sqf
class Missions {
  class Mission1 {
        template ="Antistasi_Altis.Altis";
        difficulty = "Regular"; //can be Recruit, Regular, Veteran or Custom. Custom needs setting up though.
        class Params {
            autoLoadLastGame = 60;
            LogLevel = 2;
            A3A_logDebugConsole = 1;
    };
  };
};
```

You can change the `difficulty` with other values as suggested in the comments

And the `template`, is the map you wanna play on, you can change it to other values

| Map              | Missionname                                   |
| ---------------- | --------------------------------------------- |
| Altis            | `Antistasi_Altis.Altis`                       |
| Anizay           | `Antistasi_tem_anizay.tem_anizay`             |
| Cam Lao Nam      | `Antistasi_cam_lao_nam.cam_lao_nam`           |
| Chernarus Autumn | `Antistasi_chernarus.chernarus`               |
| Chernarus Summer | `Antistasi_chernarus_summer.chernarus_summer` |
| Chernarus Winter | `Antistasi_chernarus_winter.chernarus_winter` |
| Khe Sanh         | `Antistasi_vn_khe_sanh.vn_khe_sanh`           |
| Kunduz           | `Antistasi_Kunduz.Kunduz`                     |
| Livonia          | `Antistasi_Enoch.Enoch`                       |
| Malden           | `Antistasi_Malden.Malden`                     |
| Sahrani          | `Antistasi_sara.sara`                         |
| Takistan         | `Antistasi_Takistan.takistan`                 |
| Tanoa            | `Antistasi_Tanoa.Tanoa`                       |
| Tembelan Island  | `Antistasi_Tembelan.Tembelan`                 |
| Virolahti        | `Antistasi_vt7.vt7`                           |

Source: [Beginners Guide for Antistasi v3.0 ; Antistasi Guide documentation](https://official-antistasi-community.github.io/A3-Antistasi-Docs/beginners_guide/raw_beginners_guide.html)

---

### Setting up the admin password

In that same file (`/home/arma3server/serverfiles/cfg/arma3server.server.cfg`) 

Let's change passwordAdmin to whatever value you will remember

`passwordAdmin = "somePassword";`

We will NEED THIS when starting the server later on

You can also set up other things in that file, for instance if you don't want BattleEye troubles, then:

`battleyeLicense = 0;`

`BattlEye = 0;`

It's pretty clear and the comments in the file drive you through the different values you can use

### Setting up the mod directory

We need to tell Arma 3 server that you want to use the Antistasi mod.

Open the file:

`vim /home/arma3server/lgsm/config-lgsm/arma3server/arma3server.cfg`

And modify it so that it looks like this

```bash
##################################
####### Instance Settings ########
##################################
# PLACE INSTANCE SETTINGS HERE
## These settings will apply to a specific instance.

mods="mods/@antistasi"
```

You might notice that we indicated the relative position of the `mods/@antistatsi` folder

In `/home/arma3server/lgsm/config-lgsm/arma3server/common.cfg`

I have added this line

`startparameters="-ip=${ip} -port=${port} -cfg=${networkcfgfullpath} -config=${servercfgfullpath} -mod=${mods} -servermod=${servermods} -bepath=${bepath} -loadmissiontomemory -cpuCount=4 -enableHT"`

`cpuCount` is at `4` because my CPU on my server has 4 physical cores 

## Starting the server

Now that everything is ready you should be able to run (I assume you're positioned in `/home/arma3server/`):

`./arma3server start`

That's it for the server side.

# Installing and running the mod on your computer

Yes, you ALSO need to install the mod on your computer (client).

Download the mod on your computer from here: [Releases · official-antistasi-community/A3-Antistasi · GitHub](https://github.com/official-antistasi-community/A3-Antistasi/releases)

Now you have a rar file

Extract the file using your favorite utility (I recommend 7zip, Free Software and super efficient)

Then start Arma 3 Launcher

In the Launcher go to "Mods" -> click on Local mod (top of the screen) -> browse your disk to find  the addons folder in the Antistasi archive you just extracted. For it's located there:

`C:\Users\<user>\Downloads\@Antistasi.-.The.Mod\@Antistasi - The Mod\addons`

Click on "select folder"

Done.

It's exactly the same for any other versions of Antistasi (Antistasi Plus for instance) and of course you'll have to use the proper tool on Windows to unzip or 7zip (the best) to deal with other archive types.

## Configuring and creating your game

Connect to your server using Arma 3's launcher

Once you're logged on your server, you'll want to connect as an admin to do that, type in the in game text chat: `#login somePassword`

Remember `somePassword`? we defined it way earlier in the tutorial -> well you use it now!

A GUI should be displayed in game letting you create and set parameters for your game.

That part is not covered by this tutorial -> take your time and read the GUI you'll figure it out

### Additional notes

If you press escape you have access to a console and you can do a server exec for one of those command lines.

This sets the amount of weapons you have to gather before they become unlimited in the Arsenal

`minWeaps = 10; publicVariable "minWeaps";`

`minWeaps = 1; publicVariable "minWeaps";`
