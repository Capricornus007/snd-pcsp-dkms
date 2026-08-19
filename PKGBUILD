_pkgbase=snd-pcsp
pkgname=${_pkgbase}-dkms
pkgver=7.2
pkgrel=1
pkgdesc="An in-tree driver for the PC speaker which allows it to act like a primitive sound card (DKMS)"
arch=('x86_64')
url="https://www.kernel.org/"
license=('GPL2')
depends=('dkms')
conflicts=("${_pkgbase}")
source=("https://www.kernel.org/pub/linux/kernel/v${pkgver%%.*}.x/linux-${pkgver}.tar.xz"
        'dkms.conf')
sha512sums=('47e63679363261a864d271277340a6f2d45f544e1a056be4159df081f4f6537d0efa865c4af26611ab33a3079ee65db88ec2f6bc0e5fff43e0c043cde0cd91e1'
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
