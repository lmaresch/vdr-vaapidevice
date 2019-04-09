# This PKGBUILD could be part of the VDR4Arch project [https://github.com/vdr4arch]

pkgname=vdr-vaapidevice
pkgver=0.11.r1.a17c110
_gitver=a17c11072e7f9465f12830e6d3045956d4cb2776
_vdrapi=2.4.0
pkgrel=1
pkgdesc="The plugin provides an EPG (Electronic Program Guide) similar to the built-in one, but with extra features."
url="https://github.com/pesintta/vdr-plugin-vaapidevice"
arch=('x86_64' 'i686' )
license=('GPL2')
depends=("vdr-api=${_vdrapi}")
_plugname=${pkgname//vdr-/}
source=("vdr-plugin-${_plugname}::git+https://github.com/pesintta/vdr-plugin-vaapidevice#commit=$_gitver"
        "50-$_plugname.conf")
backup=("etc/vdr/conf.avail/50-$_plugname.conf")
sha512sums=('SKIP'
         'SKIP')

pkgver() {
    cd "${srcdir}/vdr-plugin-${_plugname}"
    git describe --long --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g;s/^v//'

}

prepare() {
    cd "${srcdir}/vdr-plugin-${_plugname}"
}

build() {
    cd "${srcdir}/vdr-plugin-${_plugname}"
    make
}

package() {
    cd "${srcdir}/vdr-plugin-${_plugname}"
    make DESTDIR="${pkgdir}" install

    install -Dm644 "$srcdir/50-$_plugname.conf" "$pkgdir/etc/vdr/conf.avail/50-$_plugname.conf"
}
