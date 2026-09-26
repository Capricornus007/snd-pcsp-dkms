_pkgbase=snd-pcsp
pkgname=${_pkgbase}-dkms
pkgver=7.2.8
pkgrel=1
pkgdesc="An in-tree driver for the PC speaker which allows it to act like a primitive sound card (DKMS)"
arch=('x86_64')
url="https://www.kernel.org/"
license=('GPL2')
depends=('dkms')
conflicts=("${_pkgbase}")
source=("https://www.kernel.org/pub/linux/kernel/v${pkgver%%.*}.x/linux-${pkgver}.tar.xz"
        'dkms.conf')
sha512sums=('f5d9e366f026dba2853f48ea81d3a0cd9ecad1462aba52fbc160c5cdd3a3c657f0f008e1dd07ddfb0a05047421223ef6c1da8e43d47c85f11c71b6bd30ce0213'
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
