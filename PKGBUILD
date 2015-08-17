# $Id: PKGBUILD 66150 2012-02-23 02:16:50Z spupykin $
# Maintainer: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Contributor: Sebastian Pohle <naitsabes@imapmail.org>

pkgname=pmtools
pkgver=20101124
pkgrel=2
pkgdesc="A small collection of ACPI power management test and investigation tools"
arch=('i686' 'x86_64')
url="http://acpi.sourceforge.net/dsdt/index.php"
license=('GPL2')
depends=('perl')
#source=(http://ftp.kernel.org/pub/linux/kernel/people/lenb/acpi/utils/$pkgname-$pkgver.tar.bz2)
source=(http://arch.p5n.pp.ru/~sergej/dl/2011/$pkgname-$pkgver.tar.bz2)
md5sums=('45e62eae9aca4fce84cb102c117f5796')

build() {
  cd "$srcdir/$pkgname"
  patch -p1 <<EOF
diff -wbBur pmtools/turbostat/Makefile pmtools.my/turbostat/Makefile
--- pmtools/turbostat/Makefile	2010-11-24 05:36:50.000000000 +0000
+++ pmtools.my/turbostat/Makefile	2010-11-24 16:42:05.000000000 +0000
@@ -1,3 +1,5 @@
+all: turbostat
+
 turbostat : turbostat.c
 
 clean :
EOF

  make
  (cd madt && make)
}

package() {
  cd "$srcdir/$pkgname"
  install -D -m755 acpidump/acpidump "$pkgdir/usr/sbin/acpidump"
  install -D -m755 acpixtract/acpixtract "$pkgdir/usr/sbin/acpixtract"
  install -D -m755 madt/madt "$pkgdir/usr/sbin/madt"
  install -D -m755 pmtest/pmtest "$pkgdir/usr/sbin/pmtest"
  install -D -m755 turbostat/turbostat "$pkgdir/usr/sbin/turbostat"
}
