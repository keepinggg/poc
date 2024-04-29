# 1.NULL pointer dereference
## env
ubuntu20.04 

gcc version 9.4.0 (Ubuntu 9.4.0-1ubuntu1~20.04.1)

swfc - part of swftools 0.9.2

## sample
[poc_SEGV_compileSWFActionCode](https://github.com/keepinggg/poc/blob/main/poc_of_swfc/poc_SEGV_compileSWFActionCode)

## crash
```
./swfc poc_SEGV_compileSWFActionCode
AddressSanitizer:DEADLYSIGNAL
=================================================================
==207836==ERROR: AddressSanitizer: SEGV on unknown address 0x000000000000 (pc 0x5626051b38f7 bp 0x7ffe5e722360 sp 0x7ffe5e722270 T0)
==207836==The signal is caused by a READ memory access.
==207836==Hint: address points to the zero page.
    #0 0x5626051b38f6 in compileSWFActionCode action/actioncompiler.c:94
    #1 0x56260517532e in swf_ActionCompile modules/swfaction.c:1111
    #2 0x5626051565b9 in s_action /mnt/hgfs/ubuntu/cve/swftools/swftools-master/src/swfc.c:1966
    #3 0x56260515668c in c_action /mnt/hgfs/ubuntu/cve/swftools/swftools-master/src/swfc.c:4162
    #4 0x56260516753a in parseArgumentsForCommand /mnt/hgfs/ubuntu/cve/swftools/swftools-master/src/swfc.c:4475
    #5 0x56260516753a in main /mnt/hgfs/ubuntu/cve/swftools/swftools-master/src/swfc.c:4598
    #6 0x7fbf0728f082 in __libc_start_main ../csu/libc-start.c:308
    #7 0x56260514813d in _start (/mnt/hgfs/ubuntu/cve/swftools/swftools-master/src/swfc+0xed13d)

AddressSanitizer can not provide additional info.
SUMMARY: AddressSanitizer: SEGV action/actioncompiler.c:94 in compileSWFActionCode
==207836==ABORTING

```

### CVE- ID
CVE-2024-28458

### Discover
zhangzhourui, luhui, tianzhihong at Guangzhou University.

# 2.memory leak
## env
ubuntu20.04 

gcc version 9.4.0 (Ubuntu 9.4.0-1ubuntu1~20.04.1)

swfc - part of swftools 0.9.2

## sample
[memory_leak1](https://github.com/keepinggg/poc/blob/main/poc_of_swfc/memory_leak1)
## crash
```
./swfc memory_leak1
output.swf:2:4: warning: Couldn't resolve 'str', doing late binding
output.swf:2:10: warning: Couldn't resolve 'Tex', doing late binding
output.swf:2:2: error: syntax error: (null) (identifiers must not start with a digit)
output.swf

=================================================================
==53502==ERROR: LeakSanitizer: detected memory leaks

Direct leak of 168 byte(s) in 7 object(s) allocated from:
    #0 0x7f09a49c8808 in __interceptor_malloc ../../../../src/libsanitizer/asan/asan_malloc_linux.cc:144
    #1 0x55a28457cd65 in rfx_alloc /mnt/hgfs/ubuntu/cve/swftools/swftools-master/lib/mem.c:30

Direct leak of 22 byte(s) in 2 object(s) allocated from:
    #0 0x7f09a49513ed in __interceptor_strdup ../../../../src/libsanitizer/asan/asan_interceptors.cc:445
    #1 0x55a2844b17c2 in initialize_file as3/parser_help.c:23

Direct leak of 12 byte(s) in 3 object(s) allocated from:
    #0 0x7f09a49c8808 in __interceptor_malloc ../../../../src/libsanitizer/asan/asan_malloc_linux.cc:144
    #1 0x55a2845128a6 in handleIdentifier /mnt/hgfs/ubuntu/cve/swftools/swftools-master/lib/tokenizer.lex:475
    #2 0x55a2845128a6 in as3_lex /mnt/hgfs/ubuntu/cve/swftools/swftools-master/lib/tokenizer.lex:685

Direct leak of 11 byte(s) in 1 object(s) allocated from:
    #0 0x7f09a49513ed in __interceptor_strdup ../../../../src/libsanitizer/asan/asan_interceptors.cc:445
    #1 0x55a2844f221a in enter_file as3/files.c:298

Direct leak of 11 byte(s) in 1 object(s) allocated from:
    #0 0x7f09a49513ed in __interceptor_strdup ../../../../src/libsanitizer/asan/asan_interceptors.cc:445
    #1 0x55a2844f21f6 in enter_file as3/files.c:296

Direct leak of 11 byte(s) in 1 object(s) allocated from:
    #0 0x7f09a49513ed in __interceptor_strdup ../../../../src/libsanitizer/asan/asan_interceptors.cc:445
    #1 0x55a2844f2208 in enter_file as3/files.c:297

Indirect leak of 216 byte(s) in 11 object(s) allocated from:
    #0 0x7f09a49c8a06 in __interceptor_calloc ../../../../src/libsanitizer/asan/asan_malloc_linux.cc:153
    #1 0x55a28457ce6d in rfx_calloc /mnt/hgfs/ubuntu/cve/swftools/swftools-master/lib/mem.c:69

Indirect leak of 160 byte(s) in 5 object(s) allocated from:
    #0 0x7f09a49c8808 in __interceptor_malloc ../../../../src/libsanitizer/asan/asan_malloc_linux.cc:144
    #1 0x55a28457cd65 in rfx_alloc /mnt/hgfs/ubuntu/cve/swftools/swftools-master/lib/mem.c:30

Indirect leak of 26 byte(s) in 4 object(s) allocated from:
    #0 0x7f09a49513ed in __interceptor_strdup ../../../../src/libsanitizer/asan/asan_interceptors.cc:445
    #1 0x55a28455f951 in charptr_dup /mnt/hgfs/ubuntu/cve/swftools/swftools-master/lib/q.c:987

SUMMARY: AddressSanitizer: 637 byte(s) leaked in 35 allocation(s).
```

### Discover
zhangzhourui, luhui, tianzhihong at Guangzhou University.

# 3.memory leak
## env
ubuntu20.04 

gcc version 9.4.0 (Ubuntu 9.4.0-1ubuntu1~20.04.1)

swfc - part of swftools 0.9.2

## sample
[memory_leak2](https://github.com/keepinggg/poc/blob/main/poc_of_swfc/memory_leak2)
## crash
```
./swfc memory_leak2
output.swf:2:79: error: syntax error: (null) (identifiers must not start with a digit)
output.swf

=================================================================
==53505==ERROR: LeakSanitizer: detected memory leaks

Direct leak of 32 byte(s) in 6 object(s) allocated from:
    #0 0x7f8fb6c5b808 in __interceptor_malloc ../../../../src/libsanitizer/asan/asan_malloc_linux.cc:144
    #1 0x5561fb4078a6 in handleIdentifier /mnt/hgfs/ubuntu/cve/swftools/swftools-master/lib/tokenizer.lex:475
    #2 0x5561fb4078a6 in as3_lex /mnt/hgfs/ubuntu/cve/swftools/swftools-master/lib/tokenizer.lex:685

Direct leak of 18 byte(s) in 9 object(s) allocated from:
    #0 0x7f8fb6c5b808 in __interceptor_malloc ../../../../src/libsanitizer/asan/asan_malloc_linux.cc:144
    #1 0x5561fb3ff5c4 in handleregexp /mnt/hgfs/ubuntu/cve/swftools/swftools-master/lib/tokenizer.lex:433
    #2 0x5561fb3ff5c4 in as3_lex /mnt/hgfs/ubuntu/cve/swftools/swftools-master/lib/tokenizer.lex:575

SUMMARY: AddressSanitizer: 50 byte(s) leaked in 15 allocation(s).
```

### Discover
zhangzhourui, luhui, tianzhihong at Guangzhou University.
