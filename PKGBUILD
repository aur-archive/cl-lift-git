# Maintainer: DavidK <david_king at softhome dot net>
# Contributor:  mrshpot <mrshpot at gmail dot com>
# Contributor:  veox <box 55 [shift-two] mail [dot] ru>

pkgname=cl-lift-git
_clname=lift   # used in CL scope, not package scope
pkgver=r530.10331cd
pkgrel=2
pkgdesc="Lisp Framework For Testing for Common Lisp"
arch=('any')
url="http://common-lisp.net/project/lift/"
license=('custom')
provides=('cl-lift')
conflicts=('cl-lift-darcs')
depends=('common-lisp')
makedepends=('git') 
install=cl-lift.install
source=("$pkgname"::'git+https://github.com/gwkkwg/lift')
md5sums=('SKIP')
options=('docs')

pkgver() {
  cd "$srcdir/$pkgname"
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

package() {
    for _dir in compare data dev docs examples test timeout; do
        install -d "${pkgdir}"/usr/share/common-lisp/source/${_clname}/${_dir}
    done
    install -d "${pkgdir}"/usr/share/common-lisp/systems
    install -d "${pkgdir}"/usr/share/licenses/${pkgname}

    cd "$srcdir/$pkgname"
    install -m 644 -t "${pkgdir}"/usr/share/common-lisp/source/${_clname}/ \
		lift-standard.config
    for _dir in compare data dev docs examples test timeout; do
        install -m 644 -t "${pkgdir}"/usr/share/common-lisp/source/${_clname}/${_dir}/ \
            ${_dir}/*
    done
    install -m 644 -t "${pkgdir}"/usr/share/common-lisp/source/${_clname} \
        *.asd
    install -m 644 -t "${pkgdir}"/usr/share/licenses/${pkgname} \
        "${srcdir}/$pkgname/COPYING"

    cd "${pkgdir}"/usr/share/common-lisp/systems
    ln -s ../source/${_clname}/${_clname}.asd .
    ln -s ../source/${_clname}/${_clname}-documentation.asd .
    ln -s ../source/${_clname}/${_clname}-test.asd .
}
