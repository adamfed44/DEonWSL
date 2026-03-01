# DEonWSL

EVERYTHING TESTED ONLY IN UBUNTU 24.04 LTS AND MOSTLY WSL 2

Before doing anything, install WSL and VcXsrv or Xming (doesnt matter which), then start it.

Before installing ANY desktop enviroment, first do:

sudo apt update

Then copy this config to C:\Users\[yourusername]\.wslconfig


[wsl2]
networkingMode=mirrored

dnsTunneling=true

autoProxy=true

localhostForwarding=true


Then pick the DE you want.

And if you want the export and unset to be automatic, then open ~/.bashrc and copy the unset, export and dbus_launch lines to the end of the file, then save it.

## Gnome (WSL 2)

sudo apt install gnome-session gnome-software gnome-terminal nautilus gnome-control-center

export DISPLAY=127.0.0.1:0.0

export XDG\_SESSION\_TYPE=x11

export GDK\_BACKEND=x11

unset WAYLAND\_DISPLAY

gnome-session

## KDE Plasma (WSL 2)

sudo apt install kde-standard

export DISPLAY=127.0.0.1:0.0

export LIBGL\_ALWAYS\_SOFTWARE=1

export GALLIUM\_DRIVER=llvmpipe

dbus-launch --exit-with-session startplasma-x11

Run these inside Plasma

kwriteconfig5 --file kwinrc --group Compositing --key Enabled false

qdbus org.kde.KWin /KWin reconfigure

kwriteconfig5 --file kdeglobals --group KDE --key AnimationDurationFactor 0

kquitapp5 plasmashell \&\& kstart5 plasmashell > /dev/null 2>\&1 \&

Press Alt-Shift-F12 to disable animations

## XFCE 4 (WSL 1, do it if you have Windows 10 and WSL 1 only)

sudo apt install xfce4 xfce4-goodies

export DISPLAY=127.0.0.1:0.0

startxfce4

## XFCE 4 (WSL 2)

sudo apt install xfce4 xfce4-goodies

export DISPLAY=127.0.0.1:0.0

export XDG\_SESSION\_TYPE=x11

export GDK\_BACKEND=x11

unset WAYLAND\_DISPLAY

startxfce4

## LXDE (not the best)

sudo apt install lxde

export DISPLAY=127.0.0.1:0.0

export XDG\_SESSION\_TYPE=x11

export GDK\_BACKEND=x11

unset WAYLAND\_DISPLAY

dbus_launch --exit-with-session startlxde





