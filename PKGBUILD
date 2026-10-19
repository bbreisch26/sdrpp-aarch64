# Maintainer: Ben Breisch <ben.breisch@gmail.com>
# Arch Linux ARM build based on the AUR sdrpp-git recipe.
# Original AUR maintainers: Alexandre Rouma and éclairevoyant.

_pkgname=sdrpp
pkgname="$_pkgname-git"
pkgver=1.0.4.r886.8c9f5ee8
pkgrel=4
pkgdesc="SDR++ with release modules available on Arch Linux ARM"
arch=(aarch64)
url="https://github.com/AlexandreRouma/SDRPlusPlus"
license=(GPL-3.0-only)
depends=(airspy bladerf codec2 fftw glew glfw hackrf libad9361 libiio libvolk portaudio rtaudio rtl-sdr zstd)
makedepends=(cmake git)
provides=("$_pkgname")
conflicts=("$_pkgname")
source=("$_pkgname::git+https://github.com/AlexandreRouma/SDRPlusPlus.git")
b2sums=('SKIP')

pkgver() {
	git -C $_pkgname describe --long --tags --exclude nightly | sed 's/\([^-]*-\)g/r\1/;s/-/./g'
}

build() {
	cmake -B build -S $_pkgname \
		-DCMAKE_BUILD_TYPE=Release \
		-DOPT_BUILD_AIRSPY_SOURCE=ON \
		-DOPT_BUILD_AIRSPYHF_SOURCE=OFF \
		-DOPT_BUILD_AUDIO_SOURCE=ON \
		-DOPT_BUILD_AUDIO_SINK=ON \
		-DOPT_BUILD_BLADERF_SOURCE=ON \
		-DOPT_BUILD_DISCORD_PRESENCE=ON \
		-DOPT_BUILD_FOBOSSDR_SOURCE=OFF \
		-DOPT_BUILD_HACKRF_SOURCE=ON \
		-DOPT_BUILD_LIMESDR_SOURCE=OFF \
		-DOPT_BUILD_M17_DECODER=ON \
		-DOPT_BUILD_PERSEUS_SOURCE=OFF \
		-DOPT_BUILD_PLUTOSDR_SOURCE=ON \
		-DOPT_BUILD_RFNM_SOURCE=OFF \
		-DOPT_BUILD_RTL_SDR_SOURCE=ON \
		-DOPT_BUILD_SDRPLAY_SOURCE=OFF \
		-DOPT_BUILD_NEW_PORTAUDIO_SINK=ON \
		-DOPT_BUILD_PORTAUDIO_SINK=OFF \
		-DOPT_BUILD_ATV_DECODER=OFF \
		-DOPT_BUILD_PAGER_DECODER=OFF \
		-DCMAKE_POLICY_VERSION_MINIMUM=3.5
	make -C build -j2
}

package() {
	make -C build DESTDIR="$pkgdir" install
}
