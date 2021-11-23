# Maintainer: Martin Merfort <martin.merfort@sixt.com>
pkgname=cato_client
pkgver=2.2.0.3
pkgrel=1
pkgdesc="Cato VPN"
arch=('x86_64')
url="https://myvpn.catonetworks.com/login"
license=('custom')
depends=('sed' 'tar' 'systemd')
backup=("etc/cato/client.json")
source=(
    'https://myvpn.catonetworks.com/public/clients/cato-install-ubuntu18.sh'
    'cato_client.service'
    'client.json'
)
noextract=('cato-install-ubuntu18.sh')
sha256sums=(
    'af39a4779d484571765afdb68d40bfc93d4bf39d1378478955934f1797490e1f'
    '03408e9d4dabdd81575f0429f95ebc337ba78e9b9b83614633369bd594d3e688'
    '331e05b35d60dfbd5198cd2f923aeffd2172e67cc989f41397bf6533dcb21529'
)

package() {
    sed -e '1,/^exit$/d' "cato-install-ubuntu18.sh" | bsdtar -C "${pkgdir}/" -xf -
    install -Dm755 "${pkgdir}/cato/client" "${pkgdir}/usr/bin/cato_client"
    install -Dm644 "${srcdir}/cato_client.service" "${pkgdir}/usr/lib/systemd/system/cato_client.service"
    install -Dm600 "${srcdir}/client.json" "${pkgdir}/etc/cato/client.json"
    rm -f cclient.sh status.sh
}
