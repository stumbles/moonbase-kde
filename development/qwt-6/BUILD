source /etc/profile.d/qt6.rc &&

sed -e '/^\s*QWT_INSTALL_PREFIX/ s|=.*|= /usr|' \
    -e '/^QWT_INSTALL_DOCS/ s|/doc|/share/doc/qwt|' \
    -e '/^QWT_INSTALL_HEADERS/ s|include|&/qwt|' \
    -e '/^QWT_INSTALL_PLUGINS/ s|plugins/designer|lib/qt6/&|' \
    -e '/^QWT_INSTALL_FEATURES/ s|features|lib/qt6/mkspecs/&|' \
    -i qwtconfig.pri &&

/usr/lib/qt6/bin/qmake &&
default_make
