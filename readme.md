How to build AliceVision:

1. Download openExr-2.4.0.
  cd openexr-2.4.0 && mkdir build && cd build
  cmake -LAH .. && make -j4 && sudo make install
2. Download boost-1.7.0
  cd boost_1_70_o 
  ./bootstrap.sh
  sudo ./b2 install
3. oiio(before download pybind using pip3)
  cd oiio && mkdir build && cd build
  cmake -DCMAKE_BUILD_TYPE=Release .. 
  make -j4 && sudo make install 
  Hint: when the compiler complains about not found lXxf86vm, use sudo apt-get install libxxf86vm-dev
4. eigen3.3.4 https://gitlab.com/libeigen/eigen/-/releases
  cd eigen-3.3.4 && mkdir build && cd build 
  cmake -DCMAKE_BUILD_TYPE=Release  .. 
  sudo make install
  sudo cp -r /usr/local/include/eigen3 /usr/include 
5. ceres 1.14.0 https://github.com/ceres-solver/ceres-solver/releases/tag/1.14.0
 

  sudo apt-get install cmake
  sudo apt-get install libgoogle-glog-dev libgflags-dev
  sudo apt-get install libatlas-base-dev
  sudo apt-get install libsuitesparse-dev
  tar zxf ceres-solver-1.14.0.tar.gz
  mkdir ceres-bin
  cd ceres-bin
  cmake ../ceres-solver-1.14.0
  make -j3
  make install
6. geogram 
  wget -c https://gforge.inria.fr/frs/download.php/file/38315/geogram_1.7.5.zip   
  sh -f configure.sh
  cd build/Linux64-gcc-dynamic-Release 
  make -j4
  sudo make install
7. opengv
  git clone --depth 1 https://github.com/alicevision/opengv.git --branch=cmake_fix_install
  cd opengv && mkdir build && cd build
  cmake -DCMAKE_BUILD_TYPE=Release .. && make -j4
  sudo make install 
8. alicevision
  git clone https://github.com/alicevision/AliceVision.git --recursive
  cd AliceVision && mkdir build && cd build
  cmake -DCMAKE_BUILD_TYPE=Release -DALICEVISION_USE_CUDA=OFF -DALICEVISION_USE_UNCERTAINTYTE=OFF.. && make -j4
9. QT5 > 5.13 (http://download.qt.io/archive/qt/5.13/5.13.2/)
  chmod +x qt-opensource-linux-x64-5.13.2.run
  sudo ./qt-opensource-linux-x64-5.13.2.run
  QT_DIR=/opt/Qt5.13.2/5.13.2/gcc_64
  (!!!check all the components of qt during installation)
10. QTalmenbic
  git clone --depth 1 https://github.com/alembic/alembic 
  cd alembic
  mkdir build && cd build
  make -j4
  sudo make install

  export QT_DIR=/opt/Qt5.13.2/5.13.2/gcc_64
  cmake ..  -DCMAKE_PREFIX_PATH=$QT_DIR  -DCMAKE_BUILD_TYPE=Release
  sudo make install
 11. QTOIIO
  git clone --recursive git://github.com/alicevision/QtOIIO
  cd QtOIIO
  mkdir build && cd build
  export QT_DIR=/opt/Qt5.13.2/5.13.2/gcc_64
  cmake .. -DCMAKE_PREFIX_PATH=$QT_DIR -DCMAKE_BUILD_TYPE=Release
  make install
 12. QtAliceVision
  git clone --recursive git://github.com/alicevision/QtAliceVision
  cd QtAliceVision
  mkdir build && cd build
  export QT_DIR=/opt/Qt5.13.2/5.13.2/gcc_64
  cmake .. -DCMAKE_PREFIX_PATH=$QT_DIR -DCMAKE_BUILD_TYPE=Release
  make install
 13. meshroom
 export ALICEVISION_SENSOR_DB=/path/to/AliceVision/src/aliceVision/sensorDB/cameraSensors.db
 export ALICEVISION_VOCTREE=/home/yetao/vlfeat_K80L3.SIFT.tree
 export QML2_IMPORT_PATH=/usr/local/qml
 
 in the forlder meshroom, open terminal
 export PATH=/home/username/AliceVision/build/Linux-x86_64
 PYTHONPATH=$PWD python3 meshroom/ui
 (maybe terminal complains about the python3 edition messed use /usr/bin/python3 meshroom instead)

  
  
  
  
  
  
