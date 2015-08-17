# Maintainer: mid-kid <esteve.varela@gmail.com>
pkgname=qt-ponies-git
_realname=qt-ponies
pkgver=v0.8.6.g2657b25
pkgrel=2
pkgdesc="An implementation of DesktopPonies in Qt"
arch=("i686" "x86_64")
url="https://github.com/myszha/qt-ponies"
license=('GPL')
depends=("qt4" "libxfixes")
makedepends=("git")
source=("$_realname::git+https://github.com/myszha/$_realname.git")
md5sums=("SKIP")

pkgver() {
	cd "$srcdir/$_realname"
	git describe --tags | sed 's|-|.|g'
}

prepare() {
	cd "$srcdir/$_realname"
	# Set default desktop-ponies directory
	sed -i "s/.\/desktop-ponies/\/usr\/share\/qt-ponies\/desktop-ponies/g" src/configwindow.cpp
}

build() {
	cd "$srcdir/$_realname"
	/usr/lib/qt4/bin/qmake
	make
}

package() {
	cd "$srcdir/$_realname"
	make INSTALL_ROOT="$pkgdir/" install
}
