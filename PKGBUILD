# Maintainer: Gustavo Castro << gustawho [at] gmail [dot] com >>
pkgname=sushi4physics-2hdmc
_srcname=SusHi
pkgver=1.4.1
pkgrel=2
pkgdesc="Higgs production in the 2HDM (2HDMC support)"
url="http://sushi.hepforge.org/"
arch=('x86_64')
license=('GPLv2')
depends=('lhapdf' '2hdmc')
makedepends=('gcc-fortran')
provides=('sushi4physics')
conflicts=('sushi4physics' 'sushi4physics-fh' 'sushi4physics-hb')
source=("http://www.hepforge.org/archive/sushi/${_srcname}-${pkgver}.tar.gz"
        "2hdmc.patch")
sha512sums=('3033c35551fc6ba50afef00cf7facccbae7c82b63f90df293167e7318e35576ef6033b94b68ce6330d43b4c61416e5d5589a118c6b7389cf2ba96c0148e0c5ff'
            '99d165b5625214955bb14794e7a39331b150ca75fe86bb1bfb040270323f45f0a1f1860b3be9d0a2a6143044291d1bb456cf52d8da572f7df82e41329b5b14da')

build() {
  patch "${srcdir}/${_srcname}-${pkgver}/Makefile" < "${srcdir}/2hdmc.patch"
  cd "${srcdir}/${_srcname}-${pkgver}"
  ./configure --prefix=/usr
  make predef=2HDMC
}

package() {
  mkdir -p "${pkgdir}/usr/bin" "${pkgdir}/usr/lib"
  cd "${srcdir}/${_srcname}-${pkgver}"
  install -m755 bin/sushi.2HDMC "${pkgdir}/usr/bin/sushi.2HDMC"
  install -m755 lib/libshare.a "${pkgdir}/usr/lib/libshare.a"
  install -m755 lib/libsushi2HDMC.a "${pkgdir}/usr/lib/libsushi2HDMC.a"
  ln -s "${pkgdir}/usr/bin/sushi.2HDMC" "${pkgdir}/usr/bin/sushi"
  ln -s "${pkgdir}/usr/lib/libsushi2HDMC.a" "${pkgdir}/usr/lib/libsushi.a"
}

# vim:set ts=2 sw=2 et:
