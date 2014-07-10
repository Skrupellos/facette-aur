# Maintainer: Nicolas Leclercq <nicolas.private@gmail.com>

pkgname=facette
pkgver=0.1.0
pkgrel=1
epoch=
pkgdesc='Facette is a software to display time series data from several various sources'
arch=('i686' 'x86_64')
url='http://facette.io/'
license=('BSD')
groups=()
depends=('go' 'rrdtool')
makedepends=('nodejs')
checkdepends=()
optdepends=()
provides=('facette')
conflicts=()
replaces=()
backup=()
options=()
install='facette.install'
changelog=
source=(
	"https://github.com/facette/facette/releases/download/$pkgver/$pkgname-$pkgver-linux-amd64.tar.gz"
	'facette.service'
	'facette.install')
noextract=()
md5sums=(
	'130a4c5471ce39219233d34e1d16bf7e'
	'd1e55b27ca233bba20d320113bc1a906'
	'ade342a98ade039939cf354580b12651')

package() {
  cd "$srcdir/$pkgname-linux-amd64"

	# create target directory structure
	mkdir -p ${pkgdir}/{usr/bin,usr/share/facette,usr/share/facette/man,etc/facette,var/log/facette,var/run/facette}

	# binaries
	cp bin/{facette,facettectl} ${pkgdir}/usr/bin

  # static content
  cp -r share/facette/{examples,static,template} ${pkgdir}/usr/share/facette

  # man
  cp -r share/man ${pkgdir}/usr/share/facette

	# default config
	cp -r share/facette/examples/{facette.json,providers} ${pkgdir}/etc/facette

	# copy systemd service file
	install -D -m644 $srcdir/facette.service $pkgdir/usr/lib/systemd/system/facette.service
}

