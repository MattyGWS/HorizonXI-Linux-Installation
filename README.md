# HorizonXI-Linux-Installation
A step by step guide to installing HorizonXI, the private FFXI server, on linux/steamdeck using Steam. **Not Windows on steamdeck.**

**Please please please read each step carefully and do things in the correct order.**

Recommended to use a keyboard plugged in on Steamdeck! Otherwise you will have to use STEAM+X buttons to use a virtual keyboard on screen and it's not fun.

Please read each step carefully. If you are on Steamdeck you will need to go through each of these steps in order. If you are on a normal linux distro you can ignore the steamdeck steps/comments.

-----
-----

Software to be aware of;

**KDE** - This guide assumes you're using the KDE desktop environment, as opposed to Gnome or other DEs. The guide will be pretty much identical on all desktop environments but for some reason KDE devs gave stupid names to some of the default applications as seen below.

**Konsole** - This is a terminal (commandline) software for typing in commands, this is already installed. You'll be copy/pasting commands in here but remember that copy/pasting in konsole is ctrl+shift + c, and ctrl+shift + v, where everywhere else copy/paste is just ctrl+c and ctrl+v. if this is annoying you can use a mouse and right click in the konsole window and copy/paste that way, or even use the copy and paste buttons in the top right corner of the Konsole.

**Discover** - This is just an app store, it's already installed, think of it like windows' store app.

**ProtonUp-qt** - This needs to be installed, go to the discover app and search for it, install it. This software just allows you to add proton-ge to steam (a community version of proton, the compatibility software that lets you run windows software on linux, dont worry if this sounds confusing you don't need to know much about it).

**Kate** - Already installed, this is the notepad of your linux desktop.

**Dolphin** - This is just the folder/file explorer like on windows, it has a name for some reason and that name is dolphin.

**Steam** - If you're on Steamdeck you will obviously have this, if you're on other distros it may not be installed by default and you can find it in the discover store or whatever app store your distro has.

-----
I realise this looks daunting but all we're doing here is extracting the launchers .exe file as if it were a .zip, then running the .exe inside that with Steam as a non steam game. And with all that out of the way, here we go!


1. If you're on steamdeck you will need to set a memorable sudo password (admin password) if you haven't already. If you're on a normal linux desktop distro you can probably skip this as it's likely already been done (though it doesn't hurt to do it if you're unsure). Open the konsole and type `passwd` then type in a password as prompted then press enter. Heads up; when typing in the password in the Konsole it may look like you aren't typing at all, this is a security feature of the terminal, you're still inputting the password but it just doesn't visibly show.

2. Ensuring it's in the download folder, open the Konsole (if you haven't already) and copy/paste this command then press enter;

```
wget -P $HOME//Downloads https://github.com/HorizonFFXI/HorizonXI-Launcher-Binaries/releases/download/v1.3.0/HorizonXI-Launcher-1.3.0.Setup.exe &&
mkdir $HOME/horizon-xi;
cp "$HOME/Downloads/HorizonXI-Launcher-1.3.0.Setup.exe" $HOME/horizon-xi/installer.exe &&
cd $HOME/horizon-xi &&
7z x -y installer.exe &&
7z x -y HorizonXI_Launcher-1.3.0-full.nupkg
```
Make sure you have the correct verion of the launcher written, in this case as of writing the latest version is 1.3.0, if this is the same version you downloaded then no worries.

3. Open the ProtonQT-Up app you got earlier from the discover store and add version "GE-Proton-42" (this will require you to restart the steam application for it to take effect once you've added this proton version). if you didn't get the app already it's fine just grab it now;

![image](https://github.com/MattyGWS/HorizonXI-Linux-Installation/assets/56587299/9a8009b2-6361-4984-b2cb-8859a3fb03b1)

4. Open the steam application and, in Library, in the bottom left corner should be a button to add a non-steam game, click the button and click browse and find the launcher (this should be located in `~/horizon-xi/lib/net45/HorizonXI-Launcher.exe` where '~/' is the user's home directory. Unless it's a steamdeck install where the user will be "deck" this directory will differ on each machine.). if you can't see it, you may need to change the filter from ".desktop" at the bottom to "all application types" like in my screenshot here;

![image](https://github.com/MattyGWS/HorizonXI-Linux-Installation/assets/56587299/ae7711ab-e4d4-4ce8-bda2-c5bfc96965a1)

5. Now that you've added the horizonxi launcher to steam, find it in your library in steam and right click>properties, then go to the compatibility tab and choose GE-proton 7-42 (same version you downloaded earlier);

![image](https://github.com/MattyGWS/HorizonXI-Linux-Installation/assets/56587299/5b1ac9f6-e317-4bd1-98a0-9d68dc5f5bd6)

6. Hit play to launch Horizon from steam. when you have the launcher open you can signup/signin and begin downloading/installing the game! Once the game is fully downloaded, if you're on steamdeck you will still need to do the below steps. If you're on a normal desktop or laptop you can now enjoy HorizonXI!

-----

**the above steps work on other linux distros but steamdeck has this extra step to make the controls work. You only need to do this once, not every time you update the launcher**;

7. Open the horizon launcher and open gamepad configuration, enable XInput.

8. Open dolphin (the folder/file explorer just like on windows) and go to; `/home/deck/.local/share/Steam/steamapps/compatdata/<prefix_id>/drive_c/users/<user>/AppData/Roaming/HorizonXI-Launcher/`

the <prefix_ID> is a random number you will need to figure out which one is for horizon as there will likely be multiple folders in here. You can use the search function in the folder

and open config.json

9. Make the following changes inside this file in Kate (Kate is the name of the text editor, don't question it);

```
"padmode000": {
    "name": "Gamepad Settings Controls",
    "key": "padmode000",
    "value": [
        1,
        1,
        0,
        0,
        1,
        1
    ]
}
```

And;

```
"padsin000": {
    "name": "Button Mappings",
    "key": "padsin000",
    "value": [
        8,
        9,
        13,
        12,
        10,
        0,
        1,
        3,
        2,
        15,
        -1,
        -1,
        14,
        -33,
        -33,
        32,
        32,
        -36,
        -36,
        35,
        35,
        6,
        7,
        5,
        4,
        11,
        -1
    ]
}
```

10. Go back into gamemode on the steamdeck, launch horizonxi launcher like any other game, hit play and you're done! (note that for me at least, on my steamdeck when i open the horizonxi launcher the mouse input from the touchpad doesn't seem to work so i have to press play by actually using the touch screen)

-----

11. Updating the launcher!

Open the Konsole and run copy/paste then run this command.

```
wget -P $HOME/Downloads https://github.com/HorizonFFXI/HorizonXI-Launcher-Binaries/releases/download/v1.3.0/HorizonXI-Launcher-1.3.0.Setup.exe &&
mkdir $HOME/horizon-xi;
cp "$HOME/Downloads/HorizonXI-Launcher-1.3.0.Setup.exe" $HOME/horizon-xi/installer.exe &&
cd $HOME/horizon-xi &&
7z x -y installer.exe &&
7z x -y HorizonXI_Launcher-1.3.0-full.nupkg
```

That's it, now you have updated the launcher. Nothing else to do! 
