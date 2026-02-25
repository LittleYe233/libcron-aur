# Maintainer: LittleYe233 <littleye233@gmail.com>
# Maintainer: hellopoisonx <x1665341912@gmail.com>
# Contributor: Atom Long <atom.long@hotmail.com>

pkgname=libcron
pkgver=1.3.3
pkgrel=1
pkgdesc='A C++ scheduling library using cron formatting.'
url='https://github.com/PerMalmberg/libcron'
arch=('x86_64' 'i686' 'arm' 'armv6h' 'armv7h' 'aarch64')
license=('MIT')
conflicts=("${pkgname}-git")
_date_ver=3.0.4
source=("${pkgname}-${pkgver}.tar.gz::${url}/archive/refs/tags/v${pkgver}.tar.gz"
        "date-${_date_ver}.tar.gz::https://github.com/HowardHinnant/date/archive/refs/tags/v${_date_ver}.tar.gz")
sha256sums=('7d413b7950c82b54157b2a7f446e1e660bd718e542e2ffd3f8715e467ab2b825'
            '56e05531ee8994124eeb498d0e6a5e1c3b9d4fccbecdf555fe266631368fb55f')
makedepends=('cmake')
options=('!strip')

prepare() {
  cd ${pkgname}-${pkgver}
  cp -rf "${srcdir}/date-${_date_ver}" -T libcron/externals/date
}

build() {
  cd ${pkgname}-${pkgver}
  cmake -DCMAKE_BUILD_TYPE=Release .
  make libcron
}

package() {
  cd ${pkgname}-${pkgver}
  install -Dm644 libcron/out/Release/liblibcron.a -t ${pkgdir}/usr/lib/
  install -Dm644 libcron/include/libcron/* -t ${pkgdir}/usr/include/libcron/
  install -Dm644 libcron/externals/date/include/date/* -t ${pkgdir}/usr/include/date/
}
