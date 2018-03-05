# Maintainer: Moritz Lipp <mlq@pwmt.org>

pkgname=zathura-pdf-mupdf-git
pkgrel=1
pkgver=0.3.2.2.g858be63
pkgdesc="PDF support for zathura by using the mupdf library"
arch=('i686' 'x86_64')
url="http://pwmt.org/projects/zathura-pdf-mupdf"
license=('custom')
depends=('zathura>=0.3.8' 'libmupdf>=1.12.0-2' 'jbig2dec>=0.14')
makedepends=('git')
conflicts=('zathura-pdf-mupdf')
provides=('zathura-pdf-mupdf')
source=('zathura-pdf-mupdf::git+https://github.com/NyanKiyoshi/zathura-pdf-mupdf.git')
md5sums=('SKIP')
_gitname=zathura-pdf-mupdf

build() {
  cd "$srcdir/$_gitname"
  make
}

package() {
  cd "$srcdir/$_gitname"
  make DESTDIR="$pkgdir/" install
  install -D -m664 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

pkgver() {
  cd "$srcdir/$_gitname"
  local ver="$(git describe --long --always)"
  printf "%s" "${ver//-/.}"
}

