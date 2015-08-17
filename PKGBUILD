# Maintainer: Andy Weidenbaum <archbaum@gmail.com>

pkgname=vim-file-line-git
pkgver=20140711
pkgrel=1
pkgdesc="Open a file in Vim on a given line"
arch=('any')
depends=('vim')
makedepends=('git')
groups=('vim-plugins')
url="https://github.com/bogado/file-line"
license=('GPL3')
source=(${pkgname%-git}::git+https://github.com/bogado/file-line)
sha256sums=('SKIP')
provides=('vim-file-line')
conflicts=('vim-file-line')
install=vimdoc.install

pkgver() {
  cd ${pkgname%-git}
  git log -1 --format="%cd" --date=short | sed "s|-||g"
}

package() {
  cd ${pkgname%-git}

  msg 'Installing docs...'
  install -Dm 644 README.md "$pkgdir/usr/share/doc/vim-file-line/README.md"

  msg 'Installing dirs...'
  install -dm 755 "$pkgdir/usr/share/vim/vimfiles"
  for _dir in plugin; do
    cp -dpr --no-preserve=ownership $_dir "$pkgdir/usr/share/vim/vimfiles/$_dir"
  done

  msg 'Cleaning up pkgdir...'
  find "$pkgdir" -type d -name .git -exec rm -r '{}' +
}
