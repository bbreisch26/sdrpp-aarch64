# SDR++ for Arch Linux ARM with RTL-SDR

This is a small Arch Linux ARM (`aarch64`) variant of the maintained [AUR `sdrpp-git` recipe](https://aur.archlinux.org/packages/sdrpp-git). It builds SDR++ with the RTL-SDR source and PortAudio output. Other hardware source modules that require additional libraries are disabled. SDR++ itself already provides [aarch64 Debian nightlies](https://github.com/AlexandreRouma/SDRPlusPlus/releases/tag/nightly); this recipe packages it for Arch Linux ARM.

## Install

On an Arch Linux ARM system with `base-devel` installed:

```sh
git clone https://github.com/bbreisch26/sdrpp-rtl-aarch64.git
cd sdrpp-rtl-aarch64
makepkg -si
```

The package depends on `rtl-sdr`, which installs the driver library and udev rules. Plug in the dongle, then check it with `rtl_test -t`. Start the app with `sdrpp`, choose **RTL-SDR** as the source, and choose **Audio Sink** for sound (provided by PortAudio).

## Scope

This recipe was built on an ARM64 Omarchy system using Arch Linux ARM packages. The package builds successfully, but reception requires a connected RTL-SDR dongle. The AUR already has a maintained `sdrpp-git` package, so this recipe is hosted here for ARM64 users and as a proposed change to its maintainer. [AUR submission rules](https://wiki.archlinux.org/title/AUR_submission_guidelines) prohibit duplicate packages.

The packaging files in this repository are licensed under MIT. SDR++ itself is licensed under GPL-3.0-only.
