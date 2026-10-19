# SDR++ for Arch Linux ARM with RTL-SDR

This is an unofficial Arch Linux ARM (`aarch64`) package recipe that builds SDR++ from its upstream source with the RTL-SDR source and PortAudio output. Other hardware source modules that require additional libraries are disabled. SDR++ also provides [aarch64 Debian nightlies](https://github.com/AlexandreRouma/SDRPlusPlus/releases/tag/nightly); this recipe packages it for Arch Linux ARM.

## Install

On an Arch Linux ARM system with `base-devel` installed:

```sh
git clone https://github.com/bbreisch26/sdrpp-rtl-aarch64.git
cd sdrpp-rtl-aarch64
makepkg -si
```

The package depends on `rtl-sdr`, which installs the driver library and udev rules. Plug in the dongle, then check it with `rtl_test -t`. Start the app with `sdrpp`, choose **RTL-SDR** as the source, and choose **Audio Sink** for sound (provided by PortAudio).

## Scope

This recipe was built and tested with an RTL-SDR dongle on an ARM64 Omarchy system using Arch Linux ARM packages. The upstream [SDR++ installation instructions](https://github.com/AlexandreRouma/SDRPlusPlus/blob/master/readme.md#arch-based) recommend building from source on Arch-based systems and explicitly do not recommend the `sdrpp-git` AUR package. This recipe builds from upstream source and is independent of that AUR package. It was originally adapted from its packaging script, with attribution in the PKGBUILD. [AUR submission rules](https://wiki.archlinux.org/title/AUR_submission_guidelines) prohibit duplicate packages and ARM-only submissions, so this recipe is hosted on GitHub.

The packaging files in this repository are licensed under MIT. SDR++ itself is licensed under GPL-3.0-only.
