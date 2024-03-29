Envycoin 1.7
=====================

* Copyright (c) 2009-2014 Bitcoin Developers
* Copyright (c) 2011-2013 Litecoin Developers
* Copyright (c) 2013-2014 Envycoin Developers


Setup
---------------------
[Envycoin Core](http://envycoin.com/en/download) is the original Envycoin client and it builds the backbone of the network. However, it downloads and stores the entire history of Envycoin transactions (which is currently several GBs); depending on the speed of your computer and network connection, the synchronization process can take anywhere from a few hours to a day or more. Thankfully you only have to do this once.

Running
---------------------
The following are some helpful notes on how to run Envycoin on your native platform. 

### Unix

You need the Qt4 run-time libraries to run Envycoin-Qt. On Debian or Ubuntu:

	sudo apt-get install libqtgui4

Unpack the files into a directory and run:

- bin/32/envycoin-qt (GUI, 32-bit) or bin/32/envycoind (headless, 32-bit)
- bin/64/envycoin-qt (GUI, 64-bit) or bin/64/envycoind (headless, 64-bit)



### Windows

Unpack the files into a directory, and then run envycoin-qt.exe.

### OSX

Drag Envycoin-Qt to your applications folder, and then run Envycoin-Qt.

### Need Help?

* See the documentation at the [Envycoin Wiki](http://envyco.in/)
for help and more information.
* Ask for help on [#envycoin](http://webchat.freenode.net?channels=envycoin) on Freenode. If you don't have an IRC client use [webchat here](http://webchat.freenode.net?channels=envycoin).
* Ask for help on the [/r/envyducation subreddit](http://reddit.com/r/envyducation).

Building
---------------------
The following are developer notes on how to build Envycoin on your native platform. They are not complete guides, but include notes on the necessary libraries, compile flags, etc.

- [OSX Build Notes](build-osx.md)
- [Unix Build Notes](build-unix.md)
- [Windows Build Notes](build-msw.md)

Development
---------------------
The Envycoin repo's [root README](https://github.com/envycoin/envycoin/blob/master/README.md) contains relevant information on the development process and automated testing.

- [Coding Guidelines](coding.md)
- [Multiwallet Qt Development](multiwallet-qt.md)
- [Release Notes](release-notes.md)
- [Release Process](release-process.md)
- [Source Code Documentation (External Link)](https://dev.visucore.com/bitcoin/doxygen/)
- [Translation Process](translation_process.md)
- [Unit Tests](unit-tests.md)

### Resources
* Discuss on the [/r/envycoindev](http://www.reddit.com/r/envycoindev) subreddit.
* Discuss on [#envycoin-dev](http://webchat.freenode.net/?channels=envycoin-dev) on Freenode. If you don't have an IRC client use [webchat here](http://webchat.freenode.net/?channels=envycoin-dev).

### Miscellaneous
- [Assets Attribution](assets-attribution.md)
- [Files](files.md)
- [Tor Support](tor.md)

License
---------------------
Distributed under the [MIT/X11 software license](http://www.opensource.org/licenses/mit-license.php).
This product includes software developed by the OpenSSL Project for use in the [OpenSSL Toolkit](http://www.openssl.org/). This product includes
cryptographic software written by Eric Young ([eay@cryptsoft.com](mailto:eay@cryptsoft.com)), and UPnP software written by Thomas Bernard.
