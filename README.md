# Envycoin Core [ENVY]
==========================

THIS IS PRELIMINARY CODE. IT WILL NOT WORK YET.


## What is Envycoin?
Envycoin is a cryptocurrency like Bitcoin, although with many key differences. Envycoin's wallet is forked from Bitcoin 0.9.2, and thus has a build process slightly different from most altcoins.

## Specs

Envycoin specs:



## License
Envycoin is released under the terms of the MIT license. See [COPYING](COPYING)
for more information or see http://opensource.org/licenses/MIT.

## Development and contributions
Development is ongoing and the development team as well as other volunteers can freely work in their own trees and submit pull requests when features or bug fixes are ready.


##  Building envycoind/envycoin-cli/envycoin-qt (these are actually useful)

  The following are developer notes on how to build Envycoin on your native platform. They are not complete guides, but include notes on the necessary libraries, compile flags, etc.

  - [OSX Build Notes](doc/build-osx.md)
  - [Unix Build Notes](doc/build-unix.md)
  - [Windows Build Notes](doc/build-msw.md)

## Network ports

* RPC: 9111
* P2P: 9112

        pchMessageStart[0] = 0xf3;
        pchMessageStart[1] = 0xf2;
        pchMessageStart[2] = 0xf2;
        pchMessageStart[3] = 0xf3;


POD-CryptoAsian
