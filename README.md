# Open-source GPU tooling for V: Vulkan Video and OpenCL

I build low-level libraries and applications in the
[V programming language](https://vlang.io). The projects span reproducible
Khronos API generation, opt-in typed ownership helpers, hardware-accelerated
H.264 playback, and OpenCL/Vulkan interoperability.

## Vulkan Video stack

| Layer | Project | Purpose |
| --- | --- | --- |
| Application | [`v_vulkan_video`](https://github.com/antono2/v_vulkan_video) | Hardware-accelerated H.264/MP4 playback and Vulkan presentation |
| Video formats | [`h264`](https://github.com/antono2/h264) · [`minimp4`](https://github.com/antono2/minimp4) | Bitstream parsing, picture ordering, and MP4 container access |
| UI and windowing | [`imgui`](https://github.com/antono2/imgui) · [`glfw`](https://github.com/antono2/glfw) | Dear ImGui/ImPlot and focused GLFW bindings |
| Resource management | [`vulkan_memory_allocator`](https://github.com/antono2/vulkan_memory_allocator) | Explicit Vulkan buffer and image allocations |
| Vulkan API | [`vulkan`](https://github.com/antono2/vulkan) | Generated Vulkan and Vulkan Video bindings with an opt-in ergonomic API |
| Generation | [`v_vulkan_bindings`](https://github.com/antono2/v_vulkan_bindings) | Reproducible generation from Khronos `vk.xml` |

The `vulkan` module keeps the complete generated API accessible while adding
opt-in typed lifecycle, device, queue, memory, buffer, and command-pool helpers.
See its releases and compatibility notes for the current registry and compiler
matrix.

## OpenCL stack

| Layer | Project | Purpose |
| --- | --- | --- |
| Module | [`opencl`](https://github.com/antono2/opencl) | Generated OpenCL 1.0–3.0 API plus typed buffers, images, SVM, events, and kernels |
| Generation | [`v_opencl_bindings`](https://github.com/antono2/v_opencl_bindings) | Registry-driven generator, validation pipeline, and canonical source |
| Interop example | [`opencl/examples/vulkan_particles`](https://github.com/antono2/opencl/tree/master/examples/vulkan_particles) | OpenCL compute with Vulkan presentation, shared memory, and semaphore synchronization |

The Vulkan particle example uses zero-copy external-memory interoperability on
UUID-matched devices when the required extensions are available, with a
portable host-staged fallback.

## Reusable memory building blocks

[`memory`](https://github.com/antono2/memory) provides checked object and slot
pools, plus range, linear, ring, and buddy allocators for V. Its general-purpose
core does not depend on Vulkan; optional examples show how the allocators can
support GPU suballocation.

## Examples and build health

- [`v_imgui_examples`](https://github.com/antono2/v_imgui_examples) — tested
  GLFW/Vulkan Dear ImGui example.

[![Vulkan bindings](https://github.com/antono2/vulkan/actions/workflows/generated-bindings-ci.yml/badge.svg)](https://github.com/antono2/vulkan/actions)
[![Vulkan generator](https://github.com/antono2/v_vulkan_bindings/actions/workflows/update_bindings_and_push_to_vulkan.yml/badge.svg)](https://github.com/antono2/v_vulkan_bindings/actions)
[![Vulkan Video](https://github.com/antono2/v_vulkan_video/actions/workflows/release-ci.yml/badge.svg)](https://github.com/antono2/v_vulkan_video/actions)
[![ImGui](https://github.com/antono2/imgui/actions/workflows/demo-release.yml/badge.svg)](https://github.com/antono2/imgui/actions)
[![OpenCL](https://github.com/antono2/opencl/actions/workflows/test.yml/badge.svg)](https://github.com/antono2/opencl/actions)

Each project README documents its supported scope, native dependencies, and
the shortest path to a working build.

## Support the work

The software and its documentation remain freely available. If you would like
to support continued work on bindings, portable builds, examples, and
documentation, visit [oreskin.de/support](https://oreskin.de/dono_en.php).
