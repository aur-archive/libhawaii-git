# Maintainer: Pier Luigi Fiorini <pierluigi.fiorini@gmail.com>

pkgname=libhawaii-git
pkgver=0.0.0
pkgrel=1
pkgdesc="Hawaii libraries"
arch=('i686' 'x86_64')
url="http://www.maui-project.org"
license=('LGPL2.1')
depends=('qt5-base' 'qt5-declarative')
makedepends=('git' 'gdb' 'cmake' 'extra-cmake-modules' 'qtchooser')
options=('debug')

_gitroot="git://github.com/mauios/libhawaii.git"
_gitbranch=dev
_gitname=libhawaii
source=(${_gitname}::${_gitroot}#branch=${_gitbranch})
md5sums=('SKIP')

pkgver() {
	cd ${srcdir}/${_gitname}
	git describe --always | sed 's|-|.|g'
}

prepare() {
	mkdir -p build
}

build() {
	export QT_SELECT=5

	cd build
	cmake ../${_gitname} \
		-DCMAKE_INSTALL_PREFIX=/usr \
		-DCMAKE_BUILD_TYPE=RelWithDebInfo
}

package() {
	cd build
	make DESTDIR="${pkgdir}" install
}
