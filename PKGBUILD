# dojecoin-qt Arch PKGBUILD
# Maintainer mxtm <max@mxtm.me>
# Based off of the dogecoin-qt-git PKGBUILD, based off of primecoin-qt's PKGBUILD by Daniel Spies

pkgname=dojecoin-qt
_binname=dojecoin
pkgver=initial
pkgrel=1
pkgdesc="A QT wallet for the cryptocurrency Dojecoin."
arch=('x86_64' 'i686')
url="http://dojecoin.com/"
license=('MIT')
provides=('dojecoin-qt')
depends=('qt4' 'miniupnpc' 'boost-libs')
makedepends=('boost' 'gcc' 'make' 'git')
source=('http://mxtm.me/dl/dojecoin-'${pkgver}'.tar.gz'
        'dojecoin.desktop')
install=dojecoin-qt.install

sha256sums=('4ba1267b6a3ed9a2dec80b31206a42bad2350bee3641e5a56089eeed446cacda'
            '501c36853385b532237dfa20f095c10ca6605c9d5cb1e849ff0cac0a05506281')

## files & commands for building
_qmake=qmake-qt4

build() {
	tar -xvzf ${_binname}-${pkgver}.tar.gz

	cd ${_binname}-${pkgver}

	${_qmake}
		
	make ${MAKEFLAGS} || make ${MAKEFLAGS}
}

package() {
	install -Dm644 ${_binname}.desktop ${pkgdir}/usr/share/applications/${_binname}.desktop

	cd ${_binname}-${pkgver}
	install -Dm755 ${_binname}-qt "$pkgdir"/usr/bin/${_binname}-qt
	install -Dm644 COPYING "$pkgdir/usr/share/licenses/$pkgname/COPYING"
	install -Dm644 src/qt/res/icons/DojeCoin.png "$pkgdir"/usr/share/pixmaps/${_binname}.png
}
