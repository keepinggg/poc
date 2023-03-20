## SEGV
### env
ubuntu20.04 
gcc version 9.4.0 (Ubuntu 9.4.0-1ubuntu1~20.04.1)
ttftool - part of swftools 0.9.2

### sample
[poc.zip](https://github.com/matthiaskramm/swftools/files/10101243/poc.zip)

### crash
```
./ttftool poc1
AddressSanitizer:DEADLYSIGNAL
=================================================================
==3017452==ERROR: AddressSanitizer: SEGV on unknown address 0x615ff2000080 (pc 0x556969fea2d4 bp 0x000000000024 sp 0x7fffe586ef40 T0)
==3017452==The signal is caused by a READ memory access.
    #0 0x556969fea2d3 in readU16 /home/ther/fuzzing101/swftools-master/lib/ttf.c:88
    #1 0x556969fea2d3 in readS16 /home/ther/fuzzing101/swftools-master/lib/ttf.c:95
    #2 0x556969ffeca1 in glyf_parse /home/ther/fuzzing101/swftools-master/lib/ttf.c:1047
    #3 0x556969ffeca1 in ttf_parse_tables /home/ther/fuzzing101/swftools-master/lib/ttf.c:1892
    #4 0x556969ffeca1 in ttf_load /home/ther/fuzzing101/swftools-master/lib/ttf.c:2180
    #5 0x55696a00f6b7 in ttf_open /home/ther/fuzzing101/swftools-master/lib/ttf.c:2435
    #6 0x556969fea0d5 in main /home/ther/fuzzing101/swftools-master/src/ttftool.c:91
    #7 0x7ff3f1649082 in __libc_start_main ../csu/libc-start.c:308
    #8 0x556969fe988d in _start (/home/ther/fuzzing/swftools-master/src/ttftool+0x688d)

AddressSanitizer can not provide additional info.
SUMMARY: AddressSanitizer: SEGV /home/ther/fuzzing101/swftools-master/lib/ttf.c:88 in readU16
==3017452==ABORTING
```

### CVE-ID
CVE-2022-46440

### Discover
zhangzhourui, luhui, tianzhihong, zhanghaonan at Guangzhou University.
