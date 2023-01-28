# Merged with official ABS plasma-framework PKGBUILD by João, 2021/02/21 (all respective contributors apply herein)
# Maintainer: João Figueiredo <jf.mundox@gmail.com>
# Contributor: zanny <lordzanny@gmail.com>
# Contributor: Antonio Rojas <arojas@archlinux.org>
# Contributor: Andrea Scarpino <andrea@archlinux.org>

pkgname=plasma-framework-git
pkgver=5.80.0_r15760.gb84fbb01f
pkgrel=1
pkgdesc='Plasma library and runtime components based upon KF5 and Qt5'
arch=($CARCH)
url='https://community.kde.org/Frameworks'
license=(LGPL)
depends=(kactivities-git kdeclarative-git kwayland-git kirigami2-git)
makedepends=(git extra-cmake-modules-git qt5-tools qt5-doc kdoctools-git doxygen)
conflicts=(${pkgname%-git})
provides=(${pkgname%-git})
groups=(kf5-git)
source=("git+https://github.com/KDE/${pkgname%-git}.git")
sha256sums=('SKIP')

pkgver() {
    cd ${pkgname%-git}
      _ver="$(grep -m1 'set(KF5\?_VERSION' CMakeLists.txt | cut -d '"' -f2 | tr - .)"
        echo "${_ver}_r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}

build() {
    cmake -B build -S ${pkgname%-git} \
        -DBUILD_TESTING=OFF \
            -DBUILD_QCH=ON
              cmake --build build
}

package() {
    DESTDIR="$pkgdir" cmake --install build
}
source=("git+https://github.com/KDE/${pkgname%-git}#branch=kf5")
