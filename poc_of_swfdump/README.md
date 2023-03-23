# heap-buffer-overflow
## env
ubuntu20.04 

gcc version 9.4.0 (Ubuntu 9.4.0-1ubuntu1~20.04.1)

swfdump - part of swftools 0.9.2

## sample
[poc.zip](https://github.com/keepinggg/poc/blob/main/poc_of_swfdump/poc)

## crash
```
./swfdump -D poc 
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
