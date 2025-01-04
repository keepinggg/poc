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
zhangzhourui, luhui, tianzhihong, zhangyuheng, chenxingchi at Guangzhou University.****
