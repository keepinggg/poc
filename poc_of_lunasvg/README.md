# 1.FPE
## env
ubuntu22.04 

gcc (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0

svg2png - lunasvg(v2.3.9)

## sample
[FPE_at_canvas](https://github.com/keepinggg/poc/blob/main/poc_of_lunasvg/FPE_at_canvas)

## crash
```
./svg2png FPE_at_canvas 50x50
AddressSanitizer:DEADLYSIGNAL
=================================================================
==24745==ERROR: AddressSanitizer: FPE on unknown address 0x581c181f91f8 (pc 0x581c181f91f8 bp 0x602000000750 sp 0x7ffea5458f00 T0)
    #0 0x581c181f91f8 in blend_transformed_tiled_argb.isra.0 (/home/ther/fuzz_target/lunasvg/build_asan/svg2png+0xd21f8)
    #1 0x581c181fad05 in plutovg_blend_texture (/home/ther/fuzz_target/lunasvg/build_asan/svg2png+0xd3d05)
    #2 0x581c181f374a in plutovg_stroke (/home/ther/fuzz_target/lunasvg/build_asan/svg2png+0xcc74a)
    #3 0x581c181d2cc6 in lunasvg::Canvas::stroke(lunasvg::Path const&, lunasvg::Transform const&, double, lunasvg::LineCap, lunasvg::LineJoin, double, lunasvg::DashData const&, lunasvg::BlendMode, double) /home/ther/fuzz_target/lunasvg/source/canvas.cpp:116
    #4 0x581c181bc237 in lunasvg::StrokeData::stroke(lunasvg::RenderState&, lunasvg::Path const&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:300
    #5 0x581c181bc237 in lunasvg::StrokeData::stroke(lunasvg::RenderState&, lunasvg::Path const&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:290
    #6 0x581c181c60e3 in lunasvg::LayoutShape::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:366
    #7 0x581c181c3c70 in lunasvg::LayoutContainer::renderChildren(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:67
    #8 0x581c181c3c70 in lunasvg::LayoutSymbol::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:136
    #9 0x581c181c3c70 in lunasvg::LayoutContainer::renderChildren(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:67
    #10 0x581c181c3c70 in lunasvg::LayoutSymbol::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:136
    #11 0x581c181c3c70 in lunasvg::LayoutContainer::renderChildren(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:67
    #12 0x581c181c3c70 in lunasvg::LayoutSymbol::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:136
    #13 0x581c181c3c70 in lunasvg::LayoutContainer::renderChildren(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:67
    #14 0x581c181c3c70 in lunasvg::LayoutSymbol::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:136
    #15 0x581c181c3c70 in lunasvg::LayoutContainer::renderChildren(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:67
    #16 0x581c181c3c70 in lunasvg::LayoutSymbol::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:136
    #17 0x581c181c4688 in lunasvg::LayoutContainer::renderChildren(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:67
    #18 0x581c181c4688 in lunasvg::LayoutGroup::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:151
    #19 0x581c181c4688 in lunasvg::LayoutContainer::renderChildren(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:67
    #20 0x581c181c4688 in lunasvg::LayoutGroup::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:151
    #21 0x581c181c3c70 in lunasvg::LayoutContainer::renderChildren(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:67
    #22 0x581c181c3c70 in lunasvg::LayoutSymbol::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:136
    #23 0x581c181c4688 in lunasvg::LayoutContainer::renderChildren(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:67
    #24 0x581c181c4688 in lunasvg::LayoutGroup::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:151
    #25 0x581c181c4688 in lunasvg::LayoutContainer::renderChildren(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:67
    #26 0x581c181c4688 in lunasvg::LayoutGroup::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:151
    #27 0x581c181c3c70 in lunasvg::LayoutContainer::renderChildren(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:67
    #28 0x581c181c3c70 in lunasvg::LayoutSymbol::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:136
    #29 0x581c181c3c70 in lunasvg::LayoutContainer::renderChildren(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:67
    #30 0x581c181c3c70 in lunasvg::LayoutSymbol::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:136
    #31 0x581c18170f28 in lunasvg::Document::render(lunasvg::Bitmap, lunasvg::Matrix const&) const /home/ther/fuzz_target/lunasvg/source/lunasvg.cpp:413
    #32 0x581c181719f2 in lunasvg::Document::renderToBitmap(unsigned int, unsigned int, unsigned int) const /home/ther/fuzz_target/lunasvg/source/lunasvg.cpp:432
    #33 0x581c1814ed2b in main /home/ther/fuzz_target/lunasvg/svg2png.cpp:57
    #34 0x7ac7f0629d8f in __libc_start_call_main ../sysdeps/nptl/libc_start_call_main.h:58
    #35 0x7ac7f0629e3f in __libc_start_main_impl ../csu/libc-start.c:392
    #36 0x581c1814feb4 in _start (/home/ther/fuzz_target/lunasvg/build_asan/svg2png+0x28eb4)

AddressSanitizer can not provide additional info.
SUMMARY: AddressSanitizer: FPE (/home/ther/fuzz_target/lunasvg/build_asan/svg2png+0xd21f8) in blend_transformed_tiled_argb.isra.0
==24745==ABORTING

```

### Discover
zhangzhourui, luhui, tianzhihong, zhangyuheng, chenxingchi at Guangzhou University.

# 2.SEGV
## env
ubuntu22.04 

gcc (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0

svg2png - lunasvg(v2.3.9)

## sample
[SEGV_at_composition_solid_source](https://github.com/keepinggg/poc/blob/main/poc_of_lunasvg/SEGV_at_composition_solid_source)

## crash
```
./svg2png SEGV_at_composition_solid_source 50x50
AddressSanitizer:DEADLYSIGNAL
=================================================================
==24752==ERROR: AddressSanitizer: SEGV on unknown address 0x7e8604ad4200 (pc 0x55effc39be10 bp 0x631000032440 sp 0x7ffd1a358c58 T0)
==24752==The signal is caused by a WRITE memory access.
    #0 0x55effc39be10 in composition_solid_source (/home/ther/fuzz_target/lunasvg/build_asan/svg2png+0xd0e10)
    #1 0x55effc39d737 in plutovg_blend_color (/home/ther/fuzz_target/lunasvg/build_asan/svg2png+0xd2737)
    #2 0x55effc3976db in plutovg_fill (/home/ther/fuzz_target/lunasvg/build_asan/svg2png+0xcc6db)
    #3 0x55effc37689d in lunasvg::Canvas::fill(lunasvg::Path const&, lunasvg::Transform const&, lunasvg::WindRule, lunasvg::BlendMode, double) /home/ther/fuzz_target/lunasvg/source/canvas.cpp:100
    #4 0x55effc36a0d1 in lunasvg::FillData::fill(lunasvg::RenderState&, lunasvg::Path const&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:287
    #5 0x55effc36a0d1 in lunasvg::FillData::fill(lunasvg::RenderState&, lunasvg::Path const&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:277
    #6 0x55effc36a0d1 in lunasvg::LayoutShape::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:365
    #7 0x55effc366c10 in lunasvg::LayoutContainer::renderChildren(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:67
    #8 0x55effc366c10 in lunasvg::LayoutPattern::apply(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:226
    #9 0x55effc36a06b in lunasvg::FillData::fill(lunasvg::RenderState&, lunasvg::Path const&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:285
    #10 0x55effc36a06b in lunasvg::LayoutShape::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:365
    #11 0x55effc368688 in lunasvg::LayoutContainer::renderChildren(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:67
    #12 0x55effc368688 in lunasvg::LayoutGroup::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:151
    #13 0x55effc367c70 in lunasvg::LayoutContainer::renderChildren(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:67
    #14 0x55effc367c70 in lunasvg::LayoutSymbol::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:136
    #15 0x55effc314f28 in lunasvg::Document::render(lunasvg::Bitmap, lunasvg::Matrix const&) const /home/ther/fuzz_target/lunasvg/source/lunasvg.cpp:413
    #16 0x55effc3159f2 in lunasvg::Document::renderToBitmap(unsigned int, unsigned int, unsigned int) const /home/ther/fuzz_target/lunasvg/source/lunasvg.cpp:432
    #17 0x55effc2f2d2b in main /home/ther/fuzz_target/lunasvg/svg2png.cpp:57
    #18 0x7e8607c29d8f in __libc_start_call_main ../sysdeps/nptl/libc_start_call_main.h:58
    #19 0x7e8607c29e3f in __libc_start_main_impl ../csu/libc-start.c:392
    #20 0x55effc2f3eb4 in _start (/home/ther/fuzz_target/lunasvg/build_asan/svg2png+0x28eb4)

AddressSanitizer can not provide additional info.
SUMMARY: AddressSanitizer: SEGV (/home/ther/fuzz_target/lunasvg/build_asan/svg2png+0xd0e10) in composition_solid_source
==24752==ABORTING
```

### Discover
zhangzhourui, luhui, tianzhihong, zhangyuheng, lizhenghao at Guangzhou University.

# 3.SEGV
## env
ubuntu22.04 

gcc (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0

svg2png - lunasvg(v2.3.9)

## sample
[SEGV_at_composition_solid_source_over](https://github.com/keepinggg/poc/blob/main/poc_of_lunasvg/SEGV_at_composition_solid_source_over)

## crash
```
./svg2png SEGV_at_composition_solid_source_over 50x50
AddressSanitizer:DEADLYSIGNAL
=================================================================
==24758==ERROR: AddressSanitizer: SEGV on unknown address 0x7da6573b3e80 (pc 0x5cc9ea065df8 bp 0x7da719eaf800 sp 0x7ffc52370548 T0)
==24758==The signal is caused by a READ memory access.
    #0 0x5cc9ea065df8 in composition_solid_source_over (/home/ther/fuzz_target/lunasvg/build_asan/svg2png+0xcfdf8)
    #1 0x5cc9ea0686e6 in plutovg_blend_color (/home/ther/fuzz_target/lunasvg/build_asan/svg2png+0xd26e6)
    #2 0x5cc9ea0626db in plutovg_fill (/home/ther/fuzz_target/lunasvg/build_asan/svg2png+0xcc6db)
    #3 0x5cc9ea04189d in lunasvg::Canvas::fill(lunasvg::Path const&, lunasvg::Transform const&, lunasvg::WindRule, lunasvg::BlendMode, double) /home/ther/fuzz_target/lunasvg/source/canvas.cpp:100
    #4 0x5cc9ea0350d1 in lunasvg::FillData::fill(lunasvg::RenderState&, lunasvg::Path const&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:287
    #5 0x5cc9ea0350d1 in lunasvg::FillData::fill(lunasvg::RenderState&, lunasvg::Path const&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:277
    #6 0x5cc9ea0350d1 in lunasvg::LayoutShape::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:365
    #7 0x5cc9ea032c70 in lunasvg::LayoutContainer::renderChildren(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:67
    #8 0x5cc9ea032c70 in lunasvg::LayoutSymbol::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:136
    #9 0x5cc9ea032c70 in lunasvg::LayoutContainer::renderChildren(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:67
    #10 0x5cc9ea032c70 in lunasvg::LayoutSymbol::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:136
    #11 0x5cc9ea031c10 in lunasvg::LayoutContainer::renderChildren(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:67
    #12 0x5cc9ea031c10 in lunasvg::LayoutPattern::apply(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:226
    #13 0x5cc9ea02b166 in lunasvg::StrokeData::stroke(lunasvg::RenderState&, lunasvg::Path const&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:298
    #14 0x5cc9ea0350e3 in lunasvg::LayoutShape::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:366
    #15 0x5cc9ea033688 in lunasvg::LayoutContainer::renderChildren(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:67
    #16 0x5cc9ea033688 in lunasvg::LayoutGroup::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:151
    #17 0x5cc9ea032c70 in lunasvg::LayoutContainer::renderChildren(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:67
    #18 0x5cc9ea032c70 in lunasvg::LayoutSymbol::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:136
    #19 0x5cc9ea032c70 in lunasvg::LayoutContainer::renderChildren(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:67
    #20 0x5cc9ea032c70 in lunasvg::LayoutSymbol::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:136
    #21 0x5cc9e9fdff28 in lunasvg::Document::render(lunasvg::Bitmap, lunasvg::Matrix const&) const /home/ther/fuzz_target/lunasvg/source/lunasvg.cpp:413
    #22 0x5cc9e9fe09f2 in lunasvg::Document::renderToBitmap(unsigned int, unsigned int, unsigned int) const /home/ther/fuzz_target/lunasvg/source/lunasvg.cpp:432
    #23 0x5cc9e9fbdd2b in main /home/ther/fuzz_target/lunasvg/svg2png.cpp:57
    #24 0x7da719829d8f in __libc_start_call_main ../sysdeps/nptl/libc_start_call_main.h:58
    #25 0x7da719829e3f in __libc_start_main_impl ../csu/libc-start.c:392
    #26 0x5cc9e9fbeeb4 in _start (/home/ther/fuzz_target/lunasvg/build_asan/svg2png+0x28eb4)

AddressSanitizer can not provide additional info.
SUMMARY: AddressSanitizer: SEGV (/home/ther/fuzz_target/lunasvg/build_asan/svg2png+0xcfdf8) in composition_solid_source_over
==24758==ABORTING
```

### Discover
zhangzhourui, luhui, tianzhihong, zhangyuheng, fengjiajun at Guangzhou University.

# 4.SEGV
## env
ubuntu22.04 

gcc (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0

svg2png - lunasvg(v2.3.9)

## sample
[SEGV_at_composition_source_over](https://github.com/keepinggg/poc/blob/main/poc_of_lunasvg/SEGV_at_composition_source_over)

## crash
```
./svg2png SEGV_at_composition_source_over 50x50
AddressSanitizer:DEADLYSIGNAL
=================================================================
==24761==ERROR: AddressSanitizer: SEGV on unknown address 0x60200001027c (pc 0x57f615282a28 bp 0x603000001120 sp 0x7ffc7f610950 T0)
==24761==The signal is caused by a READ memory access.
    #0 0x57f615282a28 in composition_source_over (/home/ther/fuzz_target/lunasvg/build_asan/svg2png+0xd0a28)
    #1 0x57f615285cb9 in plutovg_blend_texture (/home/ther/fuzz_target/lunasvg/build_asan/svg2png+0xd3cb9)
    #2 0x57f61527e74a in plutovg_stroke (/home/ther/fuzz_target/lunasvg/build_asan/svg2png+0xcc74a)
    #3 0x57f61525dcc6 in lunasvg::Canvas::stroke(lunasvg::Path const&, lunasvg::Transform const&, double, lunasvg::LineCap, lunasvg::LineJoin, double, lunasvg::DashData const&, lunasvg::BlendMode, double) /home/ther/fuzz_target/lunasvg/source/canvas.cpp:116
    #4 0x57f615247237 in lunasvg::StrokeData::stroke(lunasvg::RenderState&, lunasvg::Path const&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:300
    #5 0x57f615247237 in lunasvg::StrokeData::stroke(lunasvg::RenderState&, lunasvg::Path const&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:290
    #6 0x57f6152510e3 in lunasvg::LayoutShape::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:366
    #7 0x57f61524ec70 in lunasvg::LayoutContainer::renderChildren(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:67
    #8 0x57f61524ec70 in lunasvg::LayoutSymbol::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:136
    #9 0x57f61524ec70 in lunasvg::LayoutContainer::renderChildren(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:67
    #10 0x57f61524ec70 in lunasvg::LayoutSymbol::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:136
    #11 0x57f61524ec70 in lunasvg::LayoutContainer::renderChildren(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:67
    #12 0x57f61524ec70 in lunasvg::LayoutSymbol::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:136
    #13 0x57f61524ec70 in lunasvg::LayoutContainer::renderChildren(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:67
    #14 0x57f61524ec70 in lunasvg::LayoutSymbol::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:136
    #15 0x57f61524ec70 in lunasvg::LayoutContainer::renderChildren(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:67
    #16 0x57f61524ec70 in lunasvg::LayoutSymbol::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:136
    #17 0x57f61524ec70 in lunasvg::LayoutContainer::renderChildren(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:67
    #18 0x57f61524ec70 in lunasvg::LayoutSymbol::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:136
    #19 0x57f6151fbf28 in lunasvg::Document::render(lunasvg::Bitmap, lunasvg::Matrix const&) const /home/ther/fuzz_target/lunasvg/source/lunasvg.cpp:413
    #20 0x57f6151fc9f2 in lunasvg::Document::renderToBitmap(unsigned int, unsigned int, unsigned int) const /home/ther/fuzz_target/lunasvg/source/lunasvg.cpp:432
    #21 0x57f6151d9d2b in main /home/ther/fuzz_target/lunasvg/svg2png.cpp:57
    #22 0x718d7da29d8f in __libc_start_call_main ../sysdeps/nptl/libc_start_call_main.h:58
    #23 0x718d7da29e3f in __libc_start_main_impl ../csu/libc-start.c:392
    #24 0x57f6151daeb4 in _start (/home/ther/fuzz_target/lunasvg/build_asan/svg2png+0x28eb4)

AddressSanitizer can not provide additional info.
SUMMARY: AddressSanitizer: SEGV (/home/ther/fuzz_target/lunasvg/build_asan/svg2png+0xd0a28) in composition_source_over
==24761==ABORTING
```

### Discover
zhangzhourui, luhui, tianzhihong, zhangyuheng, chenxingchi at Guangzhou University.

# 5.stack-buffer-underflow
## env
ubuntu22.04 

gcc (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0

svg2png - lunasvg(v2.3.9)

## sample
[stack-buffer-underflow_at_layoutcontext.svg](https://github.com/keepinggg/poc/blob/main/poc_of_lunasvg/stack-buffer-underflo_at_layoutcontext.svg)

## crash
```
./svg2png stack-buffer-underflow_at_layoutcontext.svg 50x50
=================================================================
==24776==ERROR: AddressSanitizer: stack-buffer-underflow on address 0x7ffcd53d1510 at pc 0x70f7c4439c23 bp 0x7ffcd53cddf0 sp 0x7ffcd53cd598
WRITE of size 3511724192 at 0x7ffcd53d1510 thread T0
    #0 0x70f7c4439c22 in __interceptor_memset ../../../../src/libsanitizer/sanitizer_common/sanitizer_common_interceptors.inc:799
    #1 0x5936340f3396 in gray_convert_glyph.constprop.0 (/home/ther/fuzz_target/lunasvg/build_asan/svg2png+0xd7396)
    #2 0x5936340f3785 in PVG_FT_Raster_Render (/home/ther/fuzz_target/lunasvg/build_asan/svg2png+0xd7785)
    #3 0x5936340f092f in plutovg_rle_rasterize (/home/ther/fuzz_target/lunasvg/build_asan/svg2png+0xd492f)
    #4 0x5936340e88d6 in plutovg_paint (/home/ther/fuzz_target/lunasvg/build_asan/svg2png+0xcc8d6)
    #5 0x5936340b8cf3 in lunasvg::LayoutSymbol::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:137
    #6 0x5936340b7c10 in lunasvg::LayoutContainer::renderChildren(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:67
    #7 0x5936340b7c10 in lunasvg::LayoutPattern::apply(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:226
    #8 0x5936340b1166 in lunasvg::StrokeData::stroke(lunasvg::RenderState&, lunasvg::Path const&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:298
    #9 0x5936340bb0e3 in lunasvg::LayoutShape::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:366
    #10 0x5936340b8c70 in lunasvg::LayoutContainer::renderChildren(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:67
    #11 0x5936340b8c70 in lunasvg::LayoutSymbol::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:136
    #12 0x5936340b8c70 in lunasvg::LayoutContainer::renderChildren(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:67
    #13 0x5936340b8c70 in lunasvg::LayoutSymbol::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:136
    #14 0x5936340b8c70 in lunasvg::LayoutContainer::renderChildren(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:67
    #15 0x5936340b8c70 in lunasvg::LayoutSymbol::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:136
    #16 0x5936340b8c70 in lunasvg::LayoutContainer::renderChildren(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:67
    #17 0x5936340b8c70 in lunasvg::LayoutSymbol::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:136
    #18 0x593634065f28 in lunasvg::Document::render(lunasvg::Bitmap, lunasvg::Matrix const&) const /home/ther/fuzz_target/lunasvg/source/lunasvg.cpp:413
    #19 0x5936340669f2 in lunasvg::Document::renderToBitmap(unsigned int, unsigned int, unsigned int) const /home/ther/fuzz_target/lunasvg/source/lunasvg.cpp:432
    #20 0x593634043d2b in main /home/ther/fuzz_target/lunasvg/svg2png.cpp:57
    #21 0x70f7c3c29d8f in __libc_start_call_main ../sysdeps/nptl/libc_start_call_main.h:58
    #22 0x70f7c3c29e3f in __libc_start_main_impl ../csu/libc-start.c:392
    #23 0x593634044eb4 in _start (/home/ther/fuzz_target/lunasvg/build_asan/svg2png+0x28eb4)

Address 0x7ffcd53d1510 is located in stack of thread T0 at offset 0 in frame
    #0 0x5936340b86df in lunasvg::LayoutSymbol::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:131

  This frame has 6 object(s):
    [48, 56) '__for_begin' (line 66) <== Memory access at offset 0 partially underflows this variable
    [80, 88) '__for_end' (line 66) <== Memory access at offset 0 partially underflows this variable
    [112, 120) '<unknown>' <== Memory access at offset 0 partially underflows this variable
    [144, 152) '<unknown>' <== Memory access at offset 0 partially underflows this variable
    [176, 232) 'info' (line 132) <== Memory access at offset 0 partially underflows this variable
    [272, 352) 'newState' (line 133) <== Memory access at offset 0 partially underflows this variable
HINT: this may be a false positive if your program uses some custom stack unwind mechanism, swapcontext or vfork
      (longjmp and C++ exceptions *are* supported)
SUMMARY: AddressSanitizer: stack-buffer-underflow ../../../../src/libsanitizer/sanitizer_common/sanitizer_common_interceptors.inc:799 in __interceptor_memset
Shadow bytes around the buggy address:
  0x10001aa72250: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x10001aa72260: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x10001aa72270: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x10001aa72280: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x10001aa72290: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
=>0x10001aa722a0: 00 00[f1]f1 f1 f1 f1 f1 f8 f2 f2 f2 f8 f2 f2 f2
  0x10001aa722b0: f8 f2 f2 f2 f8 f2 f2 f2 00 00 00 00 00 00 00 f2
  0x10001aa722c0: f2 f2 f2 f2 00 00 00 00 00 00 00 00 00 00 f3 f3
  0x10001aa722d0: f3 f3 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x10001aa722e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x10001aa722f0: 00 00 f1 f1 f1 f1 00 f2 f2 f2 00 f2 f2 f2 f8 f2
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
==24776==ABORTING
```

### Discover
zhangzhourui, luhui, tianzhihong, chenxingchi, lizhenghao, fengjiajun at Guangzhou University.

# 6.stack-overflow
## env
ubuntu22.04 

gcc (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0

svg2png - lunasvg(v2.3.9)

## sample
[stack-overflow_at_element.svg](https://github.com/keepinggg/poc/blob/main/poc_of_lunasvg/stack-overflow_at_element.svg)

## crash
```
./svg2png stack-overflow_at_element.svg 50x50
AddressSanitizer:DEADLYSIGNAL
=================================================================
==24813==ERROR: AddressSanitizer: stack-overflow on address 0x7ffe65a38e08 (pc 0x7d7d9acb6156 bp 0x7ffe65a39640 sp 0x7ffe65a38df0 T0)
    #0 0x7d7d9acb6156 in __sanitizer::StackTrace::StackTrace(unsigned long const*, unsigned int) ../../../../src/libsanitizer/sanitizer_common/sanitizer_stacktrace.h:52
    #1 0x7d7d9acb6156 in __sanitizer::BufferedStackTrace::BufferedStackTrace() ../../../../src/libsanitizer/sanitizer_common/sanitizer_stacktrace.h:105
    #2 0x7d7d9acb6156 in operator new(unsigned long) ../../../../src/libsanitizer/asan/asan_new_delete.cpp:99
    #3 0x6459e2a77b49 in std::unique_ptr<lunasvg::PatternElement, std::default_delete<lunasvg::PatternElement> > lunasvg::makeUnique<lunasvg::PatternElement>() /home/ther/fuzz_target/lunasvg/source/element.h:126
    #4 0x6459e2a77b49 in lunasvg::Element::create(lunasvg::ElementID) /home/ther/fuzz_target/lunasvg/source/element.cpp:64
    #5 0x6459e2a77f68 in lunasvg::Element::clone() const /home/ther/fuzz_target/lunasvg/source/element.cpp:226
    #6 0x6459e2a78b81 in lunasvg::Element::clone() const /home/ther/fuzz_target/lunasvg/source/element.cpp:229
    #7 0x6459e2a78b81 in lunasvg::Element::clone() const /home/ther/fuzz_target/lunasvg/source/element.cpp:229
    #8 0x6459e2a78b81 in lunasvg::Element::clone() const /home/ther/fuzz_target/lunasvg/source/element.cpp:229
    #9 0x6459e2a78b81 in lunasvg::Element::clone() const /home/ther/fuzz_target/lunasvg/source/element.cpp:229
    #10 0x6459e2a78b81 in lunasvg::Element::clone() const /home/ther/fuzz_target/lunasvg/source/element.cpp:229
    #11 0x6459e2a78b81 in lunasvg::Element::clone() const /home/ther/fuzz_target/lunasvg/source/element.cpp:229
    #12 0x6459e2a78b81 in lunasvg::Element::clone() const /home/ther/fuzz_target/lunasvg/source/element.cpp:229
    #13 0x6459e2af5aa0 in lunasvg::UseElement::cloneTargetElement(lunasvg::Element const*) const /home/ther/fuzz_target/lunasvg/source/useelement.cpp:111
    #14 0x6459e2af643e in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:119
    #15 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #16 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #17 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #18 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #19 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #20 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #21 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #22 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #23 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #24 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #25 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #26 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #27 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #28 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #29 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #30 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #31 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #32 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #33 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #34 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #35 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #36 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #37 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #38 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #39 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #40 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #41 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #42 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #43 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #44 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #45 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #46 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #47 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #48 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #49 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #50 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #51 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #52 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #53 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #54 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #55 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #56 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #57 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #58 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #59 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #60 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #61 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #62 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #63 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #64 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #65 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #66 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #67 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #68 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #69 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #70 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #71 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #72 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #73 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #74 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #75 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #76 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #77 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #78 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #79 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #80 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #81 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #82 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #83 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #84 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #85 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #86 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #87 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #88 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #89 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #90 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #91 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #92 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #93 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #94 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #95 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #96 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #97 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #98 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #99 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #100 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #101 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #102 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #103 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #104 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #105 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #106 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #107 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #108 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #109 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #110 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #111 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #112 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #113 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #114 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #115 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #116 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #117 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #118 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #119 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #120 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #121 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #122 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #123 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #124 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #125 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #126 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #127 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #128 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #129 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #130 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #131 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #132 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #133 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #134 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #135 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #136 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #137 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #138 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #139 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #140 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #141 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #142 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #143 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #144 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #145 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #146 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #147 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #148 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #149 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #150 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #151 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #152 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #153 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #154 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #155 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #156 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #157 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #158 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #159 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #160 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #161 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #162 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #163 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #164 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #165 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #166 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #167 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #168 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #169 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #170 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #171 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #172 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #173 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #174 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #175 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #176 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #177 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #178 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #179 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #180 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #181 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #182 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #183 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #184 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #185 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #186 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #187 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #188 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #189 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #190 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #191 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #192 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #193 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #194 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #195 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #196 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #197 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #198 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #199 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #200 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #201 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #202 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #203 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #204 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #205 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #206 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #207 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #208 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #209 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #210 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #211 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #212 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #213 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #214 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #215 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #216 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #217 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #218 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #219 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #220 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #221 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #222 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #223 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #224 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #225 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #226 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #227 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #228 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #229 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #230 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #231 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #232 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #233 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #234 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #235 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #236 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #237 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #238 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #239 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #240 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #241 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #242 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #243 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #244 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #245 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #246 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #247 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #248 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124
    #249 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #250 0x6459e2a76bcf in lunasvg::Element::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/element.cpp:220
    #251 0x6459e2af656f in lunasvg::UseElement::build(lunasvg::Document const*) /home/ther/fuzz_target/lunasvg/source/useelement.cpp:124

SUMMARY: AddressSanitizer: stack-overflow ../../../../src/libsanitizer/sanitizer_common/sanitizer_stacktrace.h:52 in __sanitizer::StackTrace::StackTrace(unsigned long const*, unsigned int)
==24813==ABORTING
```

### Discover
zhangzhourui, luhui, tianzhihong, zhangyuheng, chenxingchi at Guangzhou University.

# 7.stack-use-after-scope
## env
ubuntu22.04 

gcc (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0

svg2png - lunasvg(v2.3.9)

## sample
[stack-use-after-scope_at_layoutcontext.svg](https://github.com/keepinggg/poc/blob/main/poc_of_lunasvg/stack-use-after-scope_at_layoutcontext.svg)

## crash
```
./svg2png stack-use-after-scope_at_layoutcontext.svg 50x50
=================================================================
==24822==ERROR: AddressSanitizer: stack-use-after-scope on address 0x7ffce9a396e0 at pc 0x70dc2a839c23 bp 0x7ffce9a35f90 sp 0x7ffce9a35738
WRITE of size 2770357504 at 0x7ffce9a396e0 thread T0
    #0 0x70dc2a839c22 in __interceptor_memset ../../../../src/libsanitizer/sanitizer_common/sanitizer_common_interceptors.inc:799
    #1 0x5ee8e659f396 in gray_convert_glyph.constprop.0 (/home/ther/fuzz_target/lunasvg/build_asan/svg2png+0xd7396)
    #2 0x5ee8e659f785 in PVG_FT_Raster_Render (/home/ther/fuzz_target/lunasvg/build_asan/svg2png+0xd7785)
    #3 0x5ee8e659c92f in plutovg_rle_rasterize (/home/ther/fuzz_target/lunasvg/build_asan/svg2png+0xd492f)
    #4 0x5ee8e65948d6 in plutovg_paint (/home/ther/fuzz_target/lunasvg/build_asan/svg2png+0xcc8d6)
    #5 0x5ee8e6564cf3 in lunasvg::LayoutSymbol::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:137
    #6 0x5ee8e6563c10 in lunasvg::LayoutContainer::renderChildren(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:67
    #7 0x5ee8e6563c10 in lunasvg::LayoutPattern::apply(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:226
    #8 0x5ee8e655d166 in lunasvg::StrokeData::stroke(lunasvg::RenderState&, lunasvg::Path const&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:298
    #9 0x5ee8e65670e3 in lunasvg::LayoutShape::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:366
    #10 0x5ee8e6564c70 in lunasvg::LayoutContainer::renderChildren(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:67
    #11 0x5ee8e6564c70 in lunasvg::LayoutSymbol::render(lunasvg::RenderState&) const /home/ther/fuzz_target/lunasvg/source/layoutcontext.cpp:136
    #12 0x5ee8e6511f28 in lunasvg::Document::render(lunasvg::Bitmap, lunasvg::Matrix const&) const /home/ther/fuzz_target/lunasvg/source/lunasvg.cpp:413
    #13 0x5ee8e65129f2 in lunasvg::Document::renderToBitmap(unsigned int, unsigned int, unsigned int) const /home/ther/fuzz_target/lunasvg/source/lunasvg.cpp:432
    #14 0x5ee8e64efd2b in main /home/ther/fuzz_target/lunasvg/svg2png.cpp:57
    #15 0x70dc2a029d8f in __libc_start_call_main ../sysdeps/nptl/libc_start_call_main.h:58
    #16 0x70dc2a029e3f in __libc_start_main_impl ../csu/libc-start.c:392
    #17 0x5ee8e64f0eb4 in _start (/home/ther/fuzz_target/lunasvg/build_asan/svg2png+0x28eb4)

Address 0x7ffce9a396e0 is located in stack of thread T0
SUMMARY: AddressSanitizer: stack-use-after-scope ../../../../src/libsanitizer/sanitizer_common/sanitizer_common_interceptors.inc:799 in __interceptor_memset
Shadow bytes around the buggy address:
  0x10001d33f280: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x10001d33f290: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x10001d33f2a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x10001d33f2b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x10001d33f2c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
=>0x10001d33f2d0: 00 00 00 00 00 00 00 00 00 00 00 00[f8]00 00 00
  0x10001d33f2e0: f8 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x10001d33f2f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x10001d33f300: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x10001d33f310: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x10001d33f320: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
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
==24822==ABORTING
```

### Discover
zhangzhourui, luhui, tianzhihong, zhangyuheng, lizhenghao at Guangzhou University.

# 8.SEGV
## env
ubuntu22.04 

gcc (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0

svg2png - lunasvg(v2.3.9)

## sample
[SEGV_at_gray_record_cell](https://github.com/keepinggg/poc/blob/main/poc_of_lunasvg/SEGV_at_gray_record_cell)

## crash
```
./svg2png SEGV_at_gray_record_cell 50x50
AddressSanitizer:DEADLYSIGNAL
=================================================================
==11969==ERROR: AddressSanitizer: SEGV on unknown address 0xfffffffff808719d (pc 0x5615a308e66d bp 0xffffffffffffffff sp 0x7ffe1fae31b8 T0)
==11969==The signal is caused by a WRITE memory access.
    #0 0x5615a308e66d in gray_record_cell (/home/ther/fuzz/fuzz_target/lunasvg/build_asan/svg2png+0xd566d)
    #1 0x5615a308e9e8 in gray_render_scanline (/home/ther/fuzz/fuzz_target/lunasvg/build_asan/svg2png+0xd59e8)
    #2 0x5615a308ecb3 in gray_render_line (/home/ther/fuzz/fuzz_target/lunasvg/build_asan/svg2png+0xd5cb3)
    #3 0x5615a308f6e1 in gray_render_cubic.isra.0 (/home/ther/fuzz/fuzz_target/lunasvg/build_asan/svg2png+0xd66e1)

AddressSanitizer can not provide additional info.
SUMMARY: AddressSanitizer: SEGV (/home/ther/fuzz/fuzz_target/lunasvg/build_asan/svg2png+0xd566d) in gray_record_cell
==11969==ABORTING

```

### Discover
zhangzhourui, luhui, tianzhihong, zhangyuheng at Guangzhou University.

# 9.SEGV
## env
ubuntu22.04 

gcc (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0

svg2png - lunasvg(v2.3.9)

## sample
[stack-overflow_at_gray_convert_glyph](https://github.com/keepinggg/poc/blob/main/poc_of_lunasvg/stack-overflow_at_gray_convert_glyph)

## crash
```
./svg2png stack-overflow_at_gray_convert_glyph 50x50
AddressSanitizer:DEADLYSIGNAL
=================================================================
==12302==ERROR: AddressSanitizer: stack-overflow on address 0x7ffc947ae000 (pc 0x7f4eb04f2a3a bp 0x7ffc947a8330 sp 0x7ffc947a8018 T0)
    #0 0x7f4eb04f2a3a  (/lib/x86_64-linux-gnu/libc.so.6+0x1afa3a)
    #1 0x5628c9325396 in gray_convert_glyph.constprop.0 (/home/ther/fuzz/fuzz_target/lunasvg/build_asan/svg2png+0xd7396)
    #2 0x5628c9325785 in PVG_FT_Raster_Render (/home/ther/fuzz/fuzz_target/lunasvg/build_asan/svg2png+0xd7785)

SUMMARY: AddressSanitizer: stack-overflow (/lib/x86_64-linux-gnu/libc.so.6+0x1afa3a)
==12302==ABORTING

```

### Discover
zhangzhourui, luhui, tianzhihong, zhangyuheng at Guangzhou University.
