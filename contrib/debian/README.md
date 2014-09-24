
Debian
====================
This directory contains files used to package envycoind/envycoin-qt
for Debian-based Linux systems. If you compile envycoind/envycoin-qt yourself, there are some useful files here.

## envycoin: URI support ##


envycoin-qt.desktop  (Gnome / Open Desktop)
To install:

	sudo desktop-file-install envycoin-qt.desktop
	sudo update-desktop-database

If you build yourself, you will either need to modify the paths in
the .desktop file or copy or symlink your envycoin-qt binary to `/usr/bin`
and the `../../share/pixmaps/envycoin128.png` to `/usr/share/pixmaps`

envycoin-qt.protocol (KDE)

