Eer File Format
===============

For the latest eer file format and examples, consult the **EER file format** pdf document in this repository.

How To Build the example TestEerReader
======================================

1. Create a *Build* directory where all the output can be stored. 
2. To generate a 64 bit Visual Studio solution, navigate to the *Build* directory:
    > cmake ../ -DLIBTIFF_INCLUDE_DIR="[Path to Libtiff local include directory]" -DLIBTIFF_LIB_DIR="[Path to Libtiff local lib directory]" -G=[Generator] -A x64

    * For example: 
        > cmake ../ -DLIBTIFF_INCLUDE_DIR="C:\libraries\libtiff\libtiff-4.3.0.1-vc141\include" -DLIBTIFF_LIB_DIR="C:\libraries\libtiff\libtiff-4.3.0.1-vc141\lib\Debug64" -G="Visual Studio 15 2017" -A x64

3. Open the solution in Visual Studio and build the solution. This will create a .lib for the source code (in Build/lib/Debug) and an .exe for the test example (in Build/Debug).

4. To run the TestEerReader.exe use the --help or -h argument on command line to understand what arguments the test needs. 

Build on Ubuntu Linux
1. Build and install libtiff library https://gitlab.com/libtiff/libtiff

        git clone https://gitlab.com/libtiff/libtiff.git
        cd libtiff; git checkout -b v4.6.0
        mkdir <libtiff-install> #create or designate a folder for libtiff installation
        cmake -DCMAKE_INSTALL_PREFIX=<libtiff-install> .
        make; make install

2. Checkout this repo from passlab and build

        git clone https://github.com/passlab/EerReaderLib
        cd EerReaderLib
        mkdir build; cd build
        cmake  -DLIBTIFF_INCLUDE_DIR=<libtiff-install>/include -DLIBTIFF_LIB_DIR=<libtiff-install>/lib ..
        make

3. Execute 
        ./TestEerReader --help
