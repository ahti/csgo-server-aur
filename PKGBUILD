pkgname=csgo-server
pkgver=1.35.6.8
pkgrel=1
arch=('x86_64')
pkgdesc='CS:GO dedicated server'
license=('proprietary')
depends=('lib32-gcc-libs')
makedepends=('lib32-gcc-libs')
url='https://developer.valvesoftware.com/wiki/Counter-Strike:_Global_Offensive_Dedicated_Servers'
source=(
    'http://media.steampowered.com/installer/steamcmd_linux.tar.gz'
    'csgo-server.service'
    'csgo-server.install'
)
sha256sums=(
    'SKIP'
    'a5067c646bdf211b5830f74ce6208801f2b84858c0d3dcd6f816f6487eaf3b24' # csgo-server.service
    '71cb164be7b6c44676bb15d97e6549e82b199553523986ae54cf6a5f467f7668' # csgo-server.install
)

install=csgo-server.install

prepare() {
    cd $srcdir
    mkdir -p $srcdir/csgo-server
    ./steamcmd.sh +login anonymous +force_install_dir $srcdir/csgo-server +app_update 740 validate +quit
}

pkgver() {
    cat $srcdir/csgo-server/csgo/steam.inf | grep PatchVersion | sed -e 's/.*=//g;s/\n//g' | tr -d '\r\n'
}

package() {
    mkdir -p $pkgdir/opt
    cp -r $srcdir/csgo-server $pkgdir/opt/csgo-server
    chmod 755 $pkgdir/opt/csgo-server

    install -Dm0644 "${srcdir}/csgo-server.service" "${pkgdir}/usr/lib/systemd/system/csgo-server.service"
}
