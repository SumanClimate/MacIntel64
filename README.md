These are basic software needed for any mateorological studies and research. How these software can be installed on a Mac system with intel64 achitecture are described here. 
Although, it can be installed on other online repositories but sometimes it is extremely dangerous while used to compile to other packages using those. Various library 
conflicts/issues happened. But installing those packages from their individual tarball package reduces chances of those conflicts.
## INSTALLATION ##
It is assumed that the system has gcc, gfortran and g++ installed. bash shell used here\
export CC=gcc FC=gfortran F77=gfortran F90=gfortran CXX=g++\
export INSTALLDIR=your installation directory
## 1. zlib-1.2.11
   tar -zxvf zlib-1.2.11.tar\
   cd zlib-1.2.11\
   ./configure --prefix=$INSTALLDIR\
   make\
   make install
## 2. szip-2.1.1
   tar -zxvf szip-2.1.1.tar\
   cd szip-2.1.1\
   ./configure --prefix=$INSTALLDIR\
   make\
   make install
## 3. hdf5-1.10.7
   tar -zxvf hdf5-1.10.7.tar\
   cd hdf5-1.10.7\
   ./configure --prefix=$INSTALLDIR --with-zlib=$INSTALLDIR --with-szlib=$INSTALLDIR\
   make\
   make install
## 4. netcdf-c-4.5.0
   export CPPFLAGS=-I$INSTALLDIR/include\
   export LDFLAGS=-L$INSTALLDIR/lib\
   tar -zxvf netcdf-c-4.5.0.tar\
   cd netcdf-c-4.5.0\
   ./configure --prefix=$INSTALLDIR\
   make\
   make install
## 5. udunits-2.1.2
Firstly, close all terminal and put export PATH=$INSTALLDIR/bin:$PATH in the .bashrc file. Generally Mac consider .bash_profile so you might not have .bashrc. It it doesn't exist\
create one. Put source ~/.bashrc .bash_profile. Then .bashrc will run. Now open a terminal and do the next step.\
   export CFLAGS="-Wno-implicit-function-declaration"\
   tar -zxvf udunits-2.1.2.tar\
   cd udunits-2.1.2\
   ./configure --prefix=$INSTALLDIR\
   make\
   make install
