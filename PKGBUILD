# Contributor: Prurigro
# Maintainer: Prurigro

pkgname=scribus-rc
_pkgname=scribus
pkgver=1.4.0
pkgrel=1
pkgdesc="A desktop publishing program - 1.4.0 Release Candidate Tarball Version"
arch=('i686' 'x86_64')
license=('GPL')
url="http://www.scribus.net"
install=${pkgname}.install

depends=('libcups' 'lcms' 'qt' 'ghostscript' 'libart-lgpl' 'python2' 'libxml2' 'cairo' 'desktop-file-utils' 'freetype2' 'libtiff' 'libjpeg' 'pixman' 'ghostscript' 'fontconfig' 'openssl' 'python-imaging' 'tk')
makedepends=('cmake' 'gcc' 'make' 'pkg-config')

replaces=('old-scribus' 'scribus' 'scribus-stable' 'scribus-ng' 'scribus-svn')
provides=('scribus')

source=(http://downloads.sourceforge.net/project/scribus/scribus/"$pkgver"/"$_pkgname"-"$pkgver".tar.bz2
	"$_pkgname".desktop)
		
md5sums=('119b23cafcd35ebd8488ff499f97eff5'
	 'ad86251889b0a7aa145f61cfd86cc932')

build() {
	install -d "$srcdir"/"$_pkgname"-"$pkgver"/builddir || return 1
	pushd "$srcdir"/"$_pkgname"-"$pkgver"/builddir || return 1
		cmake ../ -DCMAKE_INSTALL_PREFIX:PATH=/opt/scribus/ -DWANT_SYSTEM_CAIRO=1 || return 1

		make || return 1
		make DESTDIR="$pkgdir" install || return 1

		install -D -m644 "$startdir"/"$_pkgname".desktop  "$pkgdir"/usr/share/applications/"$_pkgname".desktop || return 1
	popd || return 1
}
