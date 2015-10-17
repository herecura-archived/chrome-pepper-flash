# Maintainer: ava1ar <mail(at)ava1ar(dot)info>

pkgname=chrome-pepper-flash
pkgdesc="Google Chrome's Pepper Flash plugin for ppapi compatible browsers (stable version)"
pkgver=19.0.0.207
pkgrel=1
_verbld=46.0.2490.71
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
sha256sums=('4e931cedefb37ce905c51075c4a328202bfc97ec06eae37ff3b3fe26c6632aec'
            'd70e55812164bf4f35f629af302ee53fc771ee4e00ffd26205e6541f3b6c8a96'
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

