# Electrum-CAT - Lightweight Catcoin client

```
Licence: MIT Licence
Author: CatcoinCore Developers
Language: Python (>= 3.10)
Homepage: https://electrum-cat.org/
```

[![Build Status](https://api.cirrus-ci.com/github/catcoincore/electrum-cat.svg?branch=master)](https://cirrus-ci.com/github/catcoincore/electrum-cat)

## Getting started

_(If you've come here looking to simply run Electrum-CAT,
[you may download it here](https://electrum-cat.org/catcoin-electrum-wallet/).)_

Electrum-CAT itself is pure Python, and so are most of the required dependencies,
but not everything. The following sections describe how to run from source, but here
is a TL;DR:

```
$ sudo apt-get install libsecp256k1-dev
$ ELECTRUM_ECC_DONT_COMPILE=1 python3 -m pip install --user ".[gui,crypto]"
```

### Not pure-python dependencies

#### Qt GUI

If you want to use the Qt interface, install the Qt dependencies:
```
$ sudo apt-get install python3-pyqt6
```

#### libsecp256k1

For elliptic curve operations,
[libsecp256k1](https://github.com/bitcoin-core/secp256k1)
is a required dependency.

If you "pip install" Electrum-CAT, by default libsecp will get compiled locally,
as part of the `electrum-ecc` dependency. This can be opted-out of,
by setting the `ELECTRUM_ECC_DONT_COMPILE=1` environment variable.
For the compilation to work, besides a C compiler, you need at least:
```
$ sudo apt-get install automake libtool
```
If you opt out of the compilation, you need to provide libsecp in another way, e.g.:
```
$ sudo apt-get install libsecp256k1-dev
```

#### cryptography

Due to the need for fast symmetric ciphers,
[cryptography](https://github.com/pyca/cryptography) is required.
Install from your package manager (or from pip):
```
$ sudo apt-get install python3-cryptography
```

#### scrypt

For fast blockchain verification,
[scrypt](https://github.com/holgern/py-scrypt) is required.
Install from your package manager (or from pip):
```
$ sudo apt-get install python3-scrypt
```

#### hardware-wallet support

If you would like hardware wallet support,
[see this](https://github.com/spesmilo/electrum-docs/blob/master/hardware-linux.rst).


### Running from tar.gz

If you downloaded the official package (tar.gz), you can run
Electrum-CAT from its root directory without installing it on your
system; all the pure python dependencies are included in the 'packages'
directory. To run Electrum from its root directory, just do:
```
$ ./run_electrum_cat
```

You can also install Electrum-CAT on your system, by running this command:
```
$ sudo apt-get install python3-setuptools python3-pip
$ python3 -m pip install --user .
```

This will download and install the Python dependencies used by
Electrum-CAT instead of using the 'packages' directory.
It will also place an executable named `electrum-cat` in `~/.local/bin`,
so make sure that is on your `PATH` variable.


### Development version (git clone)

_(For OS-specific instructions, see [here for Windows](contrib/build-wine/README_windows.md),
and [for macOS](contrib/osx/README_macos.md))_

Check out the code from GitHub:
```
$ git clone https://github.com/catcoincore/electrum-cat.git
$ cd electrum-cat
$ git submodule update --init
```

Run install (this should install dependencies):
```
$ python3 -m pip install --user -e .
```

Create translations (optional):
```
$ sudo apt-get install python3-requests gettext qttools5-dev-tools
$ ./contrib/pull_locale
```

Finally, to start Electrum-CAT:
```
$ ./run_electrum_cat
```

### Run tests

Run unit tests with `pytest`:
```
$ pytest tests -v
```

To run a single file, specify it directly like this:
```
$ pytest tests/test_bitcoin.py -v
```

## Creating Binaries

- [Linux (tarball)](contrib/build-linux/sdist/README.md)
- [Linux (AppImage)](contrib/build-linux/appimage/README.md)
- [macOS](contrib/osx/README.md)
- [Windows](contrib/build-wine/README.md)
- [Android](contrib/android/Readme.md)


## Contributing

Any help testing the software, reporting or fixing bugs, reviewing pull requests
and recent changes, writing tests, or helping with outstanding issues is very welcome.
Implementing new features, or improving/refactoring the codebase, is of course
also welcome, but to avoid wasted effort, especially for larger changes,
we encourage discussing these on the issue tracker or IRC first.

Besides [GitHub](https://github.com/catcoincore/electrum-cat),
most communication about Electrum-CAT development happens on Discord, in the
`#General` channel on Catcoin Team 3 (Unofficial) Discord server. The easiest way to participate 
with the web client, [https://discord.gg/4HDPB5DE](https://discord.gg/4HDPB5DE).
