# 1.heap-buffer-overflow
## env
ubuntu20.04 
gcc version 9.4.0 (Ubuntu 9.4.0-1ubuntu1~20.04.1)
swfrender - part of swftools 0.9.2

## sample
[id7_heap-buffer-overflow.zip](https://github.com/keepinggg/poc/blob/main/poc_of_swfrender/id7_heap-buffer-overflow.zip)

## crash
```
./swfrender id7_heap-buffer-overflow -o /dev/null
==1106906==ERROR: AddressSanitizer: heap-buffer-overflow on address 0x6070000003eb at pc 0x557c2e072578 bp 0x7ffd975b4940 sp 0x7ffd975b4930
READ of size 1 at 0x6070000003eb thread T0
    #0 0x557c2e072577 in enumerateUsedIDs_fillstyle modules/swftools.c:509
    #1 0x557c2e0728d1 in enumerateUsedIDs_styles modules/swftools.c:565
    #2 0x557c2e05c7d9 in swf_ParseShapeData modules/swfshape.c:692
    #3 0x557c2e06020d in swf_ShapeToShape2 modules/swfshape.c:884
    #4 0x557c2e04c298 in extractDefinitions readers/swf.c:375
    #5 0x557c2e04c298 in swf_open readers/swf.c:736
    #6 0x557c2e04800a in main /mnt/hgfs/ubuntu/cve/swftools/swftools-master/src/swfrender.c:174
    #7 0x7f8c197fa082 in __libc_start_main ../csu/libc-start.c:308
    #8 0x557c2e046ecd in _start (/mnt/hgfs/ubuntu/cve/swftools/swftools-master/src/swfrender+0x24ecd)

0x6070000003eb is located 0 bytes to the right of 75-byte region [0x6070000003a0,0x6070000003eb)
allocated by thread T0 here:
    #0 0x7f8c19c40808 in __interceptor_malloc ../../../../src/libsanitizer/asan/asan_malloc_linux.cc:144
    #1 0x557c2e0e4ab9 in rfx_alloc /mnt/hgfs/ubuntu/cve/swftools/swftools-master/lib/mem.c:30

SUMMARY: AddressSanitizer: heap-buffer-overflow modules/swftools.c:509 in enumerateUsedIDs_fillstyle
Shadow bytes around the buggy address:
  0x0c0e7fff8020: 00 00 00 00 00 00 00 00 00 fa fa fa fa fa 00 00
  0x0c0e7fff8030: 00 00 00 00 00 00 03 fa fa fa fa fa 00 00 00 00
  0x0c0e7fff8040: 00 00 00 00 03 fa fa fa fa fa 00 00 00 00 00 00
  0x0c0e7fff8050: 00 00 03 fa fa fa fa fa 00 00 00 00 00 00 00 00
  0x0c0e7fff8060: 00 00 fa fa fa fa 00 00 00 00 00 00 00 00 00 04
=>0x0c0e7fff8070: fa fa fa fa 00 00 00 00 00 00 00 00 00[03]fa fa
  0x0c0e7fff8080: fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa
  0x0c0e7fff8090: fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa
  0x0c0e7fff80a0: fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa
  0x0c0e7fff80b0: fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa
  0x0c0e7fff80c0: fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa
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
==1106906==ABORTING

```
### Discover
zhangzhourui, luhui, tianzhihong at Guangzhou University.


# 2.negative-size-param
## env
ubuntu20.04 
gcc version 9.4.0 (Ubuntu 9.4.0-1ubuntu1~20.04.1)
swfrender - part of swftools 0.9.2

## sample
[id107_negative-size-param.zip](https://github.com/keepinggg/poc/blob/main/poc_of_swfrender/id107_negative-size-param.zip)

## crash
```
./swfrender id107_negative-size-param -o /dev/null
=1148866==ERROR: AddressSanitizer: negative-size-param: (size=-21465837888)
    #0 0x7fe31237dfdd in __interceptor_memset ../../../../src/libsanitizer/sanitizer_common/sanitizer_common_interceptors.inc:762
    #1 0x559b516b3c75 in memset /usr/include/x86_64-linux-gnu/bits/string_fortified.h:71
    #2 0x559b516b3c75 in newclip devices/render.c:538
    #3 0x559b516b41e1 in render_startpage devices/render.c:936
    #4 0x559b516348e1 in main /mnt/hgfs/ubuntu/cve/swftools/swftools-master/src/swfrender.c:217
    #5 0x7fe311fdd082 in __libc_start_main ../csu/libc-start.c:308
    #6 0x559b51632ecd in _start (/mnt/hgfs/ubuntu/cve/swftools/swftools-master/src/swfrender+0x24ecd)

0x7fe2fef21800 is located 0 bytes inside of 8998592-byte region [0x7fe2fef21800,0x7fe2ff7b66c0)
allocated by thread T0 here:
    #0 0x7fe312423a06 in __interceptor_calloc ../../../../src/libsanitizer/asan/asan_malloc_linux.cc:153
    #1 0x559b516d0bc1 in rfx_calloc /mnt/hgfs/ubuntu/cve/swftools/swftools-master/lib/mem.c:69

SUMMARY: AddressSanitizer: negative-size-param ../../../../src/libsanitizer/sanitizer_common/sanitizer_common_interceptors.inc:762 in __interceptor_memset
==1148866==ABORTING

```
### Discover
zhangzhourui, luhui, tianzhihong at Guangzhou University.


# 3.heap-buffer-overflow 
## env
ubuntu20.04 
gcc version 9.4.0 (Ubuntu 9.4.0-1ubuntu1~20.04.1)
swfrender - part of swftools 0.9.2

## sample
[id157_heap-buffer-overflow.zip](https://github.com/keepinggg/poc/blob/main/poc_of_swfrender/id157_heap-buffer-overflow.zip)

## crash
```
./swfrender id157_heap-buffer-overflow -o /dev/null
=1167329==ERROR: AddressSanitizer: heap-buffer-overflow on address 0x7fb50bafcc00 at pc 0x7fb50f696f3d bp 0x7fffa3c52d40 sp 0x7fffa3c524e8
WRITE of size 16 at 0x7fb50bafcc00 thread T0
    #0 0x7fb50f696f3c in __interceptor_memset ../../../../src/libsanitizer/sanitizer_common/sanitizer_common_interceptors.inc:762
    #1 0x55ca7b7620cc in memset /usr/include/x86_64-linux-gnu/bits/string_fortified.h:71
    #2 0x55ca7b7620cc in render_startpage devices/render.c:922
    #3 0x55ca7b6e28e1 in main /mnt/hgfs/ubuntu/cve/swftools/swftools-master/src/swfrender.c:217
    #4 0x7fb50f2f6082 in __libc_start_main ../csu/libc-start.c:308
    #5 0x55ca7b6e0ecd in _start (/mnt/hgfs/ubuntu/cve/swftools/swftools-master/src/swfrender+0x24ecd)

0x7fb50bafcc00 is located 0 bytes to the right of 13906944-byte region [0x7fb50adb9800,0x7fb50bafcc00)
allocated by thread T0 here:
    #0 0x7fb50f73c808 in __interceptor_malloc ../../../../src/libsanitizer/asan/asan_malloc_linux.cc:144
    #1 0x55ca7b77eab9 in rfx_alloc /mnt/hgfs/ubuntu/cve/swftools/swftools-master/lib/mem.c:30
    #2 0x7fb50f2f6082 in __libc_start_main ../csu/libc-start.c:308

SUMMARY: AddressSanitizer: heap-buffer-overflow ../../../../src/libsanitizer/sanitizer_common/sanitizer_common_interceptors.inc:762 in __interceptor_memset
Shadow bytes around the buggy address:
  0x0ff721757930: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x0ff721757940: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x0ff721757950: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x0ff721757960: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x0ff721757970: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
=>0x0ff721757980:[fa]fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa
  0x0ff721757990: fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa
  0x0ff7217579a0: fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa
  0x0ff7217579b0: fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa
  0x0ff7217579c0: fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa
  0x0ff7217579d0: fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa
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
==1167329==ABORTING

```
### Discover
zhangzhourui, luhui, tianzhihong at Guangzhou University.
