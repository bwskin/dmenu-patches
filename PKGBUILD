pkgname=dmenu
pkgver=5.0
pkgrel=1
pkgdesc='Generic menu for X'
url='https://tools.suckless.org/dmenu/'
arch=('x86_64')
license=('MIT')
depends=('sh' 'glibc' 'coreutils' 'libx11' 'libxinerama' 'libxft' 'freetype2' 'fontconfig' 'libfontconfig.so')
source=(
  https://dl.suckless.org/tools/dmenu-${pkgver}.tar.gz
  0000-dmenu-lineheight.patch
  0001-dmenu-xyw.patch
  0002-dmenu-separator.patch
  0003-dmenu-fuzzy.patch
  0004-dmenu-lines-below-prompt.patch
  0005-dmenu-password.patch
  0006-dmenu-password-top-offset.patch
  0007-no_options_mode.patch
  0008-center_parameter.patch
  0009-theme-by-naoto.patch
)
sha256sums=('fe18e142c4dbcf71ba5757dbbdea93b1c67d58fc206fc116664f4336deef6ed3' 'SKIP' 'SKIP' 'SKIP' 'SKIP' 'SKIP' 'SKIP' 'SKIP' 'SKIP' 'SKIP' 'SKIP')

prepare() {
  cd ${pkgname}-${pkgver}
  echo "CPPFLAGS+=${CPPFLAGS}" >> config.mk
  echo "CFLAGS+=${CFLAGS}" >> config.mk
  echo "LDFLAGS+=${LDFLAGS}" >> config.mk
  cat ../0000-dmenu-lineheight.patch          | patch -p1
  cat ../0001-dmenu-xyw.patch                 | patch -p1
  cat ../0002-dmenu-separator.patch           | patch -p1
  cat ../0003-dmenu-fuzzy.patch               | patch -p1
  cat ../0004-dmenu-lines-below-prompt.patch  | patch -p1
  cat ../0005-dmenu-password.patch            | patch -p1
  cat ../0006-dmenu-password-top-offset.patch | patch -p1
  cat ../0007-no_options_mode.patch           | patch -p1
  cat ../0008-center_parameter.patch          | patch -p1
  cat ../0009-theme-by-naoto.patch            | patch -p1
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
