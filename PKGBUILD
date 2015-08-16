# Maintainer: lilydjwg <lilydjwg@gmail.com>

pkgname=lualogging-lilydjwg-git
pkgver=20121121
pkgrel=1
pkgdesc="LuaLogging provides a simple API to use logging features in Lua. With HTML docs and lilydjwg's modification."
url="https://github.com/lilydjwg/lualogging"
arch=('any')
license=('MIT')
depends=('lua>=5.1' 'lua<5.2')
makedepends=('git')
conflicts=('lualogging' 'lualogging-git')
provides=('lualogging' 'lualogging-git')
source=()
md5sums=()

_gitroot=git://github.com/lilydjwg/lualogging.git
_gitname=lualogging

build() {
  cd "$srcdir"
  msg "Connecting to the GIT server...."

  if [[ -d $srcdir/$_gitname ]] ; then
    cd $_gitname
    git pull origin
    msg "The local files are updated."
  else
    git clone $_gitroot $_gitname
  fi

  cd "$srcdir/$_gitname"
  make
}
package(){
  cd "$srcdir/$_gitname"
  make PREFIX=$pkgdir/usr install
  _docdir="$pkgdir/usr/share/doc/lualogging"
  mkdir -p $_docdir
  cp -r doc/html/* $_docdir
  install -Dm644  "COPYRIGHT" "$pkgdir/usr/share/licenses/lualogging/LICENSE"
  find $pkgdir -type f -exec chmod 644 {} \;
}
# vim:syntax=sh:sw=2
