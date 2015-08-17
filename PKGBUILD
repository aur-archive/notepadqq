# Maintainer: twa022 <twa022 at gmail dot com>
# Contributor: Zom <zom[at]eevul[dot]org>

pkgname=notepadqq
pkgver=0.45.1
_codemirrorver=4.7.0
pkgrel=1
pkgdesc="A Linux clone of Notepad++"
arch=('i686' 'x86_64')
url="http://notepadqq.sourceforge.net/wp/"
license=('GPL3')
depends=('qt5-webkit' 'qt5-svg')
makedepends=('')
source=("${pkgname}-${pkgver}.tar.gz"::https://github.com/notepadqq/${pkgname}/archive/v${pkgver}.tar.gz
        codemirror-${_codemirrorver}.tar.gz::https://github.com/notepadqq/CodeMirror/archive/${_codemirrorver}.tar.gz)
sha256sums=('8a65e695d935f47b013b9c1e553e9fb5d1a07fccb9d55b6a5db9684c954ed95d'
            '7fe7bfc906ef0a7108330f9a3d003459ed545f7a4a6cfc2d6193dd799784b5f2')

build() {
  cd ${srcdir}/notepadqq-${pkgver}
  cp -R ${srcdir}/CodeMirror-${_codemirrorver}/* ${srcdir}/notepadqq-${pkgver}/src/editor/libs/codemirror/

  ./configure --qmake-path qmake-qt5 --prefix=/usr
  make
}

package() {
  cd ${srcdir}/notepadqq-${pkgver}/src/ui

  make INSTALL_ROOT="$pkgdir" install
  install -Dm644 "${pkgdir}/usr/share/icons/hicolor/scalable/apps/${pkgname}.svg" "${pkgdir}/usr/share/pixmaps/${pkgname}.svg"
}
