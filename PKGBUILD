# Maintainer: ava1ar <mail(at)ava1ar(dot)info>

pkgname=chrome-pepper-flash
pkgdesc="Google Chrome's Pepper Flash plugin for ppapi compatible browsers (stable version)"
pkgver=20.0.0.306
pkgrel=1
_verbld=48.0.2564.109
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
sha256sums=('e4d8652972d468c07f517617b13e15ad7d8e5d3f3d01bf0ac4862a6652ec3087'
            'ba3fd26b9aafc5b747c979cf3abd5775e671b9088d5779d4a45c0a5b87f51aa6'
            'b35811bb330576631e64f7885c66720e0be4ca81afb04328b3a0f288a708e37f')

prepare() {
	ar x "google-chrome-${_channel}_${_verbld}_${_arch}.deb"
	bsdtar -xf data.tar.xz
}

package() {
	install -d "${pkgdir}/usr/lib/PepperFlash"
	install -m644 opt/google/chrome/PepperFlash/* "${pkgdir}/usr/lib/PepperFlash"
	install -Dm644 "${srcdir}/eula_text.html" "${pkgdir}/usr/share/licenses/${pkgname}/eula_text.html"
}

