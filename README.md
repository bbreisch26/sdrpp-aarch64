# SDR++ for Arch Linux ARM

An unofficial `aarch64` PKGBUILD for [SDR++](https://github.com/AlexandreRouma/SDRPlusPlus), built on a Raspberry Pi 4 (Cortex-A72).

## Install

Install `base-devel`, then:

```sh
git clone https://github.com/bbreisch26/sdrpp-aarch64.git
cd sdrpp-aarch64
makepkg -si
```

Run `sdrpp` after installation.

## Modules

The build uses `CMAKE_BUILD_TYPE=Release` and includes the modules in [SDR++'s release list](https://github.com/AlexandreRouma/SDRPlusPlus/blob/master/readme.md#module-list), with these exceptions:

| Release module | This build | Reason |
| --- | --- | --- |
| Airspy HF+, FobosSDR, Perseus, RFNM, SDRplay sources | Omitted | Required libraries are unavailable in the Arch Linux ARM repositories. |
| LimeSDR source | Omitted | Arch Linux ARM `limesuite` 23.11.0-9 crashes during device discovery on this Cortex-A72. |
| Legacy PortAudio sink | Omitted | It and the RtAudio sink both build as `audio_sink`; SDR++ cannot include both. |
| Android audio sink | Omitted | Android only. |

Airspy, bladeRF, HackRF, PlutoSDR, and RTL-SDR sources are included. The default **Audio Sink** uses RtAudio; the new PortAudio sink is installed and can be added in SDR++'s Module Manager. M17 and SDR++'s other release modules are included.

The packaging files are MIT licensed. SDR++ is GPL-3.0-only.
