# Maintainer: CyberPingU <cyberpingu@tuta.io>
pkgname=kryfo-bin
_pkgname=kryfo
pkgver=0.6.2
_pkgtag="${pkgver}-beta"
pkgrel=1
pkgdesc="Private messenger over Tor, no phone number or account (binary release)"
arch=('x86_64')
url="https://kryfo.app"
license=('GPL-3.0-or-later')
depends=(
    'gtk3'
    'libsecret'
    'mesa'
    'xdg-desktop-portal'
    'gst-plugins-base'
    'gst-plugins-good'
)
provides=('kryfo')
conflicts=('kryfo')
source=("https://github.com/GnosiWorks/Kryfo/releases/download/v${pkgver}/kryfo-${_pkgtag}-linux-x64.tar.gz")
sha256sums=('b127d137d9749422eb8529897d64aef6412619fa697fe802b5f44fb0ae111a78')

package() {
    cd "kryfo-${_pkgtag}-linux-x64"

    # Install main application files to /opt/kryfo
    install -dm755 "${pkgdir}/opt/${_pkgname}"
    cp -a kryfo lib data "${pkgdir}/opt/${_pkgname}/"

    # Symlink binary to /usr/bin/kryfo
    install -dm755 "${pkgdir}/usr/bin"
    ln -s "/opt/${_pkgname}/kryfo" "${pkgdir}/usr/bin/${_pkgname}"

    # Install desktop entry and point Exec to /opt/kryfo/kryfo
    install -Dm644 app.kryfo.Kryfo.desktop "${pkgdir}/usr/share/applications/app.kryfo.Kryfo.desktop"
    sed -i "s|^Exec=.*|Exec=/opt/${_pkgname}/kryfo %u|" "${pkgdir}/usr/share/applications/app.kryfo.Kryfo.desktop"

    # Install application icons
    if [ -d "data/icons/hicolor" ]; then
        install -dm755 "${pkgdir}/usr/share/icons/hicolor"
        cp -a data/icons/hicolor/* "${pkgdir}/usr/share/icons/hicolor/"
    fi

    # Install license
    install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}
