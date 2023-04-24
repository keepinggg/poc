# 1.heap-buffer-overflow
## env
ubuntu20.04 

gcc version 9.4.0 (Ubuntu 9.4.0-1ubuntu1~20.04.1)

swfdump - part of swftools 0.9.2

## sample
[poc_heap-buffer_overflow_swf_GetPlaceObject](https://github.com/keepinggg/poc/blob/main/poc_of_swfdump/poc_heap-buffer_overflow_swf_GetPlaceObject)

## crash
```
./swfdump -D poc_heap-buffer_overflow_swf_GetPlaceObject
==2946990==ERROR: AddressSanitizer: heap-buffer-overflow on address 0x603000000023 at pc 0x7f76f23fca7d bp 0x7fff4af77e40 sp 0x7fff4af775e8
READ of size 11 at 0x603000000023 thread T0
    #0 0x7f76f23fca7c in __interceptor_strlen ../../../../src/libsanitizer/sanitizer_common/sanitizer_common_interceptors.inc:354
    #1 0x561bf882902a in swf_GetPlaceObject modules/swfobject.c:195
    #2 0x561bf881db3a in main /home/ther/fuzzing/swftools-master/src/swfdump.c:1341
    #3 0x7f76f205c082 in __libc_start_main ../csu/libc-start.c:308
    #4 0x561bf8816ced in _start (/home/ther/fuzzing/swftools-master/src/swfdump+0x23ced)

0x603000000023 is located 0 bytes to the right of 19-byte region [0x603000000010,0x603000000023)
allocated by thread T0 here:
    #0 0x7f76f24a2808 in __interceptor_malloc ../../../../src/libsanitizer/asan/asan_malloc_linux.cc:144
    #1 0x561bf888d0ef in rfx_alloc /home/ther/fuzzing/swftools-master/lib/mem.c:30
    #2 0x561bf889c4b3  (/home/ther/fuzzing/swftools-master/src/swfdump+0xa94b3)

SUMMARY: AddressSanitizer: heap-buffer-overflow ../../../../src/libsanitizer/sanitizer_common/sanitizer_common_interceptors.inc:354 in __interceptor_strlen
Shadow bytes around the buggy address:
  0x0c067fff7fb0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x0c067fff7fc0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x0c067fff7fd0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x0c067fff7fe0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x0c067fff7ff0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
=>0x0c067fff8000: fa fa 00 00[03]fa fa fa fa fa fa fa fa fa fa fa
  0x0c067fff8010: fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa
  0x0c067fff8020: fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa
  0x0c067fff8030: fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa
  0x0c067fff8040: fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa
  0x0c067fff8050: fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa
Shadow byte legend (one shadow byte represents 8 application bytes):
  Addressable:           00
  Partially addressable: 01 02 03 04 05 06 07 
  Heap left redzone:       fa
  Freed heap region:       fd
  Stack left redzone:      f1
  Stack mid redzone:       f2
  Stack right redzone:     f3
  Stack after return:      f5
  Stack use after scope:   f8
  Global redzone:          f9
  Global init order:       f6
  Poisoned by user:        f7
  Container overflow:      fc
  Array cookie:            ac
  Intra object redzone:    bb
  ASan internal:           fe
  Left alloca redzone:     ca
  Right alloca redzone:    cb
  Shadow gap:              cc
==2946990==ABORTING

```

### CVE-ID
CVE-2023-27249

### Discover
zhangzhourui, luhui, tianzhihong at Guangzhou University.

# 2.NULL pointer dereference
## env
ubuntu20.04 

gcc version 9.4.0 (Ubuntu 9.4.0-1ubuntu1~20.04.1)

swfdump - part of swftools 0.9.2

## sample
[poc_SEGV_swf_FontExtract_DefineTextCallback](https://github.com/keepinggg/poc/blob/main/poc_of_swfdump/poc_SEGV_swf_FontExtract_DefineTextCallback)

## crash
```
./swfdump -D poc_SEGV_swf_FontExtract_DefineTextCallback
==963719==ERROR: AddressSanitizer: SEGV on unknown address 0x000000000000 (pc 0x5588f4dfd3e0 bp 0x7ffe5d0b8c80 sp 0x7ffe5d0b8b60 T0)
==963719==The signal is caused by a WRITE memory access.
==963719==Hint: address points to the zero page.
    #0 0x5588f4dfd3df in swf_FontExtract_DefineTextCallback modules/swftext.c:508
    #1 0x5588f4e006c2 in swf_FontExtract_DefineText modules/swftext.c:532
    #2 0x5588f4e00a2a in swf_FontExtract modules/swftext.c:617
    #3 0x5588f4de414e in fontcallback2 /home/ther/fuzzing/swftools-master/src/swfdump.c:941
    #4 0x5588f4dfe784 in swf_FontEnumerate modules/swftext.c:133
    #5 0x5588f4dea6c2 in main /home/ther/fuzzing/swftools-master/src/swfdump.c:1296
    #6 0x7faf5a182082 in __libc_start_main ../csu/libc-start.c:308
    #7 0x5588f4de3ced in _start (/home/ther/fuzzing/swftools-master/src/swfdump+0x23ced)

AddressSanitizer can not provide additional info.
SUMMARY: AddressSanitizer: SEGV modules/swftext.c:508 in swf_FontExtract_DefineTextCallback
==963719==ABORTING

```

### Discover
zhangzhourui, luhui, tianzhihong, zhanghaonan at Guangzhou University.

# 3.NULL pointer dereference
## env
ubuntu20.04 

gcc version 9.4.0 (Ubuntu 9.4.0-1ubuntu1~20.04.1)

swfdump - part of swftools 0.9.2

## sample
[poc_SEGV_textcallback](https://github.com/keepinggg/poc/blob/main/poc_of_swfdump/poc_SEGV_textcallback)

## crash
```
./swfdump -D poc_SEGV_textcallback
==963737==ERROR: AddressSanitizer: SEGV on unknown address 0x000000000000 (pc 0x564fa1282f2d bp 0x000000000000 sp 0x7ffe017c3e00 T0)
==963737==The signal is caused by a READ memory access.
==963737==Hint: address points to the zero page.
    #0 0x564fa1282f2c in textcallback /home/ther/fuzzing/swftools-master/src/swfdump.c:409
    #1 0x564fa129c55d in swf_FontExtract_DefineTextCallback modules/swftext.c:516
    #2 0x564fa129f6a4 in swf_ParseDefineText modules/swftext.c:527
    #3 0x564fa1284a03 in handleText /home/ther/fuzzing/swftools-master/src/swfdump.c:457
    #4 0x564fa128ab62 in main /home/ther/fuzzing/swftools-master/src/swfdump.c:1520
    #5 0x7f073471a082 in __libc_start_main ../csu/libc-start.c:308
    #6 0x564fa1282ced in _start (/home/ther/fuzzing/swftools-master/src/swfdump+0x23ced)

AddressSanitizer can not provide additional info.
SUMMARY: AddressSanitizer: SEGV /home/ther/fuzzing/swftools-master/src/swfdump.c:409 in textcallback
==963737==ABORTING

```

### Discover
zhangzhourui, luhui, tianzhihong, zhanghaonan at Guangzhou University.

# 4.stack-overflow
## env
ubuntu20.04 

gcc version 9.4.0 (Ubuntu 9.4.0-1ubuntu1~20.04.1)

swfdump - part of swftools 0.9.2

## sample
[poc_stack-overflow_constant_tostring](https://github.com/keepinggg/poc/blob/main/poc_of_swfdump/poc_stack-overflow_constant_tostring)

## crash
```
./swfdump -D poc_stack-overflow_constant_tostring
=963740==ERROR: AddressSanitizer: stack-overflow on address 0x7ffee2312f90 (pc 0x7f8db2b9c881 bp 0x7ffee2313450 sp 0x7ffee2312ee0 T0)
    #0 0x7f8db2b9c880 in __vfprintf_internal /build/glibc-SzIz7B/glibc-2.31/stdio-common/vfprintf-internal.c:1289
    #1 0x7f8db2b9fea1 in buffered_vfprintf /build/glibc-SzIz7B/glibc-2.31/stdio-common/vfprintf-internal.c:2377
    #2 0x7f8db2b9cd23 in __vfprintf_internal /build/glibc-SzIz7B/glibc-2.31/stdio-common/vfprintf-internal.c:1346
    #3 0x7f8db2f20f88 in __interceptor_vfprintf ../../../../src/libsanitizer/sanitizer_common/sanitizer_common_interceptors.inc:1604
    #4 0x7f8db2f211ce in __interceptor___fprintf_chk ../../../../src/libsanitizer/sanitizer_common/sanitizer_common_interceptors.inc:1666
    #5 0x557d9ec1e2ac in fprintf /usr/include/x86_64-linux-gnu/bits/stdio2.h:100
    #6 0x557d9ec1e2ac in constant_tostring as3/pool.c:778
    #7 0x557d9ec147f4 in traits_dump as3/abc.c:607
    #8 0x557d9ec14159 in dump_method as3/abc.c:403
    #9 0x557d9ec1468e in traits_dump as3/abc.c:596
    #10 0x557d9ec14159 in dump_method as3/abc.c:403
    #11 0x557d9ec1468e in traits_dump as3/abc.c:596
    #12 0x557d9ec14159 in dump_method as3/abc.c:403
    #13 0x557d9ec1468e in traits_dump as3/abc.c:596
    #14 0x557d9ec14159 in dump_method as3/abc.c:403
    #15 0x557d9ec1468e in traits_dump as3/abc.c:596
    #16 0x557d9ec14159 in dump_method as3/abc.c:403
    #17 0x557d9ec1468e in traits_dump as3/abc.c:596
    #18 0x557d9ec14159 in dump_method as3/abc.c:403
    #19 0x557d9ec1468e in traits_dump as3/abc.c:596
    #20 0x557d9ec14159 in dump_method as3/abc.c:403
    #21 0x557d9ec1468e in traits_dump as3/abc.c:596
    #22 0x557d9ec14159 in dump_method as3/abc.c:403
    #23 0x557d9ec1468e in traits_dump as3/abc.c:596
    #24 0x557d9ec14159 in dump_method as3/abc.c:403
    #25 0x557d9ec1468e in traits_dump as3/abc.c:596
    #26 0x557d9ec14159 in dump_method as3/abc.c:403
    #27 0x557d9ec1468e in traits_dump as3/abc.c:596
    #28 0x557d9ec14159 in dump_method as3/abc.c:403
    #29 0x557d9ec1468e in traits_dump as3/abc.c:596
    #30 0x557d9ec14159 in dump_method as3/abc.c:403
    #31 0x557d9ec1468e in traits_dump as3/abc.c:596
    #32 0x557d9ec14159 in dump_method as3/abc.c:403
    #33 0x557d9ec1468e in traits_dump as3/abc.c:596
    #34 0x557d9ec14159 in dump_method as3/abc.c:403
    #35 0x557d9ec1468e in traits_dump as3/abc.c:596
    #36 0x557d9ec14159 in dump_method as3/abc.c:403
    #37 0x557d9ec1468e in traits_dump as3/abc.c:596
    #38 0x557d9ec14159 in dump_method as3/abc.c:403
    #39 0x557d9ec1468e in traits_dump as3/abc.c:596
    #40 0x557d9ec14159 in dump_method as3/abc.c:403
    #41 0x557d9ec1468e in traits_dump as3/abc.c:596
    #42 0x557d9ec14159 in dump_method as3/abc.c:403
    #43 0x557d9ec1468e in traits_dump as3/abc.c:596
    #44 0x557d9ec14159 in dump_method as3/abc.c:403
    #45 0x557d9ec1468e in traits_dump as3/abc.c:596
    #46 0x557d9ec14159 in dump_method as3/abc.c:403
    #47 0x557d9ec1468e in traits_dump as3/abc.c:596
    #48 0x557d9ec14159 in dump_method as3/abc.c:403
    #49 0x557d9ec1468e in traits_dump as3/abc.c:596
    #50 0x557d9ec14159 in dump_method as3/abc.c:403
    #51 0x557d9ec1468e in traits_dump as3/abc.c:596
    #52 0x557d9ec14159 in dump_method as3/abc.c:403
    #53 0x557d9ec1468e in traits_dump as3/abc.c:596
    #54 0x557d9ec14159 in dump_method as3/abc.c:403
    #55 0x557d9ec1468e in traits_dump as3/abc.c:596
    #56 0x557d9ec14159 in dump_method as3/abc.c:403
    #57 0x557d9ec1468e in traits_dump as3/abc.c:596
    #58 0x557d9ec14159 in dump_method as3/abc.c:403
    #59 0x557d9ec1468e in traits_dump as3/abc.c:596
    #60 0x557d9ec14159 in dump_method as3/abc.c:403
    #61 0x557d9ec1468e in traits_dump as3/abc.c:596
    #62 0x557d9ec14159 in dump_method as3/abc.c:403
    #63 0x557d9ec1468e in traits_dump as3/abc.c:596
    #64 0x557d9ec14159 in dump_method as3/abc.c:403
    #65 0x557d9ec1468e in traits_dump as3/abc.c:596
    #66 0x557d9ec14159 in dump_method as3/abc.c:403
    #67 0x557d9ec1468e in traits_dump as3/abc.c:596
    #68 0x557d9ec14159 in dump_method as3/abc.c:403
    #69 0x557d9ec1468e in traits_dump as3/abc.c:596
    #70 0x557d9ec14159 in dump_method as3/abc.c:403
    #71 0x557d9ec1468e in traits_dump as3/abc.c:596
    #72 0x557d9ec14159 in dump_method as3/abc.c:403
    #73 0x557d9ec1468e in traits_dump as3/abc.c:596
    #74 0x557d9ec14159 in dump_method as3/abc.c:403
    #75 0x557d9ec1468e in traits_dump as3/abc.c:596
    #76 0x557d9ec14159 in dump_method as3/abc.c:403
    #77 0x557d9ec1468e in traits_dump as3/abc.c:596
    #78 0x557d9ec14159 in dump_method as3/abc.c:403
    #79 0x557d9ec1468e in traits_dump as3/abc.c:596
    #80 0x557d9ec14159 in dump_method as3/abc.c:403
    #81 0x557d9ec1468e in traits_dump as3/abc.c:596
    #82 0x557d9ec14159 in dump_method as3/abc.c:403
    #83 0x557d9ec1468e in traits_dump as3/abc.c:596
    #84 0x557d9ec14159 in dump_method as3/abc.c:403
    #85 0x557d9ec1468e in traits_dump as3/abc.c:596
    #86 0x557d9ec14159 in dump_method as3/abc.c:403
    #87 0x557d9ec1468e in traits_dump as3/abc.c:596
    #88 0x557d9ec14159 in dump_method as3/abc.c:403
    #89 0x557d9ec1468e in traits_dump as3/abc.c:596
    #90 0x557d9ec14159 in dump_method as3/abc.c:403
    #91 0x557d9ec1468e in traits_dump as3/abc.c:596
    #92 0x557d9ec14159 in dump_method as3/abc.c:403
    #93 0x557d9ec1468e in traits_dump as3/abc.c:596
    #94 0x557d9ec14159 in dump_method as3/abc.c:403
    #95 0x557d9ec1468e in traits_dump as3/abc.c:596
    #96 0x557d9ec14159 in dump_method as3/abc.c:403
    #97 0x557d9ec1468e in traits_dump as3/abc.c:596
    #98 0x557d9ec14159 in dump_method as3/abc.c:403
    #99 0x557d9ec1468e in traits_dump as3/abc.c:596
    #100 0x557d9ec14159 in dump_method as3/abc.c:403
    #101 0x557d9ec1468e in traits_dump as3/abc.c:596
    #102 0x557d9ec14159 in dump_method as3/abc.c:403
    #103 0x557d9ec1468e in traits_dump as3/abc.c:596
    #104 0x557d9ec14159 in dump_method as3/abc.c:403
    #105 0x557d9ec1468e in traits_dump as3/abc.c:596
    #106 0x557d9ec14159 in dump_method as3/abc.c:403
    #107 0x557d9ec1468e in traits_dump as3/abc.c:596
    #108 0x557d9ec14159 in dump_method as3/abc.c:403
    #109 0x557d9ec1468e in traits_dump as3/abc.c:596
    #110 0x557d9ec14159 in dump_method as3/abc.c:403
    #111 0x557d9ec1468e in traits_dump as3/abc.c:596
    #112 0x557d9ec14159 in dump_method as3/abc.c:403
    #113 0x557d9ec1468e in traits_dump as3/abc.c:596
    #114 0x557d9ec14159 in dump_method as3/abc.c:403
    #115 0x557d9ec1468e in traits_dump as3/abc.c:596
    #116 0x557d9ec14159 in dump_method as3/abc.c:403
    #117 0x557d9ec1468e in traits_dump as3/abc.c:596
    #118 0x557d9ec14159 in dump_method as3/abc.c:403
    #119 0x557d9ec1468e in traits_dump as3/abc.c:596
    #120 0x557d9ec14159 in dump_method as3/abc.c:403
    #121 0x557d9ec1468e in traits_dump as3/abc.c:596
    #122 0x557d9ec14159 in dump_method as3/abc.c:403
    #123 0x557d9ec1468e in traits_dump as3/abc.c:596
    #124 0x557d9ec14159 in dump_method as3/abc.c:403
    #125 0x557d9ec1468e in traits_dump as3/abc.c:596
    #126 0x557d9ec14159 in dump_method as3/abc.c:403
    #127 0x557d9ec1468e in traits_dump as3/abc.c:596
    #128 0x557d9ec14159 in dump_method as3/abc.c:403
    #129 0x557d9ec1468e in traits_dump as3/abc.c:596
    #130 0x557d9ec14159 in dump_method as3/abc.c:403
    #131 0x557d9ec1468e in traits_dump as3/abc.c:596
    #132 0x557d9ec14159 in dump_method as3/abc.c:403
    #133 0x557d9ec1468e in traits_dump as3/abc.c:596
    #134 0x557d9ec14159 in dump_method as3/abc.c:403
    #135 0x557d9ec1468e in traits_dump as3/abc.c:596
    #136 0x557d9ec14159 in dump_method as3/abc.c:403
    #137 0x557d9ec1468e in traits_dump as3/abc.c:596
    #138 0x557d9ec14159 in dump_method as3/abc.c:403
    #139 0x557d9ec1468e in traits_dump as3/abc.c:596
    #140 0x557d9ec14159 in dump_method as3/abc.c:403
    #141 0x557d9ec1468e in traits_dump as3/abc.c:596
    #142 0x557d9ec14159 in dump_method as3/abc.c:403
    #143 0x557d9ec1468e in traits_dump as3/abc.c:596
    #144 0x557d9ec14159 in dump_method as3/abc.c:403
    #145 0x557d9ec1468e in traits_dump as3/abc.c:596
    #146 0x557d9ec14159 in dump_method as3/abc.c:403
    #147 0x557d9ec1468e in traits_dump as3/abc.c:596
    #148 0x557d9ec14159 in dump_method as3/abc.c:403
    #149 0x557d9ec1468e in traits_dump as3/abc.c:596
    #150 0x557d9ec14159 in dump_method as3/abc.c:403
    #151 0x557d9ec1468e in traits_dump as3/abc.c:596
    #152 0x557d9ec14159 in dump_method as3/abc.c:403
    #153 0x557d9ec1468e in traits_dump as3/abc.c:596
    #154 0x557d9ec14159 in dump_method as3/abc.c:403
    #155 0x557d9ec1468e in traits_dump as3/abc.c:596
    #156 0x557d9ec14159 in dump_method as3/abc.c:403
    #157 0x557d9ec1468e in traits_dump as3/abc.c:596
    #158 0x557d9ec14159 in dump_method as3/abc.c:403
    #159 0x557d9ec1468e in traits_dump as3/abc.c:596
    #160 0x557d9ec14159 in dump_method as3/abc.c:403
    #161 0x557d9ec1468e in traits_dump as3/abc.c:596
    #162 0x557d9ec14159 in dump_method as3/abc.c:403
    #163 0x557d9ec1468e in traits_dump as3/abc.c:596
    #164 0x557d9ec14159 in dump_method as3/abc.c:403
    #165 0x557d9ec1468e in traits_dump as3/abc.c:596
    #166 0x557d9ec14159 in dump_method as3/abc.c:403
    #167 0x557d9ec1468e in traits_dump as3/abc.c:596
    #168 0x557d9ec14159 in dump_method as3/abc.c:403
    #169 0x557d9ec1468e in traits_dump as3/abc.c:596
    #170 0x557d9ec14159 in dump_method as3/abc.c:403
    #171 0x557d9ec1468e in traits_dump as3/abc.c:596
    #172 0x557d9ec14159 in dump_method as3/abc.c:403
    #173 0x557d9ec1468e in traits_dump as3/abc.c:596
    #174 0x557d9ec14159 in dump_method as3/abc.c:403
    #175 0x557d9ec1468e in traits_dump as3/abc.c:596
    #176 0x557d9ec14159 in dump_method as3/abc.c:403
    #177 0x557d9ec1468e in traits_dump as3/abc.c:596
    #178 0x557d9ec14159 in dump_method as3/abc.c:403
    #179 0x557d9ec1468e in traits_dump as3/abc.c:596
    #180 0x557d9ec14159 in dump_method as3/abc.c:403
    #181 0x557d9ec1468e in traits_dump as3/abc.c:596
    #182 0x557d9ec14159 in dump_method as3/abc.c:403
    #183 0x557d9ec1468e in traits_dump as3/abc.c:596
    #184 0x557d9ec14159 in dump_method as3/abc.c:403
    #185 0x557d9ec1468e in traits_dump as3/abc.c:596
    #186 0x557d9ec14159 in dump_method as3/abc.c:403
    #187 0x557d9ec1468e in traits_dump as3/abc.c:596
    #188 0x557d9ec14159 in dump_method as3/abc.c:403
    #189 0x557d9ec1468e in traits_dump as3/abc.c:596
    #190 0x557d9ec14159 in dump_method as3/abc.c:403
    #191 0x557d9ec1468e in traits_dump as3/abc.c:596
    #192 0x557d9ec14159 in dump_method as3/abc.c:403
    #193 0x557d9ec1468e in traits_dump as3/abc.c:596
    #194 0x557d9ec14159 in dump_method as3/abc.c:403
    #195 0x557d9ec1468e in traits_dump as3/abc.c:596
    #196 0x557d9ec14159 in dump_method as3/abc.c:403
    #197 0x557d9ec1468e in traits_dump as3/abc.c:596
    #198 0x557d9ec14159 in dump_method as3/abc.c:403
    #199 0x557d9ec1468e in traits_dump as3/abc.c:596
    #200 0x557d9ec14159 in dump_method as3/abc.c:403
    #201 0x557d9ec1468e in traits_dump as3/abc.c:596
    #202 0x557d9ec14159 in dump_method as3/abc.c:403
    #203 0x557d9ec1468e in traits_dump as3/abc.c:596
    #204 0x557d9ec14159 in dump_method as3/abc.c:403
    #205 0x557d9ec1468e in traits_dump as3/abc.c:596
    #206 0x557d9ec14159 in dump_method as3/abc.c:403
    #207 0x557d9ec1468e in traits_dump as3/abc.c:596
    #208 0x557d9ec14159 in dump_method as3/abc.c:403
    #209 0x557d9ec1468e in traits_dump as3/abc.c:596
    #210 0x557d9ec14159 in dump_method as3/abc.c:403
    #211 0x557d9ec1468e in traits_dump as3/abc.c:596
    #212 0x557d9ec14159 in dump_method as3/abc.c:403
    #213 0x557d9ec1468e in traits_dump as3/abc.c:596
    #214 0x557d9ec14159 in dump_method as3/abc.c:403
    #215 0x557d9ec1468e in traits_dump as3/abc.c:596
    #216 0x557d9ec14159 in dump_method as3/abc.c:403
    #217 0x557d9ec1468e in traits_dump as3/abc.c:596
    #218 0x557d9ec14159 in dump_method as3/abc.c:403
    #219 0x557d9ec1468e in traits_dump as3/abc.c:596
    #220 0x557d9ec14159 in dump_method as3/abc.c:403
    #221 0x557d9ec1468e in traits_dump as3/abc.c:596
    #222 0x557d9ec14159 in dump_method as3/abc.c:403
    #223 0x557d9ec1468e in traits_dump as3/abc.c:596
    #224 0x557d9ec14159 in dump_method as3/abc.c:403
    #225 0x557d9ec1468e in traits_dump as3/abc.c:596
    #226 0x557d9ec14159 in dump_method as3/abc.c:403
    #227 0x557d9ec1468e in traits_dump as3/abc.c:596
    #228 0x557d9ec14159 in dump_method as3/abc.c:403
    #229 0x557d9ec1468e in traits_dump as3/abc.c:596
    #230 0x557d9ec14159 in dump_method as3/abc.c:403
    #231 0x557d9ec1468e in traits_dump as3/abc.c:596
    #232 0x557d9ec14159 in dump_method as3/abc.c:403
    #233 0x557d9ec1468e in traits_dump as3/abc.c:596
    #234 0x557d9ec14159 in dump_method as3/abc.c:403
    #235 0x557d9ec1468e in traits_dump as3/abc.c:596
    #236 0x557d9ec14159 in dump_method as3/abc.c:403
    #237 0x557d9ec1468e in traits_dump as3/abc.c:596
    #238 0x557d9ec14159 in dump_method as3/abc.c:403
    #239 0x557d9ec1468e in traits_dump as3/abc.c:596
    #240 0x557d9ec14159 in dump_method as3/abc.c:403
    #241 0x557d9ec1468e in traits_dump as3/abc.c:596
    #242 0x557d9ec14159 in dump_method as3/abc.c:403
    #243 0x557d9ec1468e in traits_dump as3/abc.c:596
    #244 0x557d9ec14159 in dump_method as3/abc.c:403
    #245 0x557d9ec1468e in traits_dump as3/abc.c:596
    #246 0x557d9ec14159 in dump_method as3/abc.c:403
    #247 0x557d9ec1468e in traits_dump as3/abc.c:596
    #248 0x557d9ec14159 in dump_method as3/abc.c:403
    #249 0x557d9ec1468e in traits_dump as3/abc.c:596

SUMMARY: AddressSanitizer: stack-overflow /build/glibc-SzIz7B/glibc-2.31/stdio-common/vfprintf-internal.c:1289 in __vfprintf_internal
==963740==ABORTING


```

### Discover
zhangzhourui, luhui, tianzhihong, zhanghaonan at Guangzhou University.

