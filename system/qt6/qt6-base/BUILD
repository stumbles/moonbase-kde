OPTS+=" -DCMAKE_BUILD_TYPE=Release \
        -DFEATURE_optimize_full=ON  \
        -DCMAKE_INSTALL_PREFIX=/usr \
        -DINSTALL_BINDIR=lib/qt6/bin \
        -DINSTALL_LIBDIR=lib/qt6 \
        -DINSTALL_LIBEXECDIR=/usr/lib/qt6 \
        -DINSTALL_DOCDIR=share/doc/qt6 \
        -DINSTALL_ARCHDATADIR=/usr/lib/qt6 \
        -DINSTALL_DATADIR=share/qt6 \
        -DINSTALL_INCLUDEDIR=include/qt6 \
        -DINSTALL_MKSPECSDIR=lib/qt6/mkspecs \
        -DINSTALL_EXAMPLESDIR=share/doc/qt6/examples \
        -DINSTALL_SYSCONFDIR=/etc/xdg \
        -DFEATURE_mtdev=OFF"

cmake -B build -S . -G Ninja $OPTS -Wno-dev &&
cmake --build build &&
prepare_install &&
cmake --install build &&

# Remove pointing to the src build directory files.
find /usr/lib/qt6 -type f -name '*Qt6*.prl' -exec sed -i -e '/^QMAKE_PRL_BUILD_DIR/d;s/\(QMAKE_PRL_LIBS =\).*/\1/' {} \; &&
find /usr/lib/qt6 -type f -name '*.prl' -exec sed -i -e '/^QMAKE_PRL_BUILD_DIR/d;s/\(QMAKE_PRL_LIBS =\).*/\1/' {} \; &&
find /usr/lib/ -type f -name '*Qt6*.prl' -exec sed -i -e '/^QMAKE_PRL_BUILD_DIR/d;s/\(QMAKE_PRL_LIBS =\).*/\1/' {} \; &&
find /usr/lib/ -type f -name '*.prl' -exec sed -i -e '/^QMAKE_PRL_BUILD_DIR/d;s/\(QMAKE_PRL_LIBS =\).*/\1/' {} \; &&

cat > qt6.rc << EOF &&
  export Qt6_DIR=/usr
  export QT6_PLUGIN_PATH="\${Qt6_DIR}/lib/qt6/plugins"
  export XDG_DATA_DIRS="\${XDG_DATA_DIRS:-/usr/share}:/usr/share/qt6"
  export PKG_CONFIG_PATH="\${Qt6_DIR}/lib/qt6/pkgconfig:\${PKG_CONFIG_PATH}"
  export PATH="\${Qt6_DIR}/lib/qt6/bin:\${PATH}"
  export CMAKE_PREFIX_PATH="\${Qt6_DIR}/lib/qt6/cmake:\${CMAKE_PREFIX_PATH}"
  export RCC=${Qt6_DIR}/lib/qt6/rcc
  export MOC=${Qt6_DIR}/lib/qt6/moc
  export UIC=${Qt6_DIR}/lib/qt6/uic
EOF

install -m644 qt6.rc /etc/profile.d/qt6.rc