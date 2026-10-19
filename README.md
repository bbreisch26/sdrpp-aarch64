# SDR++ for Arch Linux ARM

This is an unofficial Arch Linux ARM (`aarch64`) package recipe that builds SDR++ from its upstream source. It enables the modules in the [SDR++ README release list](https://github.com/AlexandreRouma/SDRPlusPlus/blob/master/readme.md#module-list) whose dependencies are available in Arch Linux ARM repositories and work on this Cortex-A72 machine. SDR++ also provides [aarch64 Debian nightlies](https://github.com/AlexandreRouma/SDRPlusPlus/releases/tag/nightly); this recipe packages it for Arch Linux ARM.

## Install

On an Arch Linux ARM system with `base-devel` installed:

```sh
git clone https://github.com/bbreisch26/sdrpp-aarch64.git
cd sdrpp-aarch64
makepkg -si
```

For an RTL-SDR dongle, the `rtl-sdr` dependency installs the driver library and udev rules. Plug in the dongle, then check it with `rtl_test -t`. Start the app with `sdrpp`, choose **RTL-SDR** as the source, and choose **Audio Sink** for sound. The recipe also builds the new PortAudio sink as an alternative.

## Release configuration

The table compares the modules marked **Built in Release** in SDR++'s README with this Arch Linux ARM build. Other modules in the release list that need no extra library remain enabled through their upstream CMake defaults. `CMAKE_BUILD_TYPE` is set to `Release`.

| Module group | SDR++ README release | This package |
| --- | --- | --- |
| Airspy, bladeRF, HackRF, PlutoSDR, RTL-SDR sources | Built | Built using Arch Linux ARM libraries |
| LimeSDR source | Built | Omitted: Arch Linux ARM `limesuite` 23.11.0-9 crashes on this Cortex-A72 with an unsupported ARMv8.3 instruction during device discovery |
| Airspy HF+, FobosSDR, Perseus, RFNM, SDRplay sources | Built | Omitted: required libraries are not in the Arch Linux ARM repositories |
| Audio, file, Hermes, network, RFspace, RTL-TCP, SDR++ server, Spectran HTTP, SpyServer sources | Built | Built |
| RtAudio sink, network sink, new PortAudio sink | Built | Built |
| Legacy PortAudio sink | Listed as built | Omitted: it and the RtAudio sink both define `audio_sink`, so upstream cannot build them together |
| M17, Meteor, and radio decoders | Built | Built |
| Discord integration, frequency manager, IQ exporter, recorder, rig control, scanner | Built | Built |
| Android audio sink | Built for Android | Not applicable to Linux |

The no longer recommended AUR `sdrpp-git` package is not used to build this package.

## Scope

This recipe was built and tested with an RTL-SDR dongle on an ARM64 Omarchy system using Arch Linux ARM packages. The upstream [SDR++ installation instructions](https://github.com/AlexandreRouma/SDRPlusPlus/blob/master/readme.md#arch-based) recommend building from source on Arch-based systems and explicitly do not recommend the `sdrpp-git` AUR package. This recipe builds from upstream source. It was originally adapted from the AUR packaging script, with attribution in the PKGBUILD. [AUR submission rules](https://wiki.archlinux.org/title/AUR_submission_guidelines) prohibit duplicate packages and ARM-only submissions, so this recipe is hosted on GitHub.

The packaging files in this repository are licensed under MIT. SDR++ itself is licensed under GPL-3.0-only.
