# Maintainer: Caleb Bassi <calebjbassi@gmail.com>
# Maintainer: Eugen Mayer

pkgname=mons-git
_pkgname=${pkgname%-git}
pkgver=r120.375bbba
pkgrel=1
pkgdesc="KISS and POSIX Shell script to quickly manage three monitors on X"
arch=("any")
url="https://github.com/Ventto/mons"
license=("MIT")
depends=("xorg-xrandr")
makedepends=("git"
             "help2man")
provides=(${_pkgname})
conflicts=(${_pkgname})
source=("git+${url}")
md5sums=("SKIP")

pkgver() {
  cd "${_pkgname}"
  ( set -o pipefail
    git describe --long 2>/dev/null | sed 's/\([^-]*-g\)/r\1/;s/-/./g' ||
    printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
  )
}

prepare() {
  cd ${srcdir}/${_pkgname}
  git submodule update --init --recursive
}

package() {
  cd ${srcdir}/${_pkgname}
  make DESTDIR="${pkgdir}" install
}

