# 1.NULL pointer dereference
## env
ubuntu20.04 

gcc version 9.4.0 (Ubuntu 9.4.0-1ubuntu1~20.04.1)

swfdump - part of swftools 0.9.2

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


### Discover
zhangzhourui, luhui, tianzhihong at Guangzhou University.

