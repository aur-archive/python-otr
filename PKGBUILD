# Contributor: Andre Klitzing <aklitzing () online () de>
# Contributor: Ute <moc liamg msg_omh <- backwards >
# Contributor: mutantmonkey <mutantmonkey@mutantmonkey.in>

pkgname=python-otr
pkgver=0.2.2
_pkgver=0.2.1.1
pkgrel=2
pkgdesc="Simple python bindings for OTR"
arch=('any')
url="http://python-otr-old.pentabarf.de"
license=('GPL')
depends=('libotr>=3.2.0' 'python2')
makedepends=('swig')
conflicts=('pyotr')
replaces=('pyotr')
source=(http://$pkgname-old.pentabarf.de/releases/$pkgname-$_pkgver.tar.gz
         http://$pkgname-old.pentabarf.de/releases/patches/$pkgname-0.2.2.patch)
md5sums=('e753e6516d611d0c37a3fc785fb29b21'
         'c6615caeccfad5d9d0e3c2596390f88e')
sha256sums=('9395ce816452aee28e0ae003c66433a67e65f2bf8390cbefb247b657e0c840b1'
             '72654726d127bb051e5efbcf11c7bf505334d6c6aa19799b358e2eb067ade888')

build() {
    cd "${srcdir}/${pkgname}-${_pkgver}"

    patch -Np0 -i ../$pkgname-0.2.2.patch

    # Great python3 rebuild
    for file in $(find . -name '*.py' -print); do
    sed -i 's_^#!.*/usr/bin/python_#!/usr/bin/python2_' "${file}"
    sed -i 's_^#!.*/usr/bin/env.*python_#!/usr/bin/env python2_' "${file}"
    done

    python2 setup.py build
}

package() {
    cd "${srcdir}/${pkgname}-${_pkgver}"

    python2 setup.py install --prefix=/usr --root="${pkgdir}"
}

