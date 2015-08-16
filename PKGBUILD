
# Submitter: Vishesh Handa
# Maintainer: Antonis Geralis

pkgname=koko-git
pkgver=r195.af1f327
pkgrel=1
pkgdesc='A KDE Image Gallery application'
arch=('i686' 'x86_64')
url='https://projects.kde.org/projects/kde/kde-workspace'
license=('LGPL')
depends=('qt5-base' 'qt5-quickcontrols' 'baloo-git' 'plasma-framework-git' 'kdeclarative' 'ki18n' 'kconfig' 'exiv2' 'kdtree')
makedepends=('extra-cmake-modules' 'git' 'kdoctools')
optdepends=()
conflicts=('koko')
provides=('koko')
source=("git://anongit.kde.org/koko.git")
install=$pkgname.install
sha256sums=('SKIP')

pkgver() {
  cd koko
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
  mkdir -p build
}

build() { 
  cd build
  cmake ../koko \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DLIB_INSTALL_DIR=lib \
    -DLIBEXEC_INSTALL_DIR=lib \
    -DKDE_INSTALL_USE_QT_SYS_PATHS=ON \
    -DSYSCONF_INSTALL_DIR=/etc
  make
}

package() {
  cd build
  make DESTDIR="$pkgdir" install
}
