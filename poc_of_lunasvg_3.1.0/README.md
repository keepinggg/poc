# 1.SEGV
## env
ubuntu22.04 

gcc (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0

svg2png - lunasvg(v3.0.0)

## sample
[SEGV-plutovg_blend](https://github.com/keepinggg/poc/blob/main/poc_of_lunasvg_3.1.0/SEGV-plutovg_blend)

## crash
```
./svg2png SEGV-plutovg_blend 50x50
AddressSanitizer:DEADLYSIGNAL
=================================================================
==1474894==ERROR: AddressSanitizer: SEGV on unknown address 0x000000000008 (pc 0x55b272552a1d bp 0x000000000000 sp 0x7ffc00a317d0 T0)
==1474894==The signal is caused by a READ memory access.
==1474894==Hint: address points to the zero page.
    #0 0x55b272552a1d in plutovg_blend (/home/ther/fuzz/fuzz_target/lunasvg-master/build_asan/examples/svg2png+0x121a1d)
    #1 0x55b27246515e in lunasvg::Canvas::blendCanvas(lunasvg::Canvas const&, lunasvg::BlendMode, float) /home/ther/fuzz/fuzz_target/lunasvg-master/source/graphics.cpp:679
    #2 0x55b27248aef4 in lunasvg::SVGUseElement::render(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:709
    #3 0x55b2724728e9 in lunasvg::SVGElement::renderChildren(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:453
    #4 0x55b27248b67e in lunasvg::SVGGElement::render(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:868
    #5 0x55b2724728e9 in lunasvg::SVGElement::renderChildren(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:453
    #6 0x55b2724b416b in lunasvg::SVGPatternElement::applyPaint(lunasvg::SVGRenderState&, float) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgpaintelement.cpp:302
    #7 0x55b272473b3d in lunasvg::SVGPaintServer::applyPaint(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:529
    #8 0x55b27249abe2 in lunasvg::SVGGeometryElement::render(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svggeometryelement.cpp:150
    #9 0x55b2724728e9 in lunasvg::SVGElement::renderChildren(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:453
    #10 0x55b27248b67e in lunasvg::SVGGElement::render(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:868
    #11 0x55b2724728e9 in lunasvg::SVGElement::renderChildren(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:453
    #12 0x55b27248a128 in lunasvg::SVGSVGElement::render(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:612
    #13 0x55b2724728e9 in lunasvg::SVGElement::renderChildren(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:453
    #14 0x55b27248b67e in lunasvg::SVGGElement::render(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:868
    #15 0x55b2724728e9 in lunasvg::SVGElement::renderChildren(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:453
    #16 0x55b27248a128 in lunasvg::SVGSVGElement::render(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:612
    #17 0x55b2724728e9 in lunasvg::SVGElement::renderChildren(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:453
    #18 0x55b27248b67e in lunasvg::SVGGElement::render(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:868
    #19 0x55b2724728e9 in lunasvg::SVGElement::renderChildren(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:453
    #20 0x55b27248b67e in lunasvg::SVGGElement::render(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:868
    #21 0x55b2724728e9 in lunasvg::SVGElement::renderChildren(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:453
    #22 0x55b27248b67e in lunasvg::SVGGElement::render(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:868
    #23 0x55b2724728e9 in lunasvg::SVGElement::renderChildren(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:453
    #24 0x55b27248a128 in lunasvg::SVGSVGElement::render(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:612
    #25 0x55b2724554e7 in lunasvg::Document::render(lunasvg::Bitmap&, lunasvg::Matrix const&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/lunasvg.cpp:475
    #26 0x55b2724560f1 in lunasvg::Document::renderToBitmap(int, int, unsigned int) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/lunasvg.cpp:497
    #27 0x55b2724441cf in main /home/ther/fuzz/fuzz_target/lunasvg-master/examples/svg2png.cpp:55
    #28 0x7f8c52c17d8f in __libc_start_call_main ../sysdeps/nptl/libc_start_call_main.h:58
    #29 0x7f8c52c17e3f in __libc_start_main_impl ../csu/libc-start.c:392
    #30 0x55b272444d24 in _start (/home/ther/fuzz/fuzz_target/lunasvg-master/build_asan/examples/svg2png+0x13d24)

AddressSanitizer can not provide additional info.
SUMMARY: AddressSanitizer: SEGV (/home/ther/fuzz/fuzz_target/lunasvg-master/build_asan/examples/svg2png+0x121a1d) in plutovg_blend
==1474894==ABORTING
```

## Discover
zhangzhourui, luhui, tianzhihong at Guangzhou University.

# 2.allocation-size-too-big
## env
ubuntu22.04 

gcc (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0

svg2png - lunasvg(v3.0.0)

## sample
[allocation-size-too-big-plutovg_surface_create](https://github.com/keepinggg/poc/blob/main/poc_of_lunasvg_3.1.0/allocation-size-too-big-plutovg_surface_create)

## crash
```
./svg2png allocation-size-too-big-plutovg_surface_create 50x50
=================================================================
==1512010==ERROR: AddressSanitizer: requested allocation size 0xfffffffffaf08018 (0xfffffffffaf09018 after adjustments for alignment, red zones etc.) exceeds maximum supported size of 0x10000000000 (thread T0)
    #0 0x7fa82cf1d887 in __interceptor_malloc ../../../../src/libsanitizer/asan/asan_malloc_linux.cpp:145
    #1 0x55e92284e64d in plutovg_surface_create (/home/ther/fuzz/fuzz_target/lunasvg-3.0.0/build_asan/examples/svg2png+0x11164d)

==1512010==HINT: if you don't care about these errors you may set allocator_may_return_null=1
SUMMARY: AddressSanitizer: allocation-size-too-big ../../../../src/libsanitizer/asan/asan_malloc_linux.cpp:145 in __interceptor_malloc
==1512010==ABORTING
```

## Discover
zhangzhourui, luhui, tianzhihong at Guangzhou University.

# 3.SEGV
## env
ubuntu22.04 

gcc (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0

svg2png - lunasvg(v3.0.0)

## sample
[SEGV-composition_source_over](https://github.com/keepinggg/poc/blob/main/poc_of_lunasvg_3.1.0/SEGV-composition_source_over)

## crash
```
./svg2png SEGV-composition_source_over 50x50
AddressSanitizer:DEADLYSIGNAL
=================================================================
==1525136==ERROR: AddressSanitizer: SEGV on unknown address 0x603000013e30 (pc 0x5620d673d0c8 bp 0x00000000001f sp 0x7ffc4a4df6b0 T0)
==1525136==The signal is caused by a READ memory access.
    #0 0x5620d673d0c8 in composition_source_over (/home/ther/fuzz/fuzz_target/lunasvg-3.0.0/build_asan/examples/svg2png+0x1190c8)
    #1 0x5620d6745cd8 in plutovg_blend (/home/ther/fuzz/fuzz_target/lunasvg-3.0.0/build_asan/examples/svg2png+0x121cd8)
    #2 0x5620d6703c92 in plutovg_canvas_stroke_path (/home/ther/fuzz/fuzz_target/lunasvg-3.0.0/build_asan/examples/svg2png+0xdfc92)
    #3 0x5620d668e090 in lunasvg::SVGGeometryElement::render(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svggeometryelement.cpp:153
    #4 0x5620d66658e9 in lunasvg::SVGElement::renderChildren(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:453
    #5 0x5620d667e67e in lunasvg::SVGGElement::render(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:868
    #6 0x5620d66658e9 in lunasvg::SVGElement::renderChildren(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:453
    #7 0x5620d667d128 in lunasvg::SVGSVGElement::render(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:612
    #8 0x5620d66658e9 in lunasvg::SVGElement::renderChildren(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:453
    #9 0x5620d667d128 in lunasvg::SVGSVGElement::render(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:612
    #10 0x5620d66484e7 in lunasvg::Document::render(lunasvg::Bitmap&, lunasvg::Matrix const&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/lunasvg.cpp:475
    #11 0x5620d66490f1 in lunasvg::Document::renderToBitmap(int, int, unsigned int) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/lunasvg.cpp:497
    #12 0x5620d66371cf in main /home/ther/fuzz/fuzz_target/lunasvg-master/examples/svg2png.cpp:55
    #13 0x7f9996c10d8f in __libc_start_call_main ../sysdeps/nptl/libc_start_call_main.h:58
    #14 0x7f9996c10e3f in __libc_start_main_impl ../csu/libc-start.c:392
    #15 0x5620d6637d24 in _start (/home/ther/fuzz/fuzz_target/lunasvg-3.0.0/build_asan/examples/svg2png+0x13d24)

AddressSanitizer can not provide additional info.
SUMMARY: AddressSanitizer: SEGV (/home/ther/fuzz/fuzz_target/lunasvg-3.0.0/build_asan/examples/svg2png+0x1190c8) in composition_source_over
==1525136==ABORTING
```

## Discover
zhangzhourui, luhui, tianzhihong at Guangzhou University.

# 4.SEGV
## env
ubuntu22.04 

gcc (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0

svg2png - lunasvg(v3.0.0)

## sample
[SEGV-plutovg_path_add_path](https://github.com/keepinggg/poc/blob/main/poc_of_lunasvg_3.1.0/SEGV-plutovg_path_add_path)

## crash
```
./svg2png SEGV-plutovg_path_add_path 50x50
AddressSanitizer:DEADLYSIGNAL
=================================================================
==1548431==ERROR: AddressSanitizer: SEGV on unknown address 0x000000000020 (pc 0x55de61d796df bp 0x000000000000 sp 0x7fffc0c21a70 T0)
==1548431==The signal is caused by a READ memory access.
==1548431==Hint: address points to the zero page.
    #0 0x55de61d796df in plutovg_path_add_path (/home/ther/fuzz/fuzz_target/lunasvg-3.0.0/build_asan/examples/svg2png+0xeb6df)
    #1 0x55de61d6ddc4 in plutovg_canvas_clip_path (/home/ther/fuzz/fuzz_target/lunasvg-3.0.0/build_asan/examples/svg2png+0xdfdc4)
    #2 0x55de61cda3df in lunasvg::SVGClipPathElement::applyClipPath(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:1030
    #3 0x55de61d5c7f4 in lunasvg::SVGRenderState::beginGroup(lunasvg::SVGBlendInfo const&) /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgrenderstate.cpp:40
    #4 0x55de61ce70ea in lunasvg::SVGSVGElement::render(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:609
    #5 0x55de61cb24e7 in lunasvg::Document::render(lunasvg::Bitmap&, lunasvg::Matrix const&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/lunasvg.cpp:475
    #6 0x55de61cb30f1 in lunasvg::Document::renderToBitmap(int, int, unsigned int) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/lunasvg.cpp:497
    #7 0x55de61ca11cf in main /home/ther/fuzz/fuzz_target/lunasvg-master/examples/svg2png.cpp:55
    #8 0x7f80144e4d8f in __libc_start_call_main ../sysdeps/nptl/libc_start_call_main.h:58
    #9 0x7f80144e4e3f in __libc_start_main_impl ../csu/libc-start.c:392
    #10 0x55de61ca1d24 in _start (/home/ther/fuzz/fuzz_target/lunasvg-3.0.0/build_asan/examples/svg2png+0x13d24)

AddressSanitizer can not provide additional info.
SUMMARY: AddressSanitizer: SEGV (/home/ther/fuzz/fuzz_target/lunasvg-3.0.0/build_asan/examples/svg2png+0xeb6df) in plutovg_path_add_path
==1548431==ABORTING
```

## Discover
zhangzhourui, luhui, tianzhihong at Guangzhou University.

# 5.SEGV
## env
ubuntu22.04 

gcc (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0

svg2png - lunasvg(v3.0.0)

## sample
[SEGV-gray_record_cell](https://github.com/keepinggg/poc/blob/main/poc_of_lunasvg_3.1.0/SEGV-gray_record_cell)

## crash
```
./svg2png SEGV-gray_record_cell 50x50
AddressSanitizer:DEADLYSIGNAL
=================================================================
==1549737==ERROR: AddressSanitizer: SEGV on unknown address (pc 0x5556970ea8f8 bp 0x000000000000 sp 0x7ffcc2078d28 T0)
==1549737==The signal is caused by a READ memory access.
==1549737==Hint: this fault was caused by a dereference of a high value address (see register values below).  Dissassemble the provided pc to learn which register was used.
    #0 0x5556970ea8f8 in gray_record_cell (/home/ther/fuzz/fuzz_target/lunasvg-3.0.0/build_asan/examples/svg2png+0x1128f8)
    #1 0x5556970eb71f in gray_render_line (/home/ther/fuzz/fuzz_target/lunasvg-3.0.0/build_asan/examples/svg2png+0x11371f)
    #2 0x5556970ec0d1 in gray_convert_glyph_inner.constprop.0 (/home/ther/fuzz/fuzz_target/lunasvg-3.0.0/build_asan/examples/svg2png+0x1140d1)
    #3 0x5556970ec6ab in gray_convert_glyph.constprop.0 (/home/ther/fuzz/fuzz_target/lunasvg-3.0.0/build_asan/examples/svg2png+0x1146ab)
    #4 0x5556970ecb6a in PVG_FT_Raster_Render (/home/ther/fuzz/fuzz_target/lunasvg-3.0.0/build_asan/examples/svg2png+0x114b6a)
    #5 0x5556970c87be in plutovg_rasterize (/home/ther/fuzz/fuzz_target/lunasvg-3.0.0/build_asan/examples/svg2png+0xf07be)
    #6 0x5556970b7d3e in plutovg_canvas_clip_rect (/home/ther/fuzz/fuzz_target/lunasvg-3.0.0/build_asan/examples/svg2png+0xdfd3e)
    #7 0x5556970315fa in lunasvg::SVGSVGElement::render(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:611
    #8 0x5556970198e9 in lunasvg::SVGElement::renderChildren(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:453
    #9 0x555697031ee7 in lunasvg::SVGUseElement::render(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:708
    #10 0x5556970198e9 in lunasvg::SVGElement::renderChildren(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:453
    #11 0x55569703267e in lunasvg::SVGGElement::render(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:868
    #12 0x5556970198e9 in lunasvg::SVGElement::renderChildren(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:453
    #13 0x555697031ee7 in lunasvg::SVGUseElement::render(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:708
    #14 0x5556970198e9 in lunasvg::SVGElement::renderChildren(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:453
    #15 0x555697031128 in lunasvg::SVGSVGElement::render(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:612
    #16 0x5556970198e9 in lunasvg::SVGElement::renderChildren(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:453
    #17 0x555697031128 in lunasvg::SVGSVGElement::render(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:612
    #18 0x555696ffc4e7 in lunasvg::Document::render(lunasvg::Bitmap&, lunasvg::Matrix const&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/lunasvg.cpp:475
    #19 0x555696ffd0f1 in lunasvg::Document::renderToBitmap(int, int, unsigned int) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/lunasvg.cpp:497
    #20 0x555696feb1cf in main /home/ther/fuzz/fuzz_target/lunasvg-master/examples/svg2png.cpp:55
    #21 0x7f050cf31d8f in __libc_start_call_main ../sysdeps/nptl/libc_start_call_main.h:58
    #22 0x7f050cf31e3f in __libc_start_main_impl ../csu/libc-start.c:392
    #23 0x555696febd24 in _start (/home/ther/fuzz/fuzz_target/lunasvg-3.0.0/build_asan/examples/svg2png+0x13d24)

AddressSanitizer can not provide additional info.
SUMMARY: AddressSanitizer: SEGV (/home/ther/fuzz/fuzz_target/lunasvg-3.0.0/build_asan/examples/svg2png+0x1128f8) in gray_record_cell
==1549737==ABORTING
```

## Discover
zhangzhourui, luhui, tianzhihong at Guangzhou University.

# 6.SEGV
## env
ubuntu22.04 

gcc (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0

svg2png - lunasvg(v3.0.0)

## sample
[SEGV-blend_transformed_tiled_argb.isra.0](https://github.com/keepinggg/poc/blob/main/poc_of_lunasvg_3.1.0/SEGV-blend_transformed_tiled_argb.isra.0)

## crash
```
./svg2png SEGV-blend_transformed_tiled_argb.isra.0 50x50
AddressSanitizer:DEADLYSIGNAL
=================================================================
==1550229==ERROR: AddressSanitizer: SEGV on unknown address 0x602fff9c0348 (pc 0x55f4607cd9a9 bp 0x6030000002c8 sp 0x7fffb8f9c5e0 T0)
==1550229==The signal is caused by a READ memory access.
    #0 0x55f4607cd9a9 in blend_transformed_tiled_argb.isra.0 (/home/ther/fuzz/fuzz_target/lunasvg-3.0.0/build_asan/examples/svg2png+0x11a9a9)
    #1 0x55f4607d4bcd in plutovg_blend (/home/ther/fuzz/fuzz_target/lunasvg-3.0.0/build_asan/examples/svg2png+0x121bcd)
    #2 0x55f460792b4a in plutovg_canvas_fill_path (/home/ther/fuzz/fuzz_target/lunasvg-3.0.0/build_asan/examples/svg2png+0xdfb4a)
    #3 0x55f46071cc38 in lunasvg::SVGGeometryElement::render(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svggeometryelement.cpp:151
    #4 0x55f4606f48e9 in lunasvg::SVGElement::renderChildren(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:453
    #5 0x55f46070c128 in lunasvg::SVGSVGElement::render(lunasvg::SVGRenderState&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/svgelement.cpp:612
    #6 0x55f4606d74e7 in lunasvg::Document::render(lunasvg::Bitmap&, lunasvg::Matrix const&) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/lunasvg.cpp:475
    #7 0x55f4606d80f1 in lunasvg::Document::renderToBitmap(int, int, unsigned int) const /home/ther/fuzz/fuzz_target/lunasvg-master/source/lunasvg.cpp:497
    #8 0x55f4606c61cf in main /home/ther/fuzz/fuzz_target/lunasvg-master/examples/svg2png.cpp:55
    #9 0x7feefc943d8f in __libc_start_call_main ../sysdeps/nptl/libc_start_call_main.h:58
    #10 0x7feefc943e3f in __libc_start_main_impl ../csu/libc-start.c:392
    #11 0x55f4606c6d24 in _start (/home/ther/fuzz/fuzz_target/lunasvg-3.0.0/build_asan/examples/svg2png+0x13d24)

AddressSanitizer can not provide additional info.
SUMMARY: AddressSanitizer: SEGV (/home/ther/fuzz/fuzz_target/lunasvg-3.0.0/build_asan/examples/svg2png+0x11a9a9) in blend_transformed_tiled_argb.isra.0
==1550229==ABORTING
```

## Discover
zhangzhourui, luhui, tianzhihong at Guangzhou University.
