# Vulkan Video, graphics, and systems tooling for V

I build low-level libraries and applications in the
[V programming language](https://vlang.io), with a focus on reproducible
bindings, graphics, and hardware-accelerated H.264 playback through Vulkan
Video.

## Vulkan Video stack

| Layer | Project | Purpose |
| --- | --- | --- |
| Application | [`v_vulkan_video`](https://github.com/antono2/v_vulkan_video) | Hardware-accelerated H.264/MP4 player |
| Video formats | [`h264`](https://github.com/antono2/h264) · [`minimp4`](https://github.com/antono2/minimp4) | Bitstream parsing and MP4 container access |
| UI and windowing | [`imgui`](https://github.com/antono2/imgui) · [`glfw`](https://github.com/antono2/glfw) | Dear ImGui/ImPlot and focused GLFW bindings |
| Resource management | [`vulkan_memory_allocator`](https://github.com/antono2/vulkan_memory_allocator) | Explicit Vulkan buffer and image allocations |
| Vulkan API | [`vulkan`](https://github.com/antono2/vulkan) | Generated Vulkan and Vulkan Video bindings |
| Generation | [`v_vulkan_bindings`](https://github.com/antono2/v_vulkan_bindings) | Reproducible bindings generated from Khronos `vk.xml` |

The repositories form an end-to-end path from Khronos registry data and C
interfaces to a native V application. CI exercises software-only parsing,
binding generation, native library builds, and cross-platform compilation.

## OpenCL

- [`opencl`](https://github.com/antono2/opencl) provides generated OpenCL
  1.0–3.0 bindings, including external-memory and semaphore interoperability.
- [`v_opencl_bindings`](https://github.com/antono2/v_opencl_bindings) contains
  the generator, validation pipeline, and advanced Vulkan interoperability
  example.

## Examples and utilities

- [`v_imgui_examples`](https://github.com/antono2/v_imgui_examples) — tested
  GLFW/Vulkan Dear ImGui example.
- [`v_find_duplicates`](https://github.com/antono2/v_find_duplicates) — fast
  duplicate file and directory finder.
- [`vlang.kak`](https://github.com/antono2/vlang.kak) — V language support for
  the Kakoune editor.

## Current build health

[![Vulkan bindings](https://github.com/antono2/vulkan/actions/workflows/generated-bindings-ci.yml/badge.svg)](https://github.com/antono2/vulkan/actions)
[![Vulkan generator](https://github.com/antono2/v_vulkan_bindings/actions/workflows/update_bindings_and_push_to_vulkan.yml/badge.svg)](https://github.com/antono2/v_vulkan_bindings/actions)
[![Vulkan Video](https://github.com/antono2/v_vulkan_video/actions/workflows/release-ci.yml/badge.svg)](https://github.com/antono2/v_vulkan_video/actions)
[![ImGui](https://github.com/antono2/imgui/actions/workflows/demo-release.yml/badge.svg)](https://github.com/antono2/imgui/actions)
[![OpenCL](https://github.com/antono2/opencl/actions/workflows/test.yml/badge.svg)](https://github.com/antono2/opencl/actions)

Each project README documents its supported scope, native dependencies, and
the shortest path to a working build.
