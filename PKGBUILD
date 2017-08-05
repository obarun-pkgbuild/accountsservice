# Maintainer: Eric Vidal <eric@obarun.org>
# based on the original https://projects.archlinux.org/svntogit/packages.git/tree/trunk?h=packages/accountsservice
# 						Maintainer: Ionut Biru <ibiru@archlinux.org>

pkgname=accountsservice
pkgver=0.6.45
pkgrel=2
pkgdesc="D-Bus interface for user account query and manipulation"
arch=(i686 x86_64)
url="http://www.freedesktop.org/software/accountsservice/"
license=('GPL3')
depends=('glib2' 'polkit')
makedepends=('intltool' 'gtk-doc' 'gobject-introspection' 'git')
_commit=db223bc474b5ae914f2c6ff4d07c69d747cfeda7  # tags/0.6.45^0
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
				--libexecdir=/usr/lib/accountsservice \
				--localstatedir=/var \
				--disable-static \
				--enable-gtk-doc
  make
}

package() {
  cd ${pkgname}
  make DESTDIR="$pkgdir" install
}

# vim:set ts=2 sw=2 et:
