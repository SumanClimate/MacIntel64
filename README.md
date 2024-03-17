These are basic software needed for any mateorological studies and research. How these software can be installed on a Mac system with intel64 achitecture are described here. 
Although, it can be installed on other online repositories but sometimes it is extremely dangerous while used to compile to other packages using those. Various library 
conflicts/issues happened. But installing those packages from their individual tarball package reduces chances of those conflicts.
## INSTALLATION ##
It is assumed that the system has gcc, gfortran and g++ installed.\
export CC=gcc FC=gfortran F77=gfortran F90=gfortran CXX=g++\
export INSTALLDIR=your_installation_directory\
1. zlib-1.2.11.\
   tar -zxvf zlib-1.2.11.tar\
   cd zlib-1.2.11\
   ./configure --prefix=$INSTALLDIR\
   make\
   make install\
