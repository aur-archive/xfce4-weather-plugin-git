# Contributor: Lex Black <autumn-wind at web dot de>
# Contributor: Baurzhan Muftakhidinov <baurthefirst@gmail.com>
# Maintainer: twa022 <twa022 at gmail dot com>

_pkgname=xfce4-weather-plugin
pkgname=${_pkgname}-git
pkgver=20121231
pkgrel=1
pkgdesc="A weather plugin for the Xfce4 panel"
arch=('i686' 'x86_64')
license=('GPL2')
url="http://www.xfce.org"
groups=('xfce4-git')
depends=('xfce4-panel' 'libxml2' 'hicolor-icon-theme')
makedepends=('git' 'xfce4-dev-tools')
conflicts=('xfce4-weather-plugin')
provides=('xfce4-weather-plugin')
options=('!libtool')
md5sums=()
install=${_pkgname}.install


_gitroot="git://git.xfce.org/panel-plugins/xfce4-weather-plugin/"
_gitname="$_pkgname"

build() {
    
    cd $srcdir
    msg "Getting sources..."
    
    if [ -d "$srcdir/$_gitname" ] ; then
	 cd $_gitname && git pull origin
	 msg "The local files are updated."
	else
	 git clone $_gitroot
	fi

msg "GIT checkout done or server timeout"
msg "Starting build..."
    

	cd $srcdir/$_pkgname
    
  ./autogen.sh --prefix=/usr --sysconfdir=/etc --libexecdir=/usr/lib  \
    --localstatedir=/var --disable-static  --enable-debug=minimum \
   --enable-maintainer-mode

  make
}

package() {
  cd $srcdir/$_pkgname
  make DESTDIR=$pkgdir install
}
