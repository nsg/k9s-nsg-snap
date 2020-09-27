# k9s-nsg snap
[![Get it from the Snap Store](https://snapcraft.io/static/images/badges/en/snap-store-black.svg)](https://snapcraft.io/k9s-nsg)

This is an unofficial build of the software [k9s](https://github.com/derailed/k9s). The [official snap](https://snapcraft.io/k9s) is old and unmaintained. A discussion about that can be found [here](https://forum.snapcraft.io/t/personal-files-request-for-k9s-nsg/18378).

## Channels

If everything works `edge` should be an automatic successful build of the latest [release of k9s](https://github.com/derailed/k9s/releases). If this is not the case feel free to open an issue. The `stable` channel is used releases in edge that I have verified to be working, message me if you like a edge release promoted to stable.

## Install

Install the latest promoted stable release with:

* `snap install k9s-nsg`

Get the latest release from the edge channel with:

* `snap install --edge k9s-nsg`

The snap will read your configuration from `~/.kube`, you may need to grant it access with the command `snap connect k9s-nsg:kube-config`.

## Configuration

You will find K9s configuration in `$SNAP_USER_DATA/.k9s` (usually `~/snap/k9s-nsg/current/.k9s/`).

### Editor

You can change the default editor with `snap set k9s-nsg editor=<editor>`, the supported editors are:

#### nano (default)

Bundled inside the snap. Nano is a popular editor. Configured to display YAML nicely. This is the default option, to change back to this run `snap set k9s-nsg editor=nano`

#### nvim (Neovim)

Bundled inside the snap. VIM is an popular editor and so is the Neovim fork. Configured to display YAML nicely. To change to this, run `snap set k9s-nsg editor=nvim`


#### External editor

External editors installed on your system can be accessed by setting the editor to xdg-open (`snap set k9s-nsg editor=xdg-open`) this should open and dialog asking what application you like to use.

### KUBECONFIG

`KUBECONFIG` works but you need to export it to be available inside the snap. If you have something like `KUBECONFIG=/my/path`, change that to `export KUBECONFIG=/my/path/` or just add `export KUBECONFIG` after that line. This is the recommended way for multiple configuration files. Note that due the sandbox all files need to be inside `~/.kube/`.

### External commands

The sandbox is nice for security but adds limitations. If you need to run external programs/binaries they need to be moved to `$SNAP_USER_DATA` (usually `~/snap/k9s-nsg/current/`) (note that the working directory for kubectl is `$SNAP_USER_DATA/.kube/`). This may or may not be possible. If this is a hard requirement for you this snap may not be working as intended. Feel free to open an issue if you like to discuss options.
