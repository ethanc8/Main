# Fedora

## Old runtime

### Install with official packages and build parts from source

```{note}
On architectures other than x86_64, you might have to replace `/usr/lib64/` with `/usr/lib` or `/usr/lib32`.
```

```bash
sudo dnf install -y gcc-objc redhat-rpm-config gnustep-make gnustep-base gnustep-base-devel
. /usr/lib64/GNUstep/Makefiles/GNUstep.sh
wget http://ftpmain.gnustep.org/pub/gnustep/core/gnustep-gui-0.29.0.tar.gz
tar -xzvf gnustep-gui-0.29.0.tar.gz
cd gnustep-gui-0.29.0
./configure
make -j4 && sudo make install
cd ..
wget http://ftpmain.gnustep.org/pub/gnustep/core/gnustep-back-0.29.0.tar.gz
tar -xzvf gnustep-back-0.29.0.tar.gz
cd gnustep-back-0.29.0
./configure
make -j4 && sudo make install
cd .. 
```

```{note}
Based on the [PikoPixel install script](http://twilightedge.com/gnustep/pikopixel/fedora_install_script.html).
```

### Install with RPM Sphere unofficial packages

```{warning}
This should work, but is untested!
```

#### Script

```bash
sudo dnf install -y https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
sudo dnf install -y https://github.com/rpmsphere/noarch/raw/master/r/rpmsphere-release-$(rpm -E %fedora).noarch.rpm
sudo dnf install gcc-objc redhat-rpm-config gnustep-make gnustep-base gnustep-base-devel gnustep-gui gnustep-gui-devel
```

#### Instructions

1. Enable RPM Fusion -- there are two ways to do this:

    a. Click the links on the [RPM Fusion website](https://rpmfusion.org/Configuration).

    b. Run the following command:
    ```bash
    sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
    ```

2. Enable RPM Sphere:
```bash
sudo dnf install https://github.com/rpmsphere/noarch/raw/master/r/rpmsphere-release-$(rpm -E %fedora).noarch.rpm
```

3. Install GNUstep packages:
```bash
sudo dnf install gcc-objc redhat-rpm-config gnustep-make gnustep-base gnustep-base-devel gnustep-gui gnustep-gui-devel
```

## New runtime

### Build from source using install script

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/gnustep/tools-scripts/master/gnustep-web-install)"
```