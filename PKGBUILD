# Maintainer: Vincent Bernardoff <vb@luminar.eu.org>

pkgname=yyjson
pkgver=0.8.0
pkgrel=1
pkgdesc="A high performance C JSON library"
arch=('i686' 'x86_64' 'armv7h' 'aarch64')
url="https://ibireme.github.io/yyjson/"
license=('MIT')
depends=()
makedepends=('cmake')
source=("https://github.com/ibireme/yyjson/archive/refs/tags/${pkgver}.tar.gz")
sha512sums=('3872b46930fd0f4d659004a4d08cdb1c506ccc2bf2888f5ee50523929a2b72f9d8e72ee71dc958ebca630f1886858d4350521bffc18c300a27d25436833384a9')

build() {
    cd "${srcdir}/${pkgname}-${pkgver}"

    mkdir -p build && cd build
    cmake \
      -DBUILD_SHARED_LIBS=ON \
      -DCMAKE_BUILD_TYPE=RelWithDebInfo \
      -DCMAKE_INSTALL_PREFIX=/usr \
      -DCMAKE_INSTALL_LIBDIR=/usr/lib \
      ..

    cmake --build .
}

package() {
    cd "${srcdir}/${pkgname}-${pkgver}/build"

    make DESTDIR="${pkgdir}" install
    install -vDm644 -t "$pkgdir/usr/share/licenses/$pkgname" ../LICENSE
}

# vim:set ts=4 sw=4 et:
