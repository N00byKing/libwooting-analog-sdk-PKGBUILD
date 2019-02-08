_gitname=wooting-analog-sdk
pkgname="libwooting-analog-sdk-git"
url='https://github.com/N00byKing/wooting-analog-sdk'
arch=("x86_64")
pkgver=ae00066
pkgrel=1
pkgdesc="Wooting Keyboard Analog SDK"
provides=('libwooting-analog-sdk')
conflicts=('libwooting-analog-sdk')
depends=('libusb')
makedepends=('git' 'hidapi' 'libusb')
license=('MPL2')
source=('git+https://github.com/N00byKing/wooting-analog-sdk')
md5sums=(SKIP)

pkgver() {
    cd "$_gitname"
    git rev-parse --short HEAD
}

build() {
    cd "$srcdir/$_gitname"
    git submodule update --init
    cd linux
    make
}

package() {
    cd "$srcdir/$_gitname/linux"
    install -Dm755 libwooting-analog-sdk.so "$pkgdir/usr/lib/libwooting-analog-sdk.so"
    sed "s/VERSION/${pkgver}/" -i libwooting-analog-sdk.pc
    install -Dm644 libwooting-analog-sdk.pc "${pkgdir}/usr/lib/pkgconfig/libwooting-analog-sdk.pc"
    cd "$srcdir/$_gitname/src"
    install -Dm755 wooting-analog-sdk.h "$pkgdir/usr/include/wooting-analog-sdk.h"
    install -Dm755 wooting-scan-codes.h "$pkgdir/usr/include/wooting-scan-codes.h"
}
