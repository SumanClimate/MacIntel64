zlib, szip, hdf5, netcdf and udunits are basic software needed for any mateorological studies and research. How these software can be installed on a Mac system with intel64 achitecture are described here. 
Although, it can be installed on other online repositories but sometimes it is extremely dangerous while used to compile to other packages using those. Various library 
conflicts/issues happened. But installing those packages from their individual tarball package reduces chances of those conflicts.
## INSTALLATION ##
It is assumed that the system has gcc, gfortran and g++ installed. bash shell used here\
export CC=gcc FC=gfortran F77=gfortran F90=gfortran CXX=g++\
export INSTALLDIR=your installation directory
## 1. zlib-1.2.11
   tar -zxvf zlib-1.2.11.tar\
   cd zlib-1.2.11\
   ./configure --prefix=${INSTALLDIR}\
   make\
   make install
## 2. szip-2.1.1
   tar -zxvf szip-2.1.1.tar\
   cd szip-2.1.1\
   ./configure --prefix=${INSTALLDIR}\
   make\
   make install
## 3. hdf5-1.10.7
   tar -zxvf hdf5-1.10.7.tar\
   cd hdf5-1.10.7\
   ./configure --prefix=${INSTALLDIR} --with-zlib=${INSTALLDIR} --with-szlib=${INSTALLDIR}\
   make\
   make install
## 4. netcdf-c-4.5.0
   export CPPFLAGS=-I${INSTALLDIR}/include\
   export LDFLAGS=-L${INSTALLDIR}/lib\
   tar -zxvf netcdf-c-4.5.0.tar\
   cd netcdf-c-4.5.0\
   ./configure --prefix=${INSTALLDIR}\
   make\
   make install
## 5. udunits-2.1.2
Firstly, close all terminal and then put\
export PATH=${INSTALLDIR}/bin:$PATH\
export CC=gcc FC=gfortran F77=gfortran F90=gfortran CXX=g++\
in the ~/.bashrc file.\
Generally Mac consider .bash_profile by default and so you might not have .bashrc. If it doesn't exist create it. Dont forget to put source ~/.bashrc in .bash_profile. Then .bashrc will run. Now open a terminal and do the next step.\
   export CFLAGS="-Wno-implicit-function-declaration"\
   tar -zxvf udunits-2.1.2.tar\
   cd udunits-2.1.2\
   ./configure --prefix=${INSTALLDIR}\
   make\
   make install
## 6. netcdf-fortran-4.5.1
   export CPPFLAGS=-I${INSTALLDIR}/include\
   export LDFLAGS=-L${INSTALLDIR}/lib\
   export CFLAGS="-Wno-implicit-function-declaration"\
   export FFLAGS="-fallow-argument-mismatch"\
   export FCFLAGS="-fallow-argument-mismatch"\
   tar -zxvf netcdf-fortran-4.5.1.tar\
   cd netcdf-fortran-4.5.1\
   ./configure --prefix={INSTALLDIR}\
   make\
   make install
## This completes the installtion. You now can check ncdump, nc-config --all, nf-config --all etc. to check the installtion. ##
A simple c/fortran reading/writing code (https://www.unidata.ucar.edu/software/netcdf/examples/programs/) also be a a good check. While compile these code, netcdf library should be linked as below:\
gfortran simple_xy_wr.f90 -I${INSTALLDIR}/include -L${INSTALLDIR}/lib -lnetdff\
gcc simple_xy_wr.c -I${INSTALLDIR}/include -L${INSTALLDIR}/lib -lnetcdf
## NOTE: installtion of these software on new ARM64 system (M1/M2 chip) system is same as decribed here. ##
