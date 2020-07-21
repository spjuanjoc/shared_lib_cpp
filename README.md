# shared_lib_cpp

My version of a base shared library in C++

## Compilation
1. Create build dir
    ````
    $ mkdir build
    $ cd build
    ````

2. Generate makefiles

    `$ cmake ..`

3. Build library

    `$ cmake --build ./ --target shared_lib_cpp -- -j4`
