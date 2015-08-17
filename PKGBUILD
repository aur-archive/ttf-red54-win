# Maintainer: 謝致邦 <Yeking@Red54.com>

pkgname=ttf-red54-win
pkgver=8
pkgrel=1
pkgdesc='Microsoft Windows TrueType fonts'
arch=('any')
url='http://msdn.microsoft.com/en-us/evalcenter/jj554510.aspx'
license=('custom')
depends=('fontconfig' 'xorg-fonts-encodings' 'xorg-mkfontscale' 'xorg-mkfontdir')
makedepends=('p7zip' 'wimlib')
provides=('ttf-win8-fonts' 'ttf-win7-fonts' 'ttf-vista-fonts' 'ttf-ms-fonts' 'ttf-tahoma' 'ttf-dejavu' 'ttf-font')
conflicts=('ttf-win8-fonts' 'ttf-win7-fonts' 'ttf-vista-fonts' 'ttf-ms-fonts' 'ttf-tahoma')
install="$pkgname.install"
source=(
http://care.dlservice.microsoft.com/dl/download/5/3/C/53C31ED0-886C-4F81-9A38-F58CE4CE71E8/9200.16384.WIN8_RTM.120725-1247_X86FRE_ENTERPRISE_EVAL_EN-US-HRM_CENA_X86FREE_EN-US_DV5.ISO
)
md5sums=('e0ba8ad5c893dd3f5b83ea77fa4946e7')
PKGEXT='.pkg.tar'

build() {
  cd $srcdir
  7z e 9200.16384.WIN8_RTM.120725-1247_X86FRE_ENTERPRISE_EVAL_EN-US-HRM_CENA_X86FREE_EN-US_DV5.ISO sources/install.wim
  mkdir tmp fonts
  imagex mount install.wim 1 tmp
  cp tmp/Windows/Fonts/{*.ttf,*.ttc} fonts
  imagex unmount tmp
}

package() {
  cd $srcdir/fonts
  install -dm755 $pkgdir/usr/share/fonts/win
  install -m644 * $pkgdir/usr/share/fonts/win
}
