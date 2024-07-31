# HorizonXI-Linux-Installation
A step by step guide to installing HorizonXI, the private FFXI server, on linux/steamdeck using Steam. **Not Windows on steamdeck.**

**Please please please read each step carefully and do things in the correct order.**

Recommended to use a keyboard plugged in on Steamdeck! Otherwise you will have to use STEAM+X buttons to use a virtual keyboard on screen and it's not fun.

**Please read each step carefully.** If you are on Steamdeck you will need do the extra steps as stated. If you are on a normal linux distro you can ignore the steamdeck steps/comments.

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
-----

1. If you're on steamdeck you will need to set a memorable sudo password (admin password) if you haven't already. If you're on a normal linux desktop distro you can probably skip this as it's likely already been done (though it doesn't hurt to do it if you're unsure). Open the konsole and type `passwd` then type in a password as prompted then press enter. Heads up; when typing in the password in the Konsole it may look like you aren't typing at all, this is a security feature of the terminal, you're still inputting the password but it just doesn't visibly show.

2. Open the Konsole, copy/paste then run this command;

```
rm -f $HOME/Downloads/HorizonXI-Launcher-1.3.0.Setup.exe;
wget -P $HOME//Downloads https://github.com/HorizonFFXI/HorizonXI-Launcher-Binaries/releases/download/v1.3.0/HorizonXI-Launcher-1.3.0.Setup.exe &&
mkdir -p $HOME/horizon-xi;
cp "$HOME/Downloads/HorizonXI-Launcher-1.3.0.Setup.exe" $HOME/horizon-xi/installer.exe &&
cd $HOME/horizon-xi &&
7z x -y installer.exe &&
7z x -y HorizonXI_Launcher-1.3.0-full.nupkg
```

3. Open the ProtonQT-Up app you got earlier from the discover store and add version "GE-Proton-42" (this will require you to restart the steam application for it to take effect once you've added this proton version). if you didn't get the app already it's fine just grab it now;

![image](https://github.com/user-attachments/assets/8a334f84-4bf2-49cd-9035-7525123d5b31)


4. Open the steam application and, in Library, in the bottom left corner should be a button to add a non-steam game, click the button and click browse and find the launcher (this should be located in `~/horizon-xi/lib/net45/HorizonXI-Launcher.exe` where '~/' is the user's home directory. Unless it's a steamdeck install where the user will be "deck" this directory will differ on each machine.). if you can't see it, you may need to change the filter from ".desktop" at the bottom to "all application types" like in my screenshot here;

![image](https://github.com/user-attachments/assets/8c3a6b04-ca3b-46f3-827b-96186317ffd5)

5. Now that you've added the horizonxi launcher to steam, find it in your library in steam and right click>properties, then go to the compatibility tab and choose GE-proton 7-42 (same version you downloaded earlier);

![image](https://github.com/user-attachments/assets/0cdda30b-a029-4619-8ecb-2cda61bba616)

6. Hit play to launch Horizon from steam. when you have the launcher open you can signup/signin and begin downloading/installing the game! Once it's done, enjoy the game!

-----

**If you're on Steamdeck, there is an extra step to make the controls work. You only need to do this once, not every time you update the launcher**;

7. In desktop mode, open the Konsole, copy/paste then run this command;

```
rm -f $HOME/Downloads/config.json;
wget -P $HOME//Downloads https://github.com/MattyGWS/HorizonXI-Linux-Installation/blob/main/config.json &&
config_dir=$(find $HOME/.local/share/Steam/steamapps/compatdata/ -name "config.json" -exec dirname {} \;)
find $HOME/.local/share/Steam/steamapps/compatdata/ -name "config.json" -exec rm -f {} \;
if [ -n "$config_dir" ]; then
  cp $HOME/Downloads/config.json "$config_dir"
fi
```

8. Go back into gamemode on the steamdeck, launch horizonxi launcher like any other game, hit play and you're done! (note that for me at least, on my steamdeck when i open the horizonxi launcher the mouse input from the touchpad doesn't seem to work so i have to press play by actually using the touch screen)

-----

9. Updating the launcher!

Open the Konsole, copy/paste then run this command;

```
rm -f $HOME/Downloads/HorizonXI-Launcher-1.3.0.Setup.exe;
wget -P $HOME/Downloads https://github.com/HorizonFFXI/HorizonXI-Launcher-Binaries/releases/download/v1.3.0/HorizonXI-Launcher-1.3.0.Setup.exe &&
mkdir -p $HOME/horizon-xi;
cp "$HOME/Downloads/HorizonXI-Launcher-1.3.0.Setup.exe" $HOME/horizon-xi/installer.exe &&
cd $HOME/horizon-xi &&
7z x -y installer.exe &&
7z x -y HorizonXI_Launcher-1.3.0-full.nupkg
```

That's it, now you have updated the launcher. Nothing else to do! 
