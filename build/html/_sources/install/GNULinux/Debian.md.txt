# Debian-based distributions

## Old runtime

To install the GNUstep libraries and development tools:
```bash
sudo apt install gnustep-devel gnustep-core-doc systempreferences.app gworkspace.app
```
(Optional) To install the GNUstep apps:
```bash
sudo apt install gnustep gnustep-examples gnustep-games
```

## New runtime

Both of these methods will install the **development version** of GNUstep.

### Build from source using `gnustep-build` scripts

Select a script from [`@plaurent/gnustep-build`](https://github.com/plaurent/gnustep-build). For example, on Raspbian 11 Bullseye:

```bash
mkdir -p ~/Projects/GNUstep/Install
cd ~/Projects/GNUstep/Install
sudo apt install libcurl4-gnutls-dev libcurl4 # Required for NSURLSession, which is required for networking
curl -O https://raw.githubusercontent.com/plaurent/gnustep-build/master/raspbian-11-clang-11.0-runtime-2.1-ARM/GNUstep-buildon-raspbian11.sh
nano --view GNUstep-buildon-raspbian11.sh
bash GNUstep-buildon-raspbian11.sh
```

### Build from source using install script

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/gnustep/tools-scripts/master/gnustep-web-install)"
```