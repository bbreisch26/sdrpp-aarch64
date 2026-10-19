# Maintainer: Ben Breisch <ben.breisch@gmail.com>
# ARM64 RTL-SDR build based on the AUR sdrpp-git recipe.
# Original AUR maintainers: Alexandre Rouma and éclairevoyant.

_pkgname=sdrpp
pkgname="$_pkgname-git"
pkgver=1.0.4.r886.8c9f5ee8
pkgrel=2
pkgdesc="SDR++ with RTL-SDR and PortAudio support for Arch Linux ARM"
arch=(aarch64)
url="https://github.com/AlexandreRouma/SDRPlusPlus"
license=(GPL-3.0-only)
depends=(fftw glew glfw libvolk rtl-sdr portaudio)
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
		-DOPT_BUILD_AIRSPY_SOURCE=OFF \
		-DOPT_BUILD_AIRSPYHF_SOURCE=OFF \
		-DOPT_BUILD_AUDIO_SOURCE=OFF \
		-DOPT_BUILD_AUDIO_SINK=OFF \
		-DOPT_BUILD_HACKRF_SOURCE=OFF \
		-DOPT_BUILD_PLUTOSDR_SOURCE=OFF \
		-DOPT_BUILD_DISCORD_PRESENCE=OFF \
		-DOPT_BUILD_RTL_SDR_SOURCE=ON \
		-DOPT_BUILD_NEW_PORTAUDIO_SINK=OFF \
		-DOPT_BUILD_PORTAUDIO_SINK=ON \
		-DCMAKE_POLICY_VERSION_MINIMUM=3.5
	make -C build
}

package() {
	make -C build DESTDIR="$pkgdir" install
}
