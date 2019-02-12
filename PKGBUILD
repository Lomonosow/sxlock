pkgname=sxlock
pkgver=r33.d8abb7a
pkgrel=1
pkgdesc="A simple screen locker for X"
arch=('i686' 'x86_64')
url="https://github.com/Lomonosow/sxlock"
license=('MIT')
depends=('libxext' 'libxrandr' 'pam' 'ttf-droid')
makedepends=('git')
source=('git+https://github.com/Lomonosow/sxlock.git')
sha256sums=('SKIP')

pkgver() {
  cd "$srcdir/sxlock"
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
  cd "$srcdir/sxlock"
  make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
  cd "$srcdir/sxlock"
  make PREFIX=/usr DESTDIR="$pkgdir" install
  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
  install -Dm644 sxlock.service "$pkgdir/etc/systemd/system/sxlock@.service"
}
