# Contributor: kasa <biuta.jr@gmail.com>

pkgname=modem-manager
pkgver=20090320
pkgrel=1
pkgdesc="Modem management service"
arch=(i686 x86_64)
license=('GPL')
url="http://www.gnome.org/projects/NetworkManager/"
depends=('dbus-glib' 'glib2' 'hal')
makedepends=('git' 'pkgconfig')
options=('!libtool')
provides=()
conflicts=()

source=()
md5sums=()

_gitroot="http://git.gitorious.org/modemmanager/mainline.git"
_gitname="modemmanager"

build() {
  cd ${srcdir}

  msg "Connecting to git.freedesktop.org GIT server...."

  if [ -d ${srcdir}/$_gitname ] ; then
    cd $_gitname && git pull origin
    msg "The local files are updated."
  else
    git clone $_gitroot $_gitname
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting make..."

  cd ${srcdir}/$_gitname

  ./autogen.sh --prefix=/usr --sysconfdir=/etc \
    --localstatedir=/var --disable-static

    make || return 1
    make DESTDIR="${pkgdir}" install || return 1

}

