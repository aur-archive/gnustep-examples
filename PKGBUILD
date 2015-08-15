# Contributor: Balló György <ballogyor+arch at gmail dot com>

pkgname=gnustep-examples
pkgver=1.4.0
pkgrel=1
pkgdesc="Helps you get started with GNUstep coding"
arch=('i686' 'x86_64')
url="http://www.gnustep.org/experience/examples.html"
license=('GPL')
depends=('gnustep-base' 'gnustep-gui')
makedepends=('gcc-objc' 'gendesk' 'imagemagick')
source=(ftp://ftp.gnustep.org/pub/gnustep/usr-apps/$pkgname-$pkgver.tar.gz)
md5sums=('03bf77ab41e7d1fc64a8325e68243be1')

prepare() {
	cd "$srcdir/$pkgname-$pkgver"
	convert gui/Calculator/Calculator.app.tiff Calculator.png
	convert gui/Ink/Ink_app.tiff Ink.png
	gendesk -n -f --pkgname="Calculator" --pkgdesc="Example calculator for GNUstep" --categories="Utility;Calculator"
	gendesk -n -f --pkgname="Ink" --pkgdesc="Example text editor for GNUstep" --categories="Utility;TextEditor"
}

build() {
	cd "$srcdir/$pkgname-$pkgver"
	. /usr/share/GNUstep/Makefiles/GNUstep.sh
	make
}

package() {
	cd "$srcdir/$pkgname-$pkgver"
	make DESTDIR="$pkgdir" install
	install -Dm644 Calculator.png "$pkgdir/usr/share/pixmaps/Calculator.png"
	install -Dm644 Ink.png "$pkgdir/usr/share/pixmaps/Ink.png"
	install -Dm644 Calculator.desktop "$pkgdir/usr/share/applications/Calculator.desktop"
	install -Dm644 Ink.desktop "$pkgdir/usr/share/applications/Ink.desktop"
}
