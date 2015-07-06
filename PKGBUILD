# Maintainer: Jaroslav Lichtblau <dragonlord@aur.archlinux.org>

pkgname=pdf2html
pkgver=1.4
pkgrel=7
pkgdesc="Converts pdf files to html files."
arch=('i686' 'x86_64')
url="ftp://atrey.karlin.mff.cuni.cz/pub/local/clock/pdf2html/pdf2html-1.4/README"
license=('GPL')
depends=('ghostscript' 'imagemagick' 'libpng')
makedepends=('patch')
source=(
	"ftp://atrey.karlin.mff.cuni.cz/pub/local/clock/$pkgname/$pkgname-$pkgver.tgz"
    'pbm2png.diff'
    'index.html.diff'
	'pdf2html-1.4-libpng15.patch'
)

md5sums=(
	'cefb8fac9366cc7f793740e9d397af1a'
	'f68531d64358cc7f23282792510199e5'
	'017aa3a4d4ce042f519ca9863994d285'
	'eeda46aff3d9cbd6206ab18de45e8e4d'
)

build() {
	cd $pkgname-$pkgver

	patch -Np0 -i "$srcdir/pbm2png.diff"
	patch -Np0 -i "$srcdir/index.html.diff"
	patch -Np0 -i "$srcdir/pdf2html-1.4-libpng15.patch"

	make
}

package() {
	cd $pkgname-$pkgver

	install -dm755 "$pkgdir/usr/share/$pkgname"
	install -Dm644 *.png index.html "$pkgdir/usr/share/$pkgname"
	echo "cp /usr/share/pdf2html/*.png ." >> pdf2html
	install -dm755 "$pkgdir/usr/bin"
	install -Dm755 pbm2png pbm2eps9 pdf2html ps2eps9 "$pkgdir/usr/bin"
}
