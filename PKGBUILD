pkgname=fpc-i386-win32-directx
pkgver=20070501
pkgrel=2
pkgdesc="Minimal Free Pascal headers for DirectX 9 (i386-win32)"
arch=(any)
url="http://msdn.microsoft.com/directx"
license=("unknown")
depends=(fpc-i386-win32-rtl)
makedepends=(ppcross386 mingw-w64-binutils)
options=(!strip)
source=("http://www.clootie.ru/fpc/files/FPC_DirectX92.zip")
md5sums=('1faffde17a88df1c1f939eb71b2b28bb')
_fpcver=`fpc -iV`

build() {
  cd "${srcdir}"
  for file in `ls *.pas`
  do
    ppcross386 -Twin32 $file
  done
}

package() {
  cd "${srcdir}"
  find . -name '*.o' -o -name '*.ppu' -o -name '*.rst' -o -name '*.a' |
    xargs -rtl1 -I {} install -Dm644 {} "$pkgdir/usr/lib/fpc/$_fpcver/units/i386-win32/directx/"{}
  find $pkgdir -name '*.o' -o -name '*.a' | xargs -rtl1 i686-w64-mingw32-strip -g
}
