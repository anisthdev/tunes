# Maintainer: Asif Arbaj <asifarbaj@gmail.com>
_name=tunes
pkgname=totoro-tunes
pkgver=r0
pkgrel=1
pkgdesc="Music from YouTube Music into mpd's library, tagged from YouTube Music"
arch=('any')
url="https://github.com/anisthdev/tunes"
provides=('tunes')
conflicts=('tunes')
replaces=('tunes')
license=('unknown')
# A `uv run --script` script: uv brings ytmusicapi and mutagen itself
depends=('uv' 'yt-dlp' 'curl' 'mpc' 'libnotify')
optdepends=(
    'totoro-quickbar: downloads in the bar, with pause and cancel (quickbar-download)'
    'yazi: Open folder from the done notification'
)
makedepends=('git')
source=("git+$url.git")
sha256sums=('SKIP')

pkgver() {
    cd "$_name"
    printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short=7 HEAD)"
}

package() {
    cd "$_name"
    install -Dm755 tunes "$pkgdir/usr/bin/tunes"
    install -Dm644 README.md "$pkgdir/usr/share/doc/$_name/README.md"
}
