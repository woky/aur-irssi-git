# Maintainer: Lin Rs <lin dot ruohshoei+arch at gmail dot com>
# Contributor: Randy Ramos <rramos1295@gmail.com>
# Contributor: Reventlov <contact+aur@volcanis.me>
# Contributor: sudokode <sudokode@gmail.com>
# Contributor: Bartłomiej Piotrowski <nospam@bpiotrowski.pl>
# Contributor: Zariel <c.bannister@gmail.com>

pkgname=irssi-git
pkgver=1.3.dev.r9.g26d96a7b
pkgrel=1
pkgdesc="Modular text mode IRC client with Perl scripting"
arch=('x86_64')
url="https://irssi.org/"
license=('GPL')
depends=('glibc' 'glib2' 'openssl' 'libotr' 'perl' 'ncurses' 'libncursesw.so')
makedepends=('git' 'meson' 'ninja')
optdepends=('perl-libwww: For the scriptassist script')
conflicts=('irssi')
provides=('irssi')
backup=('etc/irssi.conf')
source=("${pkgname}"::"git+https://github.com/irssi/irssi.git")
sha256sums=('SKIP')

pkgver() {
  cd "${pkgname}"
  git describe --long --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}

build() {
  cd "${pkgname}"
  meson Build \
    -Dprefix=/usr \
    -Dsysconfdir=/etc \
    -Dwith-proxy=yes \
    -Dwith-per-lib=vendor \
    -Dwith-otr=yes \
    -Denable-true-color=yes
  ninja -C Build
}

package() {
  cd "${pkgname}"
  DESTDIR="${pkgdir}" ninja -C Build install
}

# vim: ts=2 sw=2 et:
