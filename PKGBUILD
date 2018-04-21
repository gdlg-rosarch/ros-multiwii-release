# Script generated with Bloom
pkgdesc="ROS - The multiwii package"


pkgname='ros-kinetic-multiwii'
pkgver='2.1.0_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('eigen3'
'ros-kinetic-catkin'
'ros-kinetic-dynamic-reconfigure'
'ros-kinetic-geometry-msgs'
'ros-kinetic-mavros-msgs'
'ros-kinetic-message-generation'
'ros-kinetic-msp'
'ros-kinetic-roscpp'
'ros-kinetic-sensor-msgs'
'ros-kinetic-std-msgs'
)

depends=('ros-kinetic-dynamic-reconfigure'
'ros-kinetic-message-runtime'
'ros-kinetic-msp'
'ros-kinetic-roscpp'
)

conflicts=()
replaces=()

_dir=multiwii
source=()
md5sums=()

prepare() {
    cp -R $startdir/multiwii $srcdir/multiwii
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/kinetic/setup.bash ] && source /opt/ros/kinetic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/kinetic \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

