_pkgbase=snd-pcsp
pkgname=${_pkgbase}-dkms
pkgver=7.1.8
pkgrel=1
pkgdesc="An in-tree driver for the PC speaker which allows it to act like a primitive sound card (DKMS)"
arch=('x86_64')
url="https://www.kernel.org/"
license=('GPL2')
depends=('dkms')
conflicts=("${_pkgbase}")
source=("https://www.kernel.org/pub/linux/kernel/v${pkgver%%.*}.x/linux-${pkgver}.tar.xz"
        'dkms.conf')
sha512sums=('e17057478fd498fd4d83c4b6d3712fdfc3c6ae1d077114ea74ee41186cbd75add292f5e5f810fdf41242fd506a476d34447392b1c8194b5e8a6af1a59ac48a74'
            '77a0678e6f1d1eaa7552daa4b8d950afa92d52210fc6fd9d1a17db839408f2fd85fd75334a5cfa0d4589d708c633dc000e5a553f5d9720d0a9cb6474208dc16b')

package() {
  # Copy dkms.conf
  install -Dt "${pkgdir}/usr/src/${_pkgbase}-${pkgver}" -m644 dkms.conf

  # Set name and version
  sed -e "s/@_PKGBASE@/${_pkgbase}/" \
      -e "s/@PKGVER@/${pkgver}/" \
      -i "${pkgdir}"/usr/src/${_pkgbase}-${pkgver}/dkms.conf

  # Copy sources (including Makefile)
  cp -rT linux-${pkgver}/sound/drivers/pcsp "${pkgdir}/usr/src/${_pkgbase}-${pkgver}"
}
