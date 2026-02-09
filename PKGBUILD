# Maintainer: bkmo <>
# This PKGbuild builds from git and not release, pkver always up to date.
pkgname=sdboot-snaps
pkgver=1.4.1
pkgrel=1
pkgdesc='Create UKIs for SD-Boot BTRFS bootable snapshot entries'
arch=('any')
license=('GPL3')
url='https://github.com/bkmo/sdboot-snaps'
depends=('systemd-ukify' 'snapper' 'btrfs-progs' 'coreutils' 'bash')
optdepends=('sbctl')
provides=('sdboot-snaps')
#source=("$pkgname-$pkgver.tar.gz::$url/archive/refs/tags/$pkgver.tar.gz")
source=(git+"https://github.com/bkmo/sdboot-snaps.git")
sha256sums=('SKIP')
backup=("etc/sdboot-snaps.conf")
install=.install

    package() {
    #cd $pkgname-$pkgver
    cd $pkgname

    install -Dm 0644  "pacman/05-path-stop.hook" -t "$pkgdir/usr/share/libalpm/hooks/"
    install -Dm 0644  "pacman/zz-path-start.hook" -t "$pkgdir/usr/share/libalpm/hooks/"
    install -Dm 0755  "pacman/snap-path-pre" -t "$pkgdir/usr/share/libalpm/scripts/"
    install -Dm 0755  "pacman/snap-path-post" -t "$pkgdir/usr/share/libalpm/scripts/"
    install -Dm 0644  "service/sdboot-snaps-watch.path" -t "$pkgdir/etc/systemd/system/"
    install -Dm 0644  "service/sdboot-snaps-watch.service" -t "$pkgdir/etc/systemd/system/"
    install -Dm 0644  "config/sdboot-snaps.conf" -t "$pkgdir/etc/"
    install -Dm 0755  "scripts/refresh-snapshot-ukis" -t "$pkgdir/usr/local/bin/"
    install -Dm 0755  "scripts/manage-ukis" -t "$pkgdir/usr/local/bin/"
    install -Dm 0755  "scripts/snapper-list" -t "$pkgdir/usr/local/bin/"
    install -Dm 0644   README.md -t "$pkgdir/usr/share/doc/${pkgname}/"
    install -Dm755 detect/snapshot-detect -t "$pkgdir/usr/local/bin/"
    install -Dm644 detect/snapshot-detect.desktop -t "$pkgdir/etc/xdg/autostart/"
    install -Dm644 LICENSE -t "${pkgdir}/usr/share/licenses/${pkgname}/"
    install -Dm644 sdboot-snaps.bmp -t "${pkgdir}/opt/sdboot-snaps/"
}
