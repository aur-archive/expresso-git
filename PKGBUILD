# Maintainer: Anselmo L. S. Melo <anselmolsm@gmail.com>

pkgname=expresso-git
pkgver=20130301
pkgrel=2
pkgdesc="Expresso is a library that provides basic components to create QML based games."
arch=('i686' 'x86_64')
url="https://gitorious.org/expresso"
license=('LGPL')
depends=('qt4' 'pulseaudio')
makedepends=('gcc' 'git' 'qt4')
source=()
md5sums=()

_gitroot="git://gitorious.org/expresso/expresso.git"
_gitname=expresso

build() {
	cd "${srcdir}"

	if [ ! -d "${srcdir}/${_gitname}" ]; then
		git clone ${_gitroot}
	else
		cd ${_gitname} && git pull origin
	fi

	msg "GIT checkout done."

	cd "${srcdir}"
	cp -rf "${_gitname}" "${_gitname}-build"
	cd "${_gitname}-build"

	qmake-qt4
	make
}

package() {
	cd "${srcdir}/${_gitname}-build"

	make INSTALL_ROOT="${pkgdir}" install
}
