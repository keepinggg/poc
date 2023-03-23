## SEGV
### env
ubuntu20.04 

gcc version 9.4.0 (Ubuntu 9.4.0-1ubuntu1~20.04.1)

xpdf4.04

### sample
[poc.zip](https://github.com/keepinggg/poc/blob/main/poc_of_xpdf/id2)

### crash
```
./pdftotext /mnt/hgfs/ubuntu/cve/xpdf/xpdf-4.04/out/default/crashes/id:000002,sig:11,src:000873,time:2679871,execs:139753,op:havoc,rep:8
Syntax Error: Couldn't read xref table
Syntax Warning: PDF file is damaged - attempting to reconstruct xref table...
Syntax Error (623): Dictionary key must be a name object
Syntax Error (631): Dictionary key must be a name object
Syntax Error (158): Dictionary key must be a name object
Syntax Error (164): Dictionary key must be a name object
Syntax Error (172): Dictionary key must be a name object
Syntax Error (292): Dictionary key must be a name object
Syntax Error (460): Dictionary key must be a name object
Syntax Error (623): Dictionary key must be a name object
Syntax Error (631): Dictionary key must be a name object
Syntax Error: End of file inside array
Syntax Error: End of file inside dictionary
AddressSanitizer:DEADLYSIGNAL
=================================================================
==1880690==ERROR: AddressSanitizer: stack-overflow on address 0x7ffd2529cff0 (pc 0x7f1ccd1d75b8 bp 0x6030001c3350 sp 0x7ffd2529cfe0 T0)
    #0 0x7f1ccd1d75b7 in __sanitizer::StackDepotNode::hash(__sanitizer::StackTrace const&) ../../../../src/libsanitizer/sanitizer_common/sanitizer_stackdepot.cc:64
    #1 0x7f1ccd1d75b7 in __sanitizer::StackDepotBase<__sanitizer::StackDepotNode, 1, 20>::Put(__sanitizer::StackTrace, bool*) ../../../../src/libsanitizer/sanitizer_common/sanitizer_stackdepotbase.h:100
    #2 0x7f1ccd1d724b in __sanitizer::StackDepotPut(__sanitizer::StackTrace) ../../../../src/libsanitizer/sanitizer_common/sanitizer_stackdepot.cc:110
    #3 0x7f1ccd0d5151 in __asan::Allocator::Allocate(unsigned long, unsigned long, __sanitizer::BufferedStackTrace*, __asan::AllocType, bool) ../../../../src/libsanitizer/asan/asan_allocator.cc:508
    #4 0x7f1ccd0d17ec in __asan::asan_memalign(unsigned long, unsigned long, __sanitizer::BufferedStackTrace*, __asan::AllocType) ../../../../src/libsanitizer/asan/asan_allocator.cc:922
    #5 0x7f1ccd1b8745 in operator new[](unsigned long) ../../../../src/libsanitizer/asan/asan_new_delete.cc:107
    #6 0x56550069bf57 in GString::resize(int) /home/ther/fuzzing/xpdf-4.04/goo/GString.cc:119
    #7 0x56550069bf57 in GString::GString(GString*) /home/ther/fuzzing/xpdf-4.04/goo/GString.cc:163
    #8 0x565500634d53 in GString::copy() /home/ther/fuzzing/xpdf-4.04/goo/GString.h:42
    #9 0x565500634d53 in Object::copy(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Object.cc:84
    #10 0x56550052e051 in Object::arrayGet(int, Object*, int) /home/ther/fuzzing/xpdf-4.04/xpdf/Object.h:243
    #11 0x56550052e051 in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:566
    #12 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #13 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #14 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #15 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #16 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #17 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #18 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #19 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #20 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #21 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #22 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #23 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #24 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #25 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #26 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #27 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #28 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #29 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #30 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #31 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #32 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #33 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #34 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #35 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #36 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #37 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #38 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #39 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #40 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #41 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #42 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #43 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #44 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #45 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #46 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #47 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #48 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #49 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #50 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #51 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #52 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #53 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #54 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #55 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #56 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #57 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #58 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #59 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #60 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #61 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #62 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #63 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #64 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #65 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #66 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #67 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #68 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #69 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #70 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #71 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #72 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #73 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #74 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #75 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #76 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #77 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #78 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #79 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #80 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #81 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #82 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #83 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #84 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #85 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #86 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #87 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #88 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #89 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #90 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #91 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #92 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #93 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #94 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #95 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #96 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #97 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #98 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #99 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #100 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #101 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #102 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #103 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #104 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #105 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #106 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #107 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #108 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #109 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #110 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #111 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #112 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #113 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #114 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #115 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #116 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #117 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #118 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #119 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #120 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #121 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #122 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #123 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #124 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #125 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #126 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #127 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #128 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #129 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #130 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #131 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #132 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #133 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #134 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #135 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #136 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #137 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #138 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #139 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #140 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #141 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #142 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #143 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #144 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #145 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #146 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #147 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #148 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #149 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #150 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #151 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #152 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #153 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #154 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #155 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #156 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #157 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #158 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #159 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #160 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #161 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #162 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #163 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #164 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #165 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #166 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #167 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #168 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #169 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #170 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #171 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #172 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #173 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #174 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #175 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #176 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #177 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #178 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #179 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #180 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #181 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #182 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #183 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #184 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #185 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #186 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #187 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #188 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #189 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #190 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #191 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #192 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #193 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #194 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #195 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #196 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #197 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #198 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #199 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #200 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #201 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #202 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #203 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #204 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #205 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #206 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #207 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #208 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #209 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #210 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #211 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #212 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #213 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #214 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #215 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #216 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #217 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #218 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #219 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #220 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #221 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #222 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #223 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #224 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #225 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #226 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #227 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #228 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #229 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #230 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #231 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #232 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #233 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #234 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #235 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #236 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #237 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #238 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #239 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #240 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #241 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #242 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #243 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #244 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #245 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #246 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #247 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #248 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #249 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #250 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #251 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567
    #252 0x56550052e05e in Catalog::countPageTree(Object*) /home/ther/fuzzing/xpdf-4.04/xpdf/Catalog.cc:567

SUMMARY: AddressSanitizer: stack-overflow ../../../../src/libsanitizer/sanitizer_common/sanitizer_stackdepot.cc:64 in __sanitizer::StackDepotNode::hash(__sanitizer::StackTrace const&)
==1880690==ABORTING
```

### CVE-ID
CVE-2023-27655

### Discover
zhangzhourui, luhui, tianzhihong at Guangzhou University.


