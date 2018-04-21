# Script generated with Bloom
pkgdesc="ROS - Launch files for freenect_camera to produce rectified, registered or disparity images. Also produce point clouds and registered point clouds. Based on the openni_launch package."
url='http://ros.org/wiki/freenect_launch'

pkgname='ros-kinetic-freenect-launch'
pkgver='0.4.2_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('ros-kinetic-catkin'
)

depends=('ros-kinetic-freenect-camera'
'ros-kinetic-image-proc'
'ros-kinetic-nodelet'
'ros-kinetic-rgbd-launch'
'ros-kinetic-tf'
)

conflicts=()
replaces=()

_dir=freenect_launch
source=()
md5sums=()

prepare() {
    cp -R $startdir/freenect_launch $srcdir/freenect_launch
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

