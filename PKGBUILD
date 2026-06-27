# Maintainer: Jim Madge <jim+aur@jmadge.com>
pkgname=kodi-addon-visualization-starburst
pkgver=21.0.2
_kodiversion="Omega"
pkgrel=1
pkgdesc="StarBurst visualization for Kodi"
arch=('any')
url="https://github.com/xbmc/visualization.starburst"
license=('GPL-2.0-only')
depends=('kodi')
makedepends=(
	'cmake'
  'glm'
	'kodi-dev'
)
source=("https://github.com/xbmc/visualization.starburst/archive/refs/tags/${pkgver}-${_kodiversion}.tar.gz")
sha256sums=('a3f70985fee6b1014e7e7599431e646f36bd3870ead78bbc8936151b805e4241')

prepare() {
	mkdir -p "${srcdir}/visualization.starburst-${pkgver}-${_kodiversion}/build"
}

build() {
	cd "${srcdir}/visualization.starburst-${pkgver}-${_kodiversion}/build"
	cmake \
		-DCMAKE_INSTALL_PREFIX=/usr/share/kodi/addons \
		-DCMAKE_BUILD_TYPE=Release \
		-DBUILD_SHARED_LIBS=1 \
		-DPACKAGE_ZIP=1 \
		../
	make
}

package() {
	cd "${srcdir}/visualization.starburst-${pkgver}-${_kodiversion}/build"
	make DESTDIR="$pkgdir/" install
}
