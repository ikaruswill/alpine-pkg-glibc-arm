# Maintainer: Will <alpine-pkgs@ikaruswill.com>

pkgname="glibc"
pkgver="2.31"
_pkgrel="0"
pkgrel="0"
pkgdesc="GNU C Library compatibility layer"
arch="armv7"
url="https://github.com/ikaruswill/arm-alpine-pkg-glibc"
license="LGPL"
source="https://github.com/ikaruswill/arm-docker-glibc-builder/releases/download/$pkgver-$_pkgrel/glibc-bin-$pkgver-$_pkgrel-armv7l.tar.gz
nsswitch.conf
ld.so.conf"
subpackages="$pkgname-bin $pkgname-dev $pkgname-i18n"
triggers="$pkgname-bin.trigger=/lib:/usr/lib:/usr/glibc-compat/lib"

package() {
  mkdir -p "$pkgdir/lib" "$pkgdir/lib64" "$pkgdir/usr/glibc-compat/lib/locale"  "$pkgdir"/usr/glibc-compat/lib64 "$pkgdir"/etc
  cp -a "$srcdir"/usr "$pkgdir"
  cp "$srcdir"/ld.so.conf "$pkgdir"/usr/glibc-compat/etc/ld.so.conf
  cp "$srcdir"/nsswitch.conf "$pkgdir"/etc/nsswitch.conf
  rm "$pkgdir"/usr/glibc-compat/etc/rpc
  rm -rf "$pkgdir"/usr/glibc-compat/bin
  rm -rf "$pkgdir"/usr/glibc-compat/sbin
  rm -rf "$pkgdir"/usr/glibc-compat/lib/gconv
  rm -rf "$pkgdir"/usr/glibc-compat/lib/getconf
  rm -rf "$pkgdir"/usr/glibc-compat/lib/audit
  rm -rf "$pkgdir"/usr/glibc-compat/share
  rm -rf "$pkgdir"/usr/glibc-compat/var
  ln -s /usr/glibc-compat/lib/ld-linux-armhf.so.3 ${pkgdir}/lib/ld-linux-armhf.so.3
  ln -s /usr/glibc-compat/lib/ld-linux-armhf.so.3 ${pkgdir}/lib64/ld-linux-armhf.so.3
  ln -s /usr/glibc-compat/lib/ld-linux-armhf.so.3 ${pkgdir}/usr/glibc-compat/lib64/ld-linux-armhf.so.3
  ln -s /usr/glibc-compat/etc/ld.so.cache ${pkgdir}/etc/ld.so.cache
}

bin() {
  depends="$pkgname libgcc"
  mkdir -p "$subpkgdir"/usr/glibc-compat
  cp -a "$srcdir"/usr/glibc-compat/bin "$subpkgdir"/usr/glibc-compat
  cp -a "$srcdir"/usr/glibc-compat/sbin "$subpkgdir"/usr/glibc-compat
}

i18n() {
  depends="$pkgname-bin"
  arch="noarch"
  mkdir -p "$subpkgdir"/usr/glibc-compat
  cp -a "$srcdir"/usr/glibc-compat/share "$subpkgdir"/usr/glibc-compat
}

sha512sums="4a247ae160e86e03ca28ba6170d7285cf70c6c2e28e34faf6c828d150a6a514849f4eb7a7101e2e9fb6dd9c590d2abba2c5e5f36a8ca0b81dcc5e76f8ea0a62a  glibc-bin-2.31-0-armv7l.tar.gz
478bdd9f7da9e6453cca91ce0bd20eec031e7424e967696eb3947e3f21aa86067aaf614784b89a117279d8a939174498210eaaa2f277d3942d1ca7b4809d4b7e  nsswitch.conf
2912f254f8eceed1f384a1035ad0f42f5506c609ec08c361e2c0093506724a6114732db1c67171c8561f25893c0dd5c0c1d62e8a726712216d9b45973585c9f7  ld.so.conf"
