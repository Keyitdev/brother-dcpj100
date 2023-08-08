# Config created by Keyitdev https://www.github.com/keyitdev/
# Copyright (C) 2023 Keyitdev
# Of course I stole most of code from someone else.
# This package is pretty shitty but it works on x86_64.

# x86_64 users should also install 'lib32-libcups' package. 
# To install lib32-libcups you must enable Multilib repository in pacman.
# If you want to use dcpj100 scanner install 'simple-scan' 'brscan4' packages.
# Remember also to enable cups (systemctl).
# Remember to add user to lp group using gpasswd -a <USER> lp

pkgname=brother-dcpj100-keyitdev-version
pkgver=3.0.0
pkgrel=3
pkgdesc="Driver for the Brother DCP-J100 multifuncional printer"
url="http://solutions.brother.com/linux/en_us/index.html"
license=('custom:brother')
depends=('a2ps' 'tcsh' 'cups' 'libcups' 'lib32-libcups' 'system-config-printer')
install="brother-dcpj100.install"
arch=('i686' 'x86_64')

md5sums=('497e5f908d843189a0e3a9671b74ae7d'
         'ee9f4388a008467c4f65f5aa3883c764'
         'ee4525fb5900c9224a61732ec30d434a')

source=(
   "fix_lp.patch" \
   "https://download.brother.com/welcome/dlf100906/dcpj100lpr-$pkgver-1.i386.rpm" \
	"https://download.brother.com/welcome/dlf100908/dcpj100cupswrapper-$pkgver-1.i386.rpm"
)

build() {
   cd "$srcdir"
   patch -Np0 < fix_lp.patch
}

post_install() {
   /opt/brother/Printers/dcpj100/cupswrapper/cupswrapperdcpj100
}

package()
{
   install -d $pkgdir/usr/bin
   install -d $pkgdir/var/spool/lpd
   install -Dm755 "$srcdir"/usr/bin/brprintconf_dcpj100 "$pkgdir"/usr/bin/
   cp -R $srcdir/opt $pkgdir/opt
}
