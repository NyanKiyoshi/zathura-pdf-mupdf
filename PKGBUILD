# Maintainer: Moritz Lipp <mlq@pwmt.org>

pkgname=zathura-pdf-mupdf-git
pkgrel=1
pkgver=0.3.3.3.g34197ee
pkgdesc="PDF support for zathura by using the mupdf library"
arch=('i686' 'x86_64')
url="http://pwmt.org/projects/zathura-pdf-mupdf"
license=('custom')
depends=('zathura>=0.3.9' 'jbig2dec' 'openjpeg2' 'libjpeg' 'cairo' 'desktop-file-utils' 'openssl')
makedepends=('git' 'meson' 'libmupdf>=1.12.0-2')
conflicts=('zathura-pdf-mupdf')
provides=('zathura-pdf-mupdf')
source=('zathura-pdf-mupdf::git+https://github.com/NyanKiyoshi/zathura-pdf-mupdf.git#tag=0.3.3')
md5sums=('SKIP')
_gitname=zathura-pdf-mupdf

prepare() {
  mkdir -p build
}

build() {
  cd build
  meson --prefix=/usr --buildtype=release $srcdir/$_gitname
  ninja
}

package() {
  cd build
  DESTDIR="$pkgdir/" ninja install
  install -D -m664 $srcdir/$_gitname/LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

pkgver() {
  cd "$srcdir/$_gitname"
  local ver="$(git describe --long --always)"
  printf "%s" "${ver//-/.}"
}

