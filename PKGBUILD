# Maintainer: asdfer <>

# Original Maintainer: Jan-Erik Rediger <badboy at archlinux dot us>
# Contributor: Thorsten Toepper <atsutane at freethoughts dot de>
# Contributor: William Giokas <1007380@gmail.com>

# This PKGBUILD was prepared for pacman 4.1 by William. Thank you. :-)
# Aaand me, asdfer, copied this PKGBUILD for a fork of mine, Thank you also. :-D

pkgname=i3-asdfer-git
pkgver=4.21.r4.g09670218
pkgrel=1
pkgdesc='asdfer i3 fork'
arch=('i686' 'x86_64')
url='http://i3wm.org/'
license=('BSD')
provides=('i3-wm')
conflicts=('i3-wm' 'i3-git' 'i3-gaps' 'i3-gaps-next-git')
groups=('i3' 'i3-vcs')
depends=('xcb-util-keysyms' 'xcb-util-wm' 'libev' 'yajl'
         'startup-notification' 'pango' 'perl' 'xcb-util-cursor' 'xcb-util-xrm'
         'libxkbcommon-x11')
makedepends=('git' 'bison' 'flex' 'asciidoc' 'xmlto' 'meson')
optdepends=('i3lock: For locking your screen.'
            'i3status: To display system information with a bar.')
options=('docs')
source=('git+https://github.com/asdfer-1234/i3#branch=stable')
sha1sums=('SKIP')

pkgver() {
  cd "$srcdir/i3"
  git describe --long | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}


build() {
  cd "i3"
  arch-meson \
    -Ddocs=true \
    -Dmans=true \
  ../build
  meson compile -C ../build
}

package() {
  cd "i3"
  DESTDIR="${pkgdir}" meson install -C ../build

  install -Dt "${pkgdir}/usr/share/licenses/${pkgname}" -m644 LICENSE
}
