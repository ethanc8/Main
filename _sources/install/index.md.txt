# Install

```{toctree}
---
hidden: true
---
GNULinux/Arch
GNULinux/Debian
GNULinux/EL
GNULinux/Fedora
```

## Old vs new runtime

The **old runtime**, provided by GCC, supports Objective-C 2.0 features and supports the Apple runtime's APIs as well as its own. It does not support newer features, such as Blocks.

The **new runtime**, `libobjc2`, supports the latest Objective-C 2.3 features. It requires you to compile all your apps with Clang, meaning it supports less platforms. However, you can still install on all major operating systems.

## Install on Windows

The installation on Windows is currently experimental. If you do not want to use an experimental installation, you can use the outdated installer.

## Install on GNU/Linux

Please select your distribution. Depending on your distribution, you may be able to install GNUstep from your distribution's package manager -- otherwise, you can install from source by using a script.

::::{grid} 1 2 2 3
:margin: 4 4 0 0
:gutter: 1

:::{grid-item-card} Debian-based distributions
:link: GNULinux/Debian
:link-type: doc

including Debian, Ubuntu, Zorin OS, elementary OS, Mint, Raspbian, Raspberry Pi OS, Armbian, and Devuan.
:::

:::{grid-item-card} Fedora
:link: GNULinux/Fedora
:link-type: doc


:::

:::{grid-item-card} EL/CentOS/RHEL-based distributions
:link: GNULinux/EL
:link-type: doc

including Red Hat Enterprise Linux, CentOS, CentOS Stream, Oracle Linux, Rocky Linux, AlmaLinux, and Springdale Linux
:::

:::{grid-item-card} Arch and Manjaro
:link: GNULinux/Arch
:link-type: doc


:::

::::

## Install on UNIX

