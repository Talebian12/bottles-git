# Maintainter: Talebian <talebian@sovietunion.xyz>
pkgname=bottles-git
pkgver=2.4d2f6cd
pkgrel=1
pkgdesc="Easily manage wineprefix using environments"
arch=('x86_64')
url="https://github.com/bottlesdevs/Bottles"
license=('GPL3')
conflicts=('bottles')
depends=(
  'python'
  'hicolor-icon-theme'
  'libhandy'
  'appstream-glib'
)
makedepends=(
  'meson'
  'ninja'
  'dconf'
)
source=("git+https://github.com/bottlesdevs/Bottles")
sha256sums=('SKIP')

_repo="Bottles"
_ver=4d2f6cd

prepare () {
  cd "$srcdir/$_repo"
  git checkout $_ver
  rm -rf build
  mkdir build 
}

build () {
  cd "$srcdir/$_repo"
  arch-meson build
  ninja -j$(nproc) -C build
}

check () {
  ninja test -C "$srcdir/$_repo/build"
}

package () { 
  cd "$srcdir/$_repo"
  DESTDIR="$pkgdir/" ninja install -C build
  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$_repo/LICENSE"
}

