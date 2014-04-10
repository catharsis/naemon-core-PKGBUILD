# Maintainer: Anton Löfgren <anton.lofgren@gmail.com>
_name=naemon
pkgname=$_name-core
pkgver=0.8.0
pkgrel=1
pkgdesc="A host/service/network monitoring and management system"
arch=('x86_64')
url="http://www.naemon.org"
license=('GPL2')
depends=('sh')
makedepends=()
checkdepends=()
optdepends=()
provides=()
conflicts=()
replaces=()
backup=()
options=()
changelog=
source=(https://github.com/$_name/$pkgname/archive/v$pkgver.tar.gz)
noextract=()
md5sums=('045db0edf45578b426d3b34b0cec1876') #generate with 'makepkg -g'

build() {
	cd "$srcdir/$pkgname-$pkgver"
	autoreconf -si
	./configure \
		--prefix="/usr" \
		--sysconfdir="/etc/$_name" \
		--localstatedir="/var" \
		--libdir="/usr/lib/" \
		--with-pluginsdir="/usr/lib/$_name/plugins" \
		--datadir="/var/$_name" \
		--with-logrotatedir="/etc/logrotate.d" \
		--with-lockfile="/var/run/$_name/$_name" \
		--with-naemon-user="$_name" \
		--with-naemon-group="$_name"
	make clean
	make
}

check() {
	cd "$srcdir/$pkgname-$pkgver"
	make -k check
}

package() {
	cd "$srcdir/$pkgname-$pkgver"
	make DESTDIR="$pkgdir/" install
}
