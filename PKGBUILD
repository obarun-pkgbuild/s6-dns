# Maintainer: Eric Vidal <eric@obarun.org>

pkgname=s6-dns
pkgver=2.2.0.1
pkgrel=1
pkgdesc="A suite of DNS client programs and libraries for Unix systems"
arch=(x86_64)
url="http://skarnet.org/software/s6/"
license=('ISC')
depends=(skalibs)
groups=(s6-suite)
conflicts=('s6-dns-git')
source=("$pkgname::git+git://git.skarnet.org/s6-dns#commit=$_commit")
_commit=123c9ff1dff1f28046f1a73503b61c29051cd7f6 # tag 2.2.0.1
sha256sums=('SKIP')
validpgpkeys=('6DD4217456569BA711566AC7F06E8FDE7B45DAAC') # Eric Vidal

build() {
  cd ${srcdir}/${pkgname}
  ./configure --prefix=/usr \
			  --bindir=/usr/bin \
			  --sbindir=/usr/bin \
			  --datadir=/etc
  make
}

package() {
  cd ${srcdir}/${pkgname}

  DESTDIR=${pkgdir} make install
  
  # add doc
  install -dm 0755 $pkgdir/usr/share/doc/$pkgname/
  cp -R doc/* $pkgdir/usr/share/doc/$pkgname/
  
  install -D -m644 COPYING "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
  
}

