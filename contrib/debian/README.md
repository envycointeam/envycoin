
Debian
====================
This directory contains files used to package bitchcoind/bitchcoin-qt
for Debian-based Linux systems. If you compile bitchcoind/bitchcoin-qt yourself, there are some useful files here.

## bitchcoin: URI support ##


bitchcoin-qt.desktop  (Gnome / Open Desktop)
To install:

	sudo desktop-file-install bitchcoin-qt.desktop
	sudo update-desktop-database

If you build yourself, you will either need to modify the paths in
the .desktop file or copy or symlink your bitchcoin-qt binary to `/usr/bin`
and the `../../share/pixmaps/bitchcoin128.png` to `/usr/share/pixmaps`

bitchcoin-qt.protocol (KDE)

