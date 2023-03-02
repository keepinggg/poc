# SEGV
## env
ubuntu20.04
gcc version 9.4.0 (Ubuntu 9.4.0-1ubuntu1~20.04.1)
XPDF commit ffaf11c

## sample
[id189.zip](https://github.com/jhcloos/xpdf/files/10868398/id189.zip)

## reproduce
```
CFLAGS="-g -fsanitize=address" CXXFLAGS="-g -fsanitize=address" LDFLAGS="-g -fsanitize=address" ./configure
make
./pdftotext poc
```

## crash
```
AddressSanitizer:DEADLYSIGNAL
=================================================================
==3166724==ERROR: AddressSanitizer: SEGV on unknown address 0x61a8d2d2d54c (pc 0x55b73eee93da bp 0x7ffde628f900 sp 0x7ffde628f8e0 T0)
==3166724==The signal is caused by a READ memory access.
    #0 0x55b73eee93d9 in DCTStream::readHuffSym(DCTHuffTable*) /mnt/hgfs/ubuntu/cve/xpdf/xpdf-master/xpdf/Stream.cc:3119
    #1 0x55b73eee35e8 in DCTStream::readDataUnit(DCTHuffTable*, DCTHuffTable*, int*, int*) /mnt/hgfs/ubuntu/cve/xpdf/xpdf-master/xpdf/Stream.cc:2607
    #2 0x55b73eedf36c in DCTStream::readMCURow() /mnt/hgfs/ubuntu/cve/xpdf/xpdf-master/xpdf/Stream.cc:2392
    #3 0x55b73eede3a2 in DCTStream::getChar() /mnt/hgfs/ubuntu/cve/xpdf/xpdf-master/xpdf/Stream.cc:2316
    #4 0x55b73eeb6869 in Object::streamGetChar() /mnt/hgfs/ubuntu/cve/xpdf/xpdf-master/xpdf/Object.h:288
    #5 0x55b73eeaacf5 in Lexer::getChar() /mnt/hgfs/ubuntu/cve/xpdf/xpdf-master/xpdf/Lexer.cc:92
    #6 0x55b73eeaaebf in Lexer::getObj(Object*) /mnt/hgfs/ubuntu/cve/xpdf/xpdf-master/xpdf/Lexer.cc:124
    #7 0x55b73eec21e9 in Parser::Parser(XRef*, Lexer*, int) /mnt/hgfs/ubuntu/cve/xpdf/xpdf-master/xpdf/Parser.cc:33
    #8 0x55b73edce0d1 in Gfx::display(Object*, int) /mnt/hgfs/ubuntu/cve/xpdf/xpdf-master/xpdf/Gfx.cc:641
    #9 0x55b73eebfe4a in Page::displaySlice(OutputDev*, double, double, int, int, int, int, int, int, int, int, int (*)(void*), void*) /mnt/hgfs/ubuntu/cve/xpdf/xpdf-master/xpdf/Page.cc:360
    #10 0x55b73eebf6ce in Page::display(OutputDev*, double, double, int, int, int, int, int (*)(void*), void*) /mnt/hgfs/ubuntu/cve/xpdf/xpdf-master/xpdf/Page.cc:308
    #11 0x55b73eec5806 in PDFDoc::displayPage(OutputDev*, int, double, double, int, int, int, int, int (*)(void*), void*) /mnt/hgfs/ubuntu/cve/xpdf/xpdf-master/xpdf/PDFDoc.cc:384
    #12 0x55b73eec588e in PDFDoc::displayPages(OutputDev*, int, int, double, double, int, int, int, int, int (*)(void*), void*) /mnt/hgfs/ubuntu/cve/xpdf/xpdf-master/xpdf/PDFDoc.cc:397
    #13 0x55b73ef38671 in main /mnt/hgfs/ubuntu/cve/xpdf/xpdf-master/xpdf/pdftotext.cc:241
    #14 0x7fb136de7082 in __libc_start_main ../csu/libc-start.c:308
    #15 0x55b73ed87ecd in _start (/mnt/hgfs/ubuntu/cve/xpdf/xpdf-master/xpdf/pdftotext+0xe4ecd)

AddressSanitizer can not provide additional info.
SUMMARY: AddressSanitizer: SEGV /mnt/hgfs/ubuntu/cve/xpdf/xpdf-master/xpdf/Stream.cc:3119 in DCTStream::readHuffSym(DCTHuffTable*)
==3166724==ABORTING
```

