# LSD (LSDeluxe)

[![license](http://img.shields.io/badge/license-Apache%20v2-blue.svg)](https://raw.githubusercontent.com/Peltoche/lsd/master/LICENSE)
[![Latest version](https://img.shields.io/crates/v/lsd.svg)](https://crates.io/crates/lsd)
[![build](https://github.com/Peltoche/lsd/workflows/CICD/badge.svg)](https://github.com/Peltoche/lsd/actions)
[![codecov](https://codecov.io/gh/Peltoche/lsd/branch/master/graph/badge.svg)](https://codecov.io/gh/Peltoche/lsd)
[![versions](https://img.shields.io/repology/repositories/lsd)](https://repology.org/project/lsd/versions)

# Table of Contents

- [Description](#description)
- [Screenshot](#screenshot)
- [Installation](#installation)
- [UnInstallation](#uninstallation)
- [Configurations](#configurations)
  * [Required](#required)
  * [Optional](#optional)
- [F.A.Q.](#faq)
- [Contributors](#contributors)
- [Credits](#credits)

## Description

This project is heavily inspired by the super [colorls](https://github.com/athityakumar/colorls)
project but with some little differences.  For example it is written in rust and not in ruby which makes it much faster.

## Screenshot

![image](https://raw.githubusercontent.com/Peltoche/lsd/assets/screen_lsd.png)

## Installation

### Prerequisites

Install the patched fonts of powerline nerd-font and/or font-awesome. Have a look at the [Nerd Font README](https://github.com/ryanoasis/nerd-fonts/blob/master/readme.md) for more installation instructions. Don't forget to setup your terminal in order to use the correct font.

See [this issue comment](https://github.com/Peltoche/lsd/issues/199#issuecomment-494218334) for detailed instructions on how to configure iTerm2 font settings correctly.

### On Archlinux

```sh
pacman -S lsd
```

### On Fedora

```sh
dnf install lsd
```

### On Ubuntu

_... and other Debian-based Linux distributions_

Download the latest .deb package from the [release page](https://github.com/Peltoche/lsd/releases) and install it via:

```sh
sudo dpkg -i lsd_0.17.0_amd64.deb # adapt version number and architecture
```

### On Gentoo

```sh
sudo emerge sys-apps/lsd
```
(Ebuild maintained by Georgy Yakovlev)


### On macOS

via [Homebrew](https://brew.sh/):

```sh
brew install lsd
```

### On NixOS/From nix

```sh
nix-env -iA nixos.lsd
```

Or add `lsd` to your `configuration.nix` like so:

```nix
# ...
environment.systemPackages = with pkgs; [
  # other packages ...
  lsd
];
# ...
```

### On FreeBSD

```sh
pkg install lsd
```

### On Windows

Install with [Scoop](https://scoop.sh):
```powershell
scoop install lsd
```

### From Sources

With Rust's package manager cargo, you can install lsd via:

```sh
cargo install lsd
```

If you want to install the latest master branch commit:
```sh
cargo install --git https://github.com/Peltoche/lsd.git --branch master
```

### From Binaries

The [release page](https://github.com/Peltoche/lsd/releases) includes precompiled binaries for Linux and macOS.

## Installation

### On Ubuntu

If you have installed it from the snap packages, you might have noticed [this issue](https://github.com/Peltoche/lsd/issues/392) with permissions on certain folders. So the solution is to uninstall ot from the snap packages and re-install from the .deb package:

To remove lsd installed via snap:

```
sudo snap remove lsd
```

## Configurations

### Required

Enable nerd fonts for your terminal, URxvt for example:

.Xresources
```
URxvt*font:    xft:Hack Nerd Font:style=Regular:size=11
```

### Optional


In order to use lsd when entering the `ls` command, you need to add this to your shell
configuration file  (~/.bashrc, ~/.zshrc, etc.):

  ```sh
  alias ls='lsd'
  ```

Some further examples of useful aliases:

  ```sh
  alias l='ls -l'
  alias la='ls -a'
  alias lla='ls -la'
  alias lt='ls --tree'
  ```

## F.A.Q.

### Default Colors

In the future the possibility to customize the colors might be implemented.
For now, the default colors are:

| User/Group | Permissions | File Types | Last time Modified | File Size |
|:---|:---|:---|:---|:---|
|![#ffffd7](https://placehold.it/17/ffffd7/000000?text=+) User|![#00d700](https://placehold.it/17/00d700/000000?text=+) Read |![#0087ff](https://placehold.it/17/0087ff/000000?text=+) Directory|![#00d700](https://placehold.it/17/00d700/000000?text=+) within the last hour|![#ffffaf](https://placehold.it/17/ffffaf/000000?text=+) Small File|
|![#d7d7af](https://placehold.it/17/d7d7af/000000?text=+) Group|![#d7ff87](https://placehold.it/17/d7ff87/000000?text=+) Write|![#00d700](https://placehold.it/17/00d700/000000?text=+) Executable File|![#00d787](https://placehold.it/17/00d787/000000?text=+) within the last day|![#ffaf87](https://placehold.it/17/ffaf87/000000?text=+) Medium File|
||![#af0000](https://placehold.it/17/af0000/000000?text=+) Execute|![#d7d700](https://placehold.it/17/d7d700/000000?text=+) Non-Executable File|![#00af87](https://placehold.it/17/00af87/000000?text=+) older|![#d78700](https://placehold.it/17/d78700/000000?text=+) Large File|
||![#ff00ff](https://placehold.it/17/ff00ff/000000?text=+) Execute with Stickybit|![#af0000](https://placehold.it/17/af0000/000000?text=+) Broken Symlink||![#ffffff](https://placehold.it/17/ffffff/000000?text=+) Non File|
||![#d75f87](https://placehold.it/17/d75f87/000000?text=+) No Access|![#00d7d7](https://placehold.it/17/00d7d7/000000?text=+) Pipe/Symlink/Blockdevice/Socket/Special|||
|||![#d78700](https://placehold.it/17/d78700/000000?text=+) CharDevice|||



## Contributors

Everyone can contribute to this project, improving the code or adding functions. If anyone wants something to be added we will try to do it.

As this is being updated regularly, don't forget to rebase your fork before creating a pull-request.

## Credits

Special thanks to:

- [meain](https://github.com/meain) for all his contributions and reviews
- [danieldulaney](https://github.com/danieldulaney) for the Windows integration
- [sharkdp](https://github.com/sharkdp) and his superb [fd](https://github.com/sharkdp/fd) from which I have stolen a lot of CI stuff.
- [athityakumar](https://github.com/athityakumar) for the project [colorls](https://github.com/athityakumar/colorls)
- All the other contributors
