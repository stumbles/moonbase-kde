source /etc/profile.d/qt6.rc &&

OPTS+=" -DCMAKE_INSTALL_PREFIX=/usr \
        -DCMAKE_BUILD_TYPE=Release \
        -DWITH_INTERNAL_SPATIALINDEX=ON \
        -DWITH_PDAL=OFF \
        -DWITH_DRACO=OFF \
        -DQSCINTILLA_INCLUDE_DIR=/usr/lib/include/qt6/ \
        -DQSCINTILLA_LIBRARY=/usr/lib/qt6/libqscintilla2_qt6.so \
        -Wno-dev"


cmake -B $MODULE-$VERSION -S . -G Ninja $OPTS &&
cmake --build $MODULE-$VERSION &&

prepare_install
cmake --install $MODULE-$VERSION
