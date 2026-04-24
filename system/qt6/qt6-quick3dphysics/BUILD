source /etc/profile.d/qt6.rc &&
export LANG='en_US.UTF-8'

# This applies here as well; https://github.com/neovim/neovim/issues/2557
CFLAGS="-U_FORTIFY_SOURCE -D_FORTIFY_SOURCE=2"
CXXFLAGS="-U_FORTIFY_SOURCE -D_FORTIFY_SOURCE=2"

OPTS+=" -DCMAKE_BUILD_TYPE=Release \
        -DCMAKE_INSTALL_PREFIX=$MODULE_PREFIX \
        -DINSTALL_LIBEXECDIR=qt6 \
        -DINSTALL_LIBDIR=qt6 \
        -DINSTALL_DOCDIR=share/doc/qt6 \
        -DINSTALL_ARCHDATADIR=qt6 \
        -DINSTALL_DATADIR=share/qt6 \
        -DINSTALL_INCLUDEDIR=include/qt6 \
        -DINSTALL_MKSPECSDIR=lib/qt6/mkspecs \
        -DINSTALL_PLUGINSDIR=lib/qt6/plugins \
        -DINSTALL_EXAMPLESDIR=share/doc/qt6/examples \
        -DCMAKE_MESSAGE_LOG_LEVEL=STATUS \
        -Wno-dev"

cmake -B build -S . -G Ninja $OPTS &&
cmake --build build &&
prepare_install &&
cmake --install build
