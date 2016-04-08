
pkgname=cegui
pkgver=0.8.4
_pkgver=0-8-4
_commit=cegui-cegui-5861231e8335
pkgrel=1
pkgdesc="A free library providing windowing and widgets for graphics APIs/engines"
arch=('x86_64')
url="http://cegui.org.uk"
license=("MIT")
depends=('pcre' 'glew' 'expat' 'freetype2' 'libxml2' 'freeglut' 'lua' 'ogre' 'gtk2')
makedepends=('cmake' 'boost' 'glm' 'mesa' 'toluapp')
source=("https://bitbucket.org/cegui/cegui/get/v0-8-4.tar.bz2")
md5sums=('4a5d46390215ff1cd2651a1d1ce161de')

prepare() {
  cd ${_commit}

  sed -i "s/lib64/lib/g" CMakeLists.txt
}

build() {
  mkdir build 
  cd build

  cmake ../${_commit} \
      -DCMAKE_INSTALL_PREFIX=/usr \
      -DCEGUI_LIB_INSTALL_DIR=lib \
      -DCEGUI_BUILD_PYTHON_MODULES=OFF 

  make
}

package() {
  cd build
  make DESTDIR="${pkgdir}" install

  install -Dm644 ../${_commit}/COPYING ${pkgdir}/usr/share/licenses/$pkgname/LICENSE
}
