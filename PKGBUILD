# Maintainer:  Spencer Colton <me@scolton.tech>

pkgname='pilot-link-sc-git'
pkgver='0.13.0.1'
pkgrel='1'
pkgdesc='pilot-link'
arch=('x86_64')
license=('GPL-2.0-only' 'LGPL-2.1-only' 'GPL-3.0-only' 'LGPL-3.0-only')
depends=('bluez-libs')
makedepends=('git')
options=('!libtool' 'staticlibs' '!buildflags' 'debug')
source=("git+https://github.com/desrod/pilot-link#branch=main")
sha256sums=('SKIP')

build() {
  cd "$srcdir/pilot-link"

  libtoolize
  aclocal
  autoheader
  automake --add-missing
  autoconf

  options=(
    "--prefix=/usr"
  )

  CFLAGS="-std=gnu90"

  CFLAGS="$CFLAGS" \
    ./autogen.sh \
    "${options[@]}"

  CFLAGS="$CFLAGS" \
    make -j1
}

package() {
  cd "$srcdir/pilot-link"
  make DESTDIR="$pkgdir" -j1 install
}
