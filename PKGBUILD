#Maintainer: steabert <steabert@member.fsf.org>
#Contributor: Ricardo Honorato Z.
#Modified for personal use by: badbodh
pkgname=vmd
pkgver=1.9.2
pkgrel=2
pkgdesc="Visual Molecular Dynamics"
license=('custom')
arch=('x86_64')
depends=('tcsh' 'perl' 'libxi' 'tcl' 'libxinerama' 'libgl' 'glu')
makedepends=('make')
optdepends=('netcdf: MMTK and AMBER 9 trajectories support'
            'openbabel: additional file formats support'
            'sqlite: dmsplugin')

# You MUST download the package from the VMD url and put it in the PKGBUILD folder!
[ "$CARCH" = "x86_64" ] && source=(${pkgname}-${pkgver}.bin.LINUXAMD64.opengl.tar.gz)

[ "$CARCH" = "x86_64" ] && md5sums=('ff8b8a761822ebbb9be0e9f450d123b0')

package() {
  cd $srcdir/${pkgname}-${pkgver}
  install -D -m644 LICENSE ${pkgdir}/usr/share/licenses/$pkgname/LICENSE
  export VMDINSTALLBINDIR="${pkgdir}/usr/bin"
  export VMDINSTALLLIBRARYDIR="${pkgdir}/usr/lib/vmd"
  ./configure
  cd src; make install
  sed -i 's|set defaultvmddir=.*|set defaultvmddir=/usr/lib/vmd|' "${pkgdir}/usr/bin/vmd"
}

