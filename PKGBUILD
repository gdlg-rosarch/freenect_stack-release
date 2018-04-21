# Script generated with Bloom
pkgdesc="ROS - A libfreenect-based ROS driver for the Microsoft Kinect. This is a port of the OpenNI driver that uses libfreenect instead, because on some systems with some devices it works better."
url='http://ros.org/wiki/freenect_camera'

pkgname='ros-kinetic-freenect-camera'
pkgver='0.4.2_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('log4cxx'
'ros-kinetic-camera-info-manager'
'ros-kinetic-catkin'
'ros-kinetic-diagnostic-updater'
'ros-kinetic-dynamic-reconfigure'
'ros-kinetic-image-transport'
'ros-kinetic-libfreenect'
'ros-kinetic-nodelet'
'ros-kinetic-pluginlib'
'ros-kinetic-roscpp'
'ros-kinetic-sensor-msgs'
)

depends=('log4cxx'
'ros-kinetic-camera-info-manager'
'ros-kinetic-diagnostic-updater'
'ros-kinetic-dynamic-reconfigure'
'ros-kinetic-image-transport'
'ros-kinetic-libfreenect'
'ros-kinetic-nodelet'
'ros-kinetic-pluginlib'
'ros-kinetic-roscpp'
'ros-kinetic-sensor-msgs'
)

conflicts=()
replaces=()

_dir=freenect_camera
source=()
md5sums=()

prepare() {
    cp -R $startdir/freenect_camera $srcdir/freenect_camera
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

