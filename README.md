# HorizonXI-Linux-Installation
A step by step guide to installing HorizonXI, the private FFXI server, on linux using Steam.

The original step by step is in this link; <https://vaughanhilts.me/2022/06/19/installing-horizon-xi-linux.html> but I understand this looks a little crazy to people not used to linux so I'll try to explain it in a more broken down way. Please read each step carefully. If you are on Steamdeck you will need to go through each of these steps in order. If you are on a normal linux distro you can ignore the steamdeck steps/comments.

Please please please read each step carefully and do things in the correct order. 

-----

Software to be aware of;

**KDE** - This guide assumes you're using the KDE desktop environment, as opposed to Gnome or other DEs. The guide will be pretty much identical on all desktop environments but for some reason KDE devs gave stupid names to some of the default applications as seen below.

**Konsole** - This is a terminal (commandline) software for typing in commands, this is already installed. You'll be copy/pasting commands in here but remember that copy/pasting in konsole is ctrl+shift + c, and ctrl+shift + v, where everywhere else copy/paste is just ctrl+c and ctrl+v. if this is annoying you can use a mouse and right click in the konsole window and copy/paste that way, or even use the copy and paste buttons in the top right corner of the Konsole.

**Discover** - This is just an app store, it's already installed, think of it like windows' store app.

**ProtonUp-qt** - This needs to be installed, go to the discover app and search for it, install it. This software just allows you to add proton-ge to steam (a community version of proton, the compatibility software that lets you run windows software on linux, dont worry if this sounds confusing you don't need to know much about it).

**Firefox** - Web browser, if not installed already you can grab this on the discover app. Otherwise use your browser of choice it's all good.

**Kate** - Already installed, this is the notepad of your linux desktop. (it's actually better and you can get it on windows too, would recommend over notepad).

**Dolphin** - This is just the folder/file explorer like on windows, it has a name for some reason and that name is dolphin.

**Steam** - If you're on steamdeck you will obviously have this, if you're on other distros it may not be installed by default and you can find it in the discover store or whatever app store your distro has. Be aware that the flatpak version of steam may be more annoying to use here as it has less permissions to read your drive than native steam would have.

**Steam Link** - This isn't needed if you can dock your steamdeck with its own mouse and keyboard, but if you can't then another option is to remote into your steamdeck from your pc. This is made extremely simple by the Steam Link application which you can get on every platform. This way you can just use your desktop/laptop pc to control your steamdeck! This is recommended over using the on-screen keyboard on the deck <https://store.steampowered.com/streaming/>

-----

steps to take

1. First you'd need to set a memorable sudo password (admin password) if you haven't already. If you're on steamdeck this step is likely needed, however if you're on a normal linux desktop distro you can probably skip this as it's already been done. Open the konsole and type `passwd` then type in a password as prompted and press enter. Heads up; when typing in the password in the Konsole it may look like you aren't typing at all, this is a security feature of the terminal, you're still inputting the password but it just doesn't visibly show.

2. Download the horizon launcher to the Downloads folder (usually the default Downloads folder location) from here;
<https://github.com/HorizonFFXI/HorizonXI-Launcher-Binaries/releases/tag/v1.0.1>

*Note that while this isn't the latest version, it's needed for the first install, you will need to update the launcher later after installing the game.*

3. Open up a konsole window and copy paste or type these lines one by one pressing enter to execute each one (you will need to update this later as of step 12, DO NOT update before installing the game) ensuring that the path is correct to your download folder;

```
mkdir ~/horizon-xi
```
```
cp "/home/deck/Downloads/HorizonXI-Launcher-1.0.1.Setup.exe" ~/horizon-xi/installer.exe
```
```
cd ~/horizon-xi
```
```
7z x installer.exe
```
```
7z x HorizonXI_Launcher-1.0.1-full.nupkg
```

4. open the ProtonQT-Up app you got earlier from the discover store and add version "GE-Proton-42" (this will require you to restart the steam application for it to take effect once you've added this proton version). if you didn't get the app already it's fine just grab it now.
![image](https://github.com/MattyGWS/HorizonXI-Linux-Installation/assets/56587299/9a8009b2-6361-4984-b2cb-8859a3fb03b1)

5. Open the steam application and, in Library, in the bottom left corner should be a button to add a non-steam game, click the button and click browse and find the launcher (on steamdeck pc this is located in "~/horizon-xi/lib/net45/HorizonXI-Launcher.exe" where 'deck' is the username on steamdeck). if you can't see it, you may need to change the filter from ".desktop" at the bottom to "all application types" like in my screenshot here;
![image](https://github.com/MattyGWS/HorizonXI-Linux-Installation/assets/56587299/ae7711ab-e4d4-4ce8-bda2-c5bfc96965a1)

6. Now that you've added the launcher, find it in your library in steam and right click>properties, then go to the compatibility tab and choose the GE-proton version from earlier
![image](https://github.com/MattyGWS/HorizonXI-Linux-Installation/assets/56587299/5b1ac9f6-e317-4bd1-98a0-9d68dc5f5bd6)

7. Launch Horizon like you would any other steam game ! when you have the launcher open you can signup/signin and begin downloading/installing the game!

-----

**the above steps work on other linux distros but steamdeck has an extra step to make the controls work** (and they work well once you've done it), this is the extra steamdeck steps;

8. Open the horizon launcher and open gamepad configuration, enable XInput.

9.  open dolphin (the folder/file explorer just like on windows) and go to; `/home/deck/.local/share/Steam/steamapps/compatdata/<prefix_id>/drive_c/users/<user>/AppData/Roaming/HorizonXI-Launcher/`

the <prefix_ID> is a random number you will need to figure out which one is for horizon as there will likely be multiple folders in here. You can use the search function in the folder

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

11. Go back into gamemode on the steamdeck, launch horizonxi launcher like any other game, hit play and you're done! (note that for me at least, on my steamdeck when i open the horizonxi launcher the mouse input from the touchpad doesn't seem to work so i have to press play by actually using the touch screen)

-----

12. Updating the launcher!

To update your launcher in the future, all you need to do is go to the horizon website and download the latest launcher exe from here;
<https://horizonxi.com/play-now>

Ensuring it's in the download folder, open your terminal and either write or paste these lines one by one (using the correct path for your download folder and name of the launcher file) pressing enter to execute each one;

```
mkdir ~/horizon-xi
```
```
cp "/home/deck/Downloads/HorizonXI-Launcher-1.1.12.Setup.exe" ~/horizon-xi/installer.exe
```
```
cd ~/horizon-xi
```
```
7z x installer.exe
```
```
7z x HorizonXI_Launcher-1.1.12-full.nupkg
```

Make sure you have the correct verion written instead of 1.1.12, in this case as of writing the latest version is 1.1.12, if this is the same version you downloaded then no worries.

You may be prompted during one of the steps to do something (either pressing y to say yes to each individual step as you go or pressing a to say yes to all steps as prompted)

That's it, now you have updated the launcher. Nothing else to do!
