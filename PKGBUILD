# Maintainer: Felix Yan <felixonmars@archlinux.org>

pkgbase=python-hyperlink
pkgname=('python-hyperlink' 'python2-hyperlink')
pkgver=17.1.1
pkgrel=1
pkgdesc='A featureful, correct URL for Python'
arch=('any')
license=('BSD')
url='https://github.com/python-hyper/hyperlink'
makedepends=('python-setuptools' 'python2-setuptools')
checkdepends=('python-pytest-runner' 'python2-pytest-runner')
source=("$pkgbase-$pkgver.tar.gz::https://github.com/python-hyper/hyperlink/archive/v$pkgver.tar.gz")
sha512sums=('abf433672dd42e90ebe14b89eff9150ea42c15aa446e24995e625be81a19b727cb2bb5723cb84446d09936266b1957d7cb4df461665650430bda12720ae192d1')

prepare() {
  cp -a hyperlink-$pkgver{,-py2}
}

build() {
  cd "$srcdir"/hyperlink-$pkgver
  python setup.py build

  cd "$srcdir"/hyperlink-$pkgver-py2
  python2 setup.py build
}

check() {
  cd "$srcdir"/hyperlink-$pkgver
  python setup.py pytest

  cd "$srcdir"/hyperlink-$pkgver-py2
  python2 setup.py pytest
}

package_python-hyperlink() {
  depends=('python')

  cd hyperlink-$pkgver
  python setup.py install --root="$pkgdir" --optimize=1
  install -D -m644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}

package_python2-hyperlink() {
  depends=('python2')

  cd hyperlink-$pkgver-py2
  python2 setup.py install --root="$pkgdir" --optimize=1
  install -D -m644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}

# vim:set ts=2 sw=2 et:
