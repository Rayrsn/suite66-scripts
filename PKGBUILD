# Maintainer	: Nathan <ndowens@artixlinux.org>

pkgname=suite66-scripts
_realname=66-scripts
pkgdesc="Complete and portable set of services to properly boot a machine with 66 tools"
pkgver=1.7.1.4
pkgrel=2
arch=('any')
license=('ISC')
depends=('s6-linux-utils' 's6-portable-utils'
    	 'util-linux' 'iproute2' 'kmod')
makedepends=('git')
optdepends=(
    'iptables: iptables support'
    'nftables: nftables support'
    'ebtables: ebtables support'
    'arptables: arptables support'
    'dmraid: dmraid support'
    'lvm2: lvm support'
    'btrfs-progs: btrfs support'
    'zfs: zfs support'
    'cryptsetup: encryption support')
url="https://gitea.artixlinux.org/artix/66-scripts"
provides=('66-scripts')
conflicts=('runit' 'openrc' 's6-linux-init' 's6-scripts')
backup=('etc/66/rc.local')
source=("git+https://gitea.artixlinux.org/artix/66-scripts#branch=${pkgver}")
sha512sums=('SKIP')

build() {
  cd "$_realname"
  ./configure \
	--bindir=/usr/bin \
	--with-system-service=/etc/66/service \
 	--with-system-module=/etc/66/module \
	--with-system-script=/etc/66/script \
  	--with-sysadmin-service-conf=/etc/suite66/conf \
	--HOSTNAME='artixlinux' \
	--SETUPCONSOLE='!yes' \
	--TMPFILE='!yes' \
  	--SYSUSER='!yes' \
	--TTY='5' \
	--FSTAB='!yes' \
	--SYSCTL='!yes' \
	--FORCECHCK='!no' \
  	--LOCALE='!yes'
}

package() {
  cd "$_realname"
  make DESTDIR="$pkgdir" install
  install -Dm644 LICENSE -t "$pkgdir"/usr/share/licenses/${pkgname}
}
