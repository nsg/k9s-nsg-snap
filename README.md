# k9s-nsg snap
[![Get it from the Snap Store](https://snapcraft.io/static/images/badges/en/snap-store-black.svg)](https://snapcraft.io/k9s-nsg)


This is an unofficial build of k9s. I made this because I like snaps, I just found k9s and liked it and the snap "k9s" is old.

## Channels

If everything works `edge` should be an automatic successful build of the latest [release of k9s](https://github.com/derailed/k9s/releases). If this is not the case feel free to open an issue. The `stable` channel is used releases in edge that I have verified to be working, message me if you like a edge release promoted to stable.

## Install

`snap install k9s-nsg` or `snap install --edge k9s-nsg`

The snap will read your configuration from `~/.kube`, you need to grant it access with the command `snap connect k9s-nsg:kube-config`.

## Configuration

You will find K9s configuration in `$SNAP_USER_DATA/.k9s` (usually `~/snap/k9s-nsg/current/.k9s/`).

K9s will normally launch your default editor when you press edit (`e`), this is not possible at the moment due the security sandbox. This snap has not permission to communicate with arbitrary applications so I have bundled the popular editors "nano" and "nvim". Nano is the default choice because it's more user friendly, to change it to nvim type `snap set k9s-nsg editor=nvim`.
