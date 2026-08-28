_pkgbase=snd-pcsp
pkgname=${_pkgbase}-dkms
pkgver=7.2.2
pkgrel=1
pkgdesc="An in-tree driver for the PC speaker which allows it to act like a primitive sound card (DKMS)"
arch=('x86_64')
url="https://www.kernel.org/"
license=('GPL2')
depends=('dkms')
conflicts=("${_pkgbase}")
source=("https://www.kernel.org/pub/linux/kernel/v${pkgver%%.*}.x/linux-${pkgver}.tar.xz"
        'dkms.conf')
sha512sums=('6ca338fd2f9d2224b9187ba1cad18c05417c0504771917203a023467a8ac3a34e346bd3bc5a3f5716aa9810381a28c730ea5fc3726773dca36d75a4677178b13'
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
