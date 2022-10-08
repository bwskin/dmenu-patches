pkgname=dmenu
pkgver=5.2
pkgrel=1
pkgdesc='Generic menu for X'
url='https://tools.suckless.org/dmenu/'
arch=('x86_64')
license=('MIT')
depends=('sh' 'glibc' 'coreutils' 'libx11' 'libxinerama' 'libxft' 'freetype2' 'fontconfig' 'libfontconfig.so')
source=(
  https://dl.suckless.org/tools/dmenu-${pkgver}.tar.gz
  0001-line-height.patch
  0002-xyw.patch
  0003-separator.patch
  0004-fuzzy-search.patch
  0005-lines-below-prompt.patch
  0006-password.patch
  0007-password-top-offset.patch
  0008-no-options.patch
  0009-center.patch
  0010-naoto-theme.patch
)
sha256sums=('SKIP' 'SKIP' 'SKIP' 'SKIP' 'SKIP' 'SKIP' 'SKIP' 'SKIP' 'SKIP' 'SKIP' 'SKIP')

prepare() {
  cd ${pkgname}-${pkgver}
  echo "CPPFLAGS+=${CPPFLAGS}" >> config.mk
  echo "CFLAGS+=${CFLAGS}" >> config.mk
  echo "LDFLAGS+=${LDFLAGS}" >> config.mk
  cat ../0001-line-height.patch         | patch -p1
  cat ../0002-xyw.patch                 | patch -p1
  cat ../0003-separator.patch           | patch -p1
  cat ../0004-fuzzy-search.patch        | patch -p1
  cat ../0005-lines-below-prompt.patch  | patch -p1
  cat ../0006-password.patch            | patch -p1
  cat ../0007-password-top-offset.patch | patch -p1
  cat ../0008-no-options.patch          | patch -p1
  cat ../0009-center.patch              | patch -p1
  cat ../0010-naoto-theme.patch         | patch -p1
}

build() {
  cd ${pkgname}-${pkgver}
  make \
	  X11INC=/usr/include/X11 \
	  X11LIB=/usr/lib/X11 \
	  FREETYPEINC=/usr/include/freetype2
}

package() {
  cd ${pkgname}-${pkgver}
  make PREFIX=/usr DESTDIR="${pkgdir}" install
  install -Dm 644 LICENSE -t "${pkgdir}/usr/share/licenses/${pkgname}"
}

# vim: ts=2 sw=2 et:
