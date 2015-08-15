# Maintainer: Bastien Dejean <nihilhill@gmail.com>

reponame=bar
fullname=${reponame}-aint-recursive
pkgname=${fullname}-bskv-git
pkgver=78
pkgrel=1
pkgdesc='A lightweight XCB based bar -- raedwulf XFT branch'
arch=('i686' 'x86_64')
url="https://github.com/raedwulf/${reponame}"
license=('custom:MIT')
depends=('libxcb')
makedepends=('git')
provides=("${fullname}")
conflicts=("${fullname}")
source=("git://github.com/raedwulf/${reponame}.git#branch=xft-full-utf8-rebase")
md5sums=('SKIP')

pkgver() {
    cd "$reponame"
    git rev-list --count HEAD
}

build() {
    if [ -e ../config.h ] ; then
        msg2 "Copying custom 'config.h'."
        cp ../config.h "$reponame"
    else
        warning "No 'config.h' found in '$(readlink -f ..)'."
    fi
    cd "$reponame"
    make PREFIX=/usr
}

package() {
    cd "$reponame"
    make PREFIX=/usr DESTDIR="$pkgdir" install
    install -D -m644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}
