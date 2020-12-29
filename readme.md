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
  
  
  
  
  
  http://download.qt.io/archive/qt/5.13/5.13.2/
