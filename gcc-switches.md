# Check the actual GCC command-line options

```
$ ./configure --enable-debug
$ (make clean && make -j 5) > /dev/null
$ dwarfdump src/bitcoind | grep -m 1 -2 DW_AT_producer
COMPILE_UNIT<header overall offset = 0x00000000>:
< 0><0x0000000b>  DW_TAG_compile_unit
                    DW_AT_producer              GNU C++11 7.5.0 -mtune=generic -march=x86-64 -g3 -O0 -std=c++11 -ftrapv -fstack-reuse=none -fstack-protector-all -fPIE
                    DW_AT_language              DW_LANG_C_plus_plus
                    DW_AT_name                  bitcoind.cpp
```

Ref: [`-grecord-gcc-switches`](https://gcc.gnu.org/onlinedocs/gcc-6.4.0/gcc/Debugging-Options.html)
