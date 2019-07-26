# banking-system-project
Simple Console Application used to test the Linux Injection / Function Hooking Application
## BankSystem

## About

The program is a simple program that emulates a Bank System.  It is a console program that manages user accounts and balances.  Users can be added and managed using this command line program.  This program is just used as a test program for the Linux (root) app that can inject a shared library into another process or application.

ubuntu@ubuntu $ ./BankSystem

## Sources: Bank System Project

Deepak Singh

Credit to Deepak Singh for the use of the Bank Syste Project.

http://www.cppforschool.com/project/banking-system-project.html

Max Compston, Embedded Software Solutions.

## Building this Release

The source code for this program is built using CMake.  

To build the x86-64 program navigate to the build directory run cmake as follows:

$ cmake .. && make

The source code for the arm64 target are cross compiled using gnu arm64 compiler, below.  First in install the cross-compiler on the host.

$ sudo apt-get install gcc-aarch64-linux-gnu g++-aarch64-linux-gnu

Next, set up the host to cross-compile arm64 creating a toolchain-aarch64-linux-gnu.cmake file in your home directory.  Add the following:

#- this one is important

SET(CMAKE_SYSTEM_NAME Linux)

SET(CMAKE_SYSTEM_PROCESSOR arm64)

#- specify the cross compiler

SET(CMAKE_C_COMPILER   /usr/bin/aarch64-linux-gnu-gcc)

SET(CMAKE_CXX_COMPILER /usr/bin/aarch64-linux-gnu-g++)

#- where is the target environment

SET(CMAKE_FIND_ROOT_PATH  /user/aarch64-linux-gnu)

#- search for programs in the build host directories

SET(CMAKE_FIND_ROOT_PATH_MODE_PROGRAM NEVER)

#- for libraries and headers in the target directories

SET(CMAKE_FIND_ROOT_PATH_MODE_LIBRARY ONLY)

SET(CMAKE_FIND_ROOT_PATH_MODE_INCLUDE ONLY)

To build the cross-compiled arm64 program navigate to the build directory and run cmake as follows:

$ cmake -DCMAKE_TOOLCHAIN_FILE=~/toolchain-aarch64-linux-gnu.cmake .. && make

