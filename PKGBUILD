# Maintainer: Raphiel Rollerscaperers <raphielscape at hentaios dot com>

pkgname=kwin-system76-scheduler-integration-git
_gitname=kwin-system76-scheduler-integration
pkgver=r11.ca5187c
pkgrel=1
pkgdesc="A kwin script that notify the System76 Scheduler which app has focus so it can be prioritized "
arch=('any')
url="https://github.com/maxiberta/${_gitname}"
license=('GPL3')
depends=('kwin')
makedepends=('kpackage')
provides=('kwin-system76-scheduler-integration')
conflicts=('kwin-system76-scheduler-integration')
source=("$_gitname::git+$url"
		"com.system76.Scheduler.dbus-proxy.service"
		"system76-scheduler-dbus-proxy")
install="${pkgname}.install"
md5sums=('SKIP'
         '7f9305c0eef37242256a684c787d24b7'
         'd51257c86f447019eed4d0541b4b7bb3')

pkgver() {
	cd "${srcdir}/${_gitname}"
	printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

package() {
	cd "${srcdir}/${_gitname}"
	kpackagetool5 --type Kwin/Script --install . -p "${pkgdir}/usr/share/kwin/scripts/"
	install -Dm644 metadata.desktop "${pkgdir}/usr/share/kservices5/${_gitname}.desktop"
	cd "${srcdir}"
	install -Dpm 0644 com.system76.Scheduler.dbus-proxy.service "$pkgdir/usr/lib/systemd/user/com.system76.Scheduler.dbus-proxy.service"
	install -Dpm 0755 system76-scheduler-dbus-proxy "$pkgdir/usr/bin/system76-scheduler-dbus-proxy"
}
