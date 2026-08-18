# PKGBUILD For util-linux and util-linux-libs

# Contributor: Janorovic Volkov <janorovicvolkov@gmail.com>
# Maintainer: Janorovic Volkov <janorovicvolkov@gmail.com>

pkgname=util-linux
pkgver=2.42.2
pkgrel=1
pkgdesc="Miscellaneous system utilities for Linux"
arch=('x86_64')
url="https://github.com/util-linux/util-linux"
license=('GPL-2.0-or-later' 'LGPL-2.1-or-later' 'BSD-3-Clause')
depends=('pam' 'shadow' 'libcap-ng' 'zlib' 'ncurses')
makedepends=('meson' 'ninja' 'gettext' 'bzip2' 'cryptsetup' 'pkgconf' 'bison' 'flex')
optdepends=('cryptsetup')
provides=('libblkid' 'libuuid' 'libfdisk' 'libmount' 'libsmartcols')
source=("https://www.kernel.org/pub/linux/utils/util-linux/v2.42/${pkgname}-${pkgver}.tar.xz")
sha256sums=('SKIP')

build() {
    meson setup "${srcdir}/${pkgname}-${pkgver}" build \
        --prefix=/usr \
        --sysconfdir=/etc \
        --localstatedir=/var \
        -Dsystemd=disabled \
        -Dselinux=disabled \
        -Dcryptsetup=enabled \
        -Dcryptsetup-dlopen=enabled
    meson compile -C build
}

package() {
  DESTDIR="${pkgdir}" meson install -C build
  rm -rf "${pkgdir}/usr/lib/systemd"
  rm -rf "${pkgdir}/lib/systemd"
}
