# Maintainer: Eric Vidal <eric@obarun.org>
# based on the original https://projects.archlinux.org/svntogit/packages.git/tree/trunk?h=packages/accountsservice
# 						Maintainer: Ionut Biru <ibiru@archlinux.org>

pkgname=accountsservice
pkgver=0.6.47
pkgrel=2
pkgdesc="D-Bus interface for user account query and manipulation"
arch=(x86_64)
url="http://www.freedesktop.org/software/accountsservice/"
license=('GPL3')
depends=('glib2' 'polkit')
makedepends=('intltool' 'gtk-doc' 'gobject-introspection' 'git')
_commit=27fbd25251c3dd59c4d8e999a902946feab73f5a # tags/0.6.46^0
source=("git+https://anongit.freedesktop.org/git/accountsservice#commit=$_commit")
sha256sums=('SKIP')
validpgpkeys=('6DD4217456569BA711566AC7F06E8FDE7B45DAAC') # Eric Vidal

#pkgver() {
#  cd $pkgname
#  git describe --tags | sed 's/-/+/g'
#}

 prepare() {
  cd $pkgname
  NOCONFIGURE=1 ./autogen.sh
}

build() {
  cd ${pkgname}
  ./configure 	--prefix=/usr \
				--sysconfdir=/etc \
				--libexecdir=/usr/lib/ \
				--localstatedir=/var \
				--disable-static \
				--enable-gtk-doc \
				--disable-systemd \
				--disable-elogind
  make
}

package() {
  cd ${pkgname}
  make DESTDIR="$pkgdir" install
}

# vim:set ts=2 sw=2 et:
