![GitHub Downloads (all assets, all releases)](https://img.shields.io/github/downloads/gaofengnan/ripgrep-debian/total)
![GitHub Downloads (all assets, latest release)](https://img.shields.io/github/downloads/gaofengnan/ripgrep-debian/latest/total)
![GitHub Release](https://img.shields.io/github/v/release/gaofengnan/ripgrep-debian)
![GitHub Release Date](https://img.shields.io/github/release-date/gaofengnan/ripgrep-debian?display_date=published_at)

<h1>
   <p align="center">
     <a href="https://github.com/BurntSushi/ripgrep"><img src="https://github.com/gaofengnan/ripgrep-debian/blob/main/ripgrep-logo.png" alt="ripgrep Logo" width="128" style="margin-right: 20px"></a>
     <a href="https://www.debian.org/"><img src="https://github.com/gaofengnan/ripgrep-debian/blob/main/debian-logo.png" alt="Debian Logo" width="104" style="margin-left: 20px"></a>
     <br>ripgrep for Debian
   </p>
</h1>
<p align="center">
 Recursively search directories for a regex pattern, respecting your gitignore.
</p>

# ripgrep for Debian

This repository contains build scripts to produce the _unofficial_ Debian packages
(.deb) for [ripgrep](https://github.com/BurntSushi/ripgrep/) hosted at [deb.gaofn.xyz](https://deb.gaofn.xyz).
This is a fork of [dariogriffo/ripgrep-debian](https://github.com/dariogriffo/ripgrep-debian) (MIT); the original packaging is by Dario Griffo.

Currently supported Debian distros are:
- Bookworm (v12)
- Trixie (v13)
- Forky (v14)
- Sid (testing)

Supported architectures:
- amd64 (x86_64) - All distributions
- arm64 (aarch64) - All distributions
- armhf (ARM hard float) - All distributions

These are the Linux targets upstream publishes binaries for. Each is a
statically linked musl build with PCRE2 compiled in, so the packages have no
library dependencies — unlike the Debian archive build, which links against
`libc6`, `libgcc-s1` and `libpcre2-8-0`.

This is an unofficial community project to provide a package that's easy to
install on Debian. If you're looking for the ripgrep source code, see
[ripgrep](https://github.com/BurntSushi/ripgrep/).

Each package installs:
- `/usr/bin/rg`
- shell completions for bash, fish and zsh
- the `rg.1` man page
- upstream and Debian changelogs, the copyright file, and the upstream
  README, FAQ and GUIDE

## Install/Update

### The Debian way

```sh
sudo install -d -m 0755 /etc/apt/keyrings
sudo curl -fsSL https://deb.gaofn.xyz/deb.gaofn.xyz.gpg -o /etc/apt/keyrings/deb.gaofn.xyz.gpg
sudo curl -fsSL https://deb.gaofn.xyz/deb.gaofn.xyz.sources -o /etc/apt/sources.list.d/deb.gaofn.xyz.sources
sudo apt update
sudo apt install -y ripgrep
```

### Manual Installation

1. Download the .deb package for your Debian version available on
   the [Releases](https://github.com/gaofengnan/ripgrep-debian/releases) page.
2. Install the downloaded .deb package.

```sh
sudo dpkg -i <filename>.deb
```

## Updating

To update to a new version, just follow any of the installation methods above. There's no need to uninstall the old version; it will be updated correctly.

## Building

### Build for single architecture
```sh
./build.sh <ripgrep_version> <build_version> <architecture>
# Example: ./build.sh 15.2.0 1 arm64
```

### Build for all architectures
```sh
./build.sh <ripgrep_version> <build_version> all
# Example: ./build.sh 15.2.0 1 all
```

## Roadmap

- [x] Produce a .deb package on GitHub Releases
- [x] Set up a debian mirror for easier updates

## Disclaimer

- This repo is not open for issues related to ripgrep. This repo is only for _unofficial_ Debian packaging.
