# Enterprise Linux



## Old runtime

```{note}
These packages are probably out-of-date, because of EPEL's stability policy.
```

1. Follow the [EPEL documentation](https://docs.fedoraproject.org/en-US/epel/#_quickstart) to enable Extra Packages for Enterprise Linux.

2. Run the following script:

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

## New runtime

### Build from source using install script

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/gnustep/tools-scripts/master/gnustep-web-install)"
```