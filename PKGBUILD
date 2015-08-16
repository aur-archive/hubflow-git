# Maintainer: Mateusz Loskot <mateusz at loskot dot net>
# Contributor: Xyne <xyne at archlinux dot ca>
# Contributor: Christoph Seitz <seitz dot christoph at gmail dot com>
pkgname=hubflow-git
pkgver=20130323
pkgrel=1
pkgdesc="A Git extension to make it easy to use GitFlow with GitHub."
arch=('any')
url="http://github.com/datasift/gitflow"
license=('BSD')
depends=('git')

_gitroot="git://github.com/datasift/gitflow.git"
_gitname="hubflow"

build() {
  msg "Connecting to GIT server"
  if [[ -d "$srcdir/$_gitname" ]] ; then
    cd "$srcdir/$_gitname" && git pull origin
    msg "The local files are updated."
  else
    git clone $_gitroot $_gitname
  fi
  msg "GIT checkout done or server timeout"

  msg "Getting submodule"
  cd "$srcdir/$_gitname"
  git submodule init
  git submodule update
  msg "Submodule checkout done or server timeout"
}

package() {
  cd "$srcdir/$_gitname"
  INSTALL_INTO="$pkgdir/usr/bin" ./install.sh
  
  install -Dm644 "$srcdir/$_gitname/LICENSE" \
    "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

# vim:set ts=2 sw=2 et:
