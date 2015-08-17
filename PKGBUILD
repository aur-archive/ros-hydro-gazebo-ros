# Script generated with import_catkin_packages.py
# For more information: https://github.com/bchretien/arch-ros-stacks
pkgdesc="ROS - Provides ROS plugins that offer message and service publishers for interfacing with Gazebo through ROS."
url='http://gazebosim.org/wiki/Tutorials'

pkgname='ros-hydro-gazebo-ros'
pkgver='2.3.6'
_pkgver_patch=0
arch=('any')
pkgrel=1
license=('Apache 2.0')

ros_makedepends=(ros-hydro-message-generation
  ros-hydro-tf
  ros-hydro-rosgraph-msgs
  ros-hydro-roscpp
  ros-hydro-geometry-msgs
  ros-hydro-roslib
  ros-hydro-catkin
  ros-hydro-std-msgs
  ros-hydro-std-srvs
  ros-hydro-cmake-modules
  ros-hydro-dynamic-reconfigure
  ros-hydro-gazebo-msgs
  ros-hydro-gazebo-plugins)
makedepends=('cmake' 'git' 'ros-build-tools'
  ${ros_makedepends[@]}
  gazebo
  tinyxml)

ros_depends=(ros-hydro-message-generation
  ros-hydro-rosgraph-msgs
  ros-hydro-roscpp
  ros-hydro-geometry-msgs
  ros-hydro-roslib
  ros-hydro-std-msgs
  ros-hydro-std-srvs
  ros-hydro-tf
  ros-hydro-dynamic-reconfigure
  ros-hydro-gazebo-msgs
  ros-hydro-gazebo-plugins)
depends=(${ros_depends[@]}
  gazebo
  tinyxml)

_tag=release/hydro/gazebo_ros/${pkgver}-${_pkgver_patch}
_dir=gazebo_ros
source=("${_dir}"::"git+https://github.com/ros-gbp/gazebo_ros_pkgs-release.git"#tag=${_tag})
md5sums=('SKIP')

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/hydro/setup.bash ] && source /opt/ros/hydro/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/hydro \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}
