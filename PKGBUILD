# Maintainer: ava1ar <mail(at)ava1ar(dot)info>

pkgname=chrome-pepper-flash
pkgdesc="Google Chrome's Pepper Flash plugin for ppapi compatible browsers (stable version)"
pkgver=19.0.0.185
pkgrel=1
_verbld=45.0.2454.101
_channel='stable'
arch=('i686' 'x86_64')
url="http://www.google.com/chrome"
license=('custom:chrome')
depends=('gcc-libs')
provides=("chromium-pepper-flash=${pkgver}" "chromium-pepper-flash-stable=${pkgver}")
replaces=("chromium-pepper-flash-stable")
optdepends=('pulseaudio-alsa: For PulseAudio users')

_arch=amd64
[[ $CARCH = i686 ]] && _arch=i386
source=(
	"google-chrome-${_channel}_${_verbld}_i386.deb::http://dl.google.com/linux/chrome/deb/pool/main/g/google-chrome-${_channel}/google-chrome-${_channel}_${_verbld}-1_i386.deb"
	"google-chrome-${_channel}_${_verbld}_amd64.deb::http://dl.google.com/linux/chrome/deb/pool/main/g/google-chrome-${_channel}/google-chrome-${_channel}_${_verbld}-1_amd64.deb"
	'http://www.google.com/chrome/intl/en/eula_text.html'
	
)
noextract=(
	"google-chrome-${_channel}_${_verbld}_i386.deb"
	"google-chrome-${_channel}_${_verbld}_amd64.deb"
)
sha256sums=('a5f2275d59b9bf49f094c62ce6a60610be5826cf96edf09525679f5e67a588d2'
            'f22f41e2ab4af3d0ef4b88f47abcf9fbcd9e9ec5e0a1ecb275cbb673ec688bb3'
            '4242ecd421c56d47e56f6384be5621fe4e7b772c11036a72145d0e580a0f464c')

prepare() {
	ar x "google-chrome-${_channel}_${_verbld}_${_arch}.deb"
	bsdtar -xf data.tar.xz
}

package() {
	install -d "${pkgdir}/usr/lib/PepperFlash"
	install -m644 opt/google/chrome/PepperFlash/* "${pkgdir}/usr/lib/PepperFlash"
	install -Dm644 "${srcdir}/eula_text.html" "${pkgdir}/usr/share/licenses/${pkgname}/eula_text.html"
}

