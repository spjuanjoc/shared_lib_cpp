# shared_lib_cpp

How to create a shared library in C++

## Compile with cmake
1. Create build dir
    ````
    $ mkdir build
    $ cd build
    ````

2. Generate makefiles

    `$ cmake ..`

3. Build library

    `$ cmake --build ./ --target shared_lib_cpp -- -j4`

## Compile from console

1. To generate files in ./bin

    `$ mkdir bin`
    
2. All in one step

    `$ g++ -fPIC -I ./include src/Foo.cpp src/library.cpp -shared -o bin/libshared_lib_cpp.so`

3. Foo only in two-steps. 
    * Build object
    
    `$ g++ -c -fPIC ./src/Foo.cpp -I ./include -o ./bin/Foo.o`

    * Build lib
    
    `$ g++ -shared ./bin/Foo_shared.o -o ./bin/libFoo_shared.so`

4. Check symbols
    
    `$ nm -D ./bin/libshared_lib_cpp.so`
    
5. Use in some binary from ./bin
    
    ````
    $ g++ main.cpp -L . -lFoo_shared -I ../include -o main_shared.out
    $ export LD_LIBRARY_PATH=.:$LD_LIBRARY_PATH
    $ ./main_shared.out
    ````
---
### Compile to static with cmake

`add_library(${PROJECT_NAME} STATIC ${SOURCES})`

### Compile to static from console

1. Create object file:
    
    `$ g++ -c ./src/Foo.cpp -I ./include -o ./bin/Foo_static.o`

2. Create archive (static library)
    
    `$ ar rvs ./bin/Foo_static.a ./bin/Foo_static.o`

3. Check symbols
    
    `$ nm ./bin/Foo_static.a`

4. Use in some binary from ./bin
    
    ````
    $ g++ main.cpp Foo_static.a -I ../include -o main_static.out
    $ ./main_static.out
   ````

---
See [shared-libraries-linux-gcc](https://www.cprogramming.com/tutorial/shared-libraries-linux-gcc.html)