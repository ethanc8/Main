# Arch and Manjaro

```{note}
Unlike other platforms, precompiled binary packages are available for the new runtime! Therefore, the new runtime is highly recommended.
```

## Old runtime

## New runtime

### Precompiled binaries

These binaries were compiled in Spring 2021 for x86_64 by Johannes Brakensiek for the website [gnustep.app](https://web.archive.org/web/20210725061813if_/https://gnustep.app/). They were based on the development versions.


1. Add the following lines to `/etc/pacman.conf`:

```ini
[home_letterus_gnustep-ngr_Arch]
SigLevel = Optional TrustAll
Server = https://download.opensuse.org/repositories/home:/letterus:/gnustep-ngr/Arch/$arch
```

2. Import the key for the repository:

```bash
wget https://download.opensuse.org/repositories/home:/letterus:/gnustep-ngr/Arch/x86_64/home_letterus_gnustep-ngr_Arch.key -O - | sudo pacman-key --add -
sudo pacman-key --lsign-key 29F300A0D5CF9F32
```

3. Install the GNUstep packages:

```bash
sudo pacman -Syy gnustep-ngr gnustep-ngr-dev gnustep-ngr-desktop
```