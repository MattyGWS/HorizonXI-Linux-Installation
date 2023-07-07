# HorizonXI-Linux-Installation
A step by step guide to installing HorizonXI, the private FFXI server, on linux.

The original step by step is in this link from earlier <https://vaughanhilts.me/2022/06/19/installing-horizon-xi-linux.html> but I understand this looks a little crazy so I'll try to explain it in a more broken down way.

-----

Software to be aware of;

**Konsole** - this is a terminal (commandline) software for typing in commands, this is already installed. You'll be copy/pasting commands in here but remember that copy/pasting in konsole is ctrl+shift + c, and ctrl+shift + v, where everywhere else copy/paste is just ctrl+c and ctrl+v. if this is annoying you can use a mouse and right click in the konsole window and copy/paste that way.

**Discover** - this is just an app store, it's already installed, think of it like windows' store app.

**ProtonUp-qt** - this needs to be installed, go to the discover app and search for it, install it. This software just allows you to add proton-ge to steam (a community version of proton, the compatibility software that lets you run windows software on linux, dont worry if this sounds confusing you don't need to know much about it).

**Firefox** - web browser, if not installed already you can grab this on the discover app.

**Kate** - already installed, this is the notepad of your linux desktop. (it's actually better and you can get it on windows too, would recommend over notepad).

**Dolphin** - this is just the folder/file explorer like on windows, it has a name for some reason and that name is dolphin.

-----

All of this is done in desktop mode if you're on the steamdeck, which looks and feels similar to windows. Best used with a mouse and keyboard if possible as it's not so fun to use with the steamdecks on screen keyboard and touch pads. That said, once you're done installing you never need to go back to desktop mode again or use a mouse and keyboard to play horizon, switching between desktop and game mode is easy enough though. If you're on a regular desktop linux distro then you can ignore the steamdeck steps.

-----

steps to take

1. First you'd need to set a memorable sudo password (admin password) if you haven't already. If you're on steamdeck this step is likely needed. Open the konsole and type `passwd` then type in a password as prompted and press enter. Heads up typing in the password in future in the konsole will look like you aren't typing at all, this is a security feature of the terminal, you're still inputting the password but it just doesn't visibly show.

2. Download the horizon launcher to the Downloads folder (usually the default Downloads folder location) from here;
<https://github.com/HorizonFFXI/HorizonXI-Launcher-Binaries/releases/tag/v1.0.1>

3. Open up a konsole window and copy paste or type this (note the line that states the version number, change that number based on whichever version you have;

```
mkdir ~/horizon-xi
cp "/home/deck/Downloads/HorizonXI-Launcher-1.0.1.Setup.exe" ~/horizon-xi/installer.exe
cd ~/horizon-xi
7z x installer.exe
7z x HorizonXI_Launcher-1.0.1-full.nupkg
```

4. open the ProtonQT-Up app you got earlier from the discover store and add version "GE-Proton-42" (this will require you to restart the steam application for it to take effect once you've added this proton version)
![image](https://github.com/MattyGWS/HorizonXI-Linux-Installation/assets/56587299/9a8009b2-6361-4984-b2cb-8859a3fb03b1)

5. Open the steam application and, in Library, in the bottom left corner should be a button to add a non-steam game, click the button and click browse and find the launcher (on my desktop pc this is located in "/home/mattyws/horizon-xi/lib/net45/HorizonXI-Launcher.exe" but maybe slightly different on the steamdeck). if you can't see it, you may need to change the ".desktop" at the bottom to "all application types" like in my screenshot here;
![image](https://github.com/MattyGWS/HorizonXI-Linux-Installation/assets/56587299/ae7711ab-e4d4-4ce8-bda2-c5bfc96965a1)

6. Now that you've added the launcher, find it in your library in steam and right click>properties, then go to the compatibility tab and choose the GE-proton version from earlier
![image](https://github.com/MattyGWS/HorizonXI-Linux-Installation/assets/56587299/5b1ac9f6-e317-4bd1-98a0-9d68dc5f5bd6)

7. Launch Horizon like you would any other steam game ! when you have the launcher open you can signup/signin and begin downloading/installing the game!

**the above steps work on other linux distros but steamdeck has an extra step to make the controls work** (and they work well once you've done it), this is the extra steamdeck steps;

8. Open the horizon launcher and open gamepad configuration, enable XInput.

9.  open dolphin (the folder/file explorer just like on windows) and go to `/home/deck/.local/share/Steam/steamapps/compatdata/<prefix_id>/drive_c/users/<user>/AppData/Roaming/HorizonXI-Launcher/`

and open config.json

10. make the following changes inside this file in the text editor (Kate is the name of the text editor, don't question it) --- This step can be skipped if you're just updating the launcher and you made the changes in the past;

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

-----
11. Go back into gamemode on the steamdeck, launch horizonxi launcher like any other game, hit play and you're done! (note that for me at least, on my steamdeck when i open the horizonxi launcher the mouse input from the touchpad doesn't seem to work so i have to press play by actually using the touch screen)

-----

12. Updating the launcher!

To update your launcher in the future, all you need to do is go to the horizon website and download the latest launcher exe from here;
<https://horizonxi.com/play-now>

Ensuring it's in the download folder, open your terminal and either write or paste this;

```
mkdir ~/horizon-xi
cp "/home/mattyws/MEGA/Downloads/HorizonXI-Launcher-1.1.6.Setup.exe" ~/horizon-xi/installer.exe
cd ~/horizon-xi
7z x installer.exe
7z x HorizonXI_Launcher-1.1.6-full.nupkg
```

but make sure you have the correct verion written instead of 1.1.6, in this case as of writing the latest version is 1.1.6.

Hit enter and go through the steps (either pressing y to say yes to every step or pressing a to say yes to all steps as prompted)

That's it, now you have updated the launcher. Nothing else to do!
