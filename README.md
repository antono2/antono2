# Games, GPU software, and developer tools in V

I'm Anton Oreskin, a software engineer and open-source maintainer. I build
applications and their reusable foundations in the
[V programming language](https://vlang.io): games, hardware-accelerated video,
GPU interoperability, memory tools, and a development environment for Kakoune.

## Torus Trooper

[`torus_trooper`](https://github.com/antono2/torus_trooper) is now public: a free
tunnel-racing arcade shooter inspired by Kenta Cho's original, with its own
spacecraft, courses, and Vulkan presentation for Windows and Linux.

- Normal, Hard, and Extreme difficulty, high scores, and unlockable starting levels.
- Customizable keyboard and controller input, graphics settings, and audio levels.
- A replay library with custom names, sorting, and `.ttr` import/export.

[Download for Windows or Linux](https://github.com/antono2/torus_trooper/releases/latest).
A Vulkan-capable graphics driver is required; the Linux package needs glibc 2.38
or newer (for example Ubuntu 24.04). macOS is not officially supported.

Explore the [gameplay preview and controls](https://github.com/antono2/torus_trooper#gameplay-preview),
[source-build instructions](https://github.com/antono2/torus_trooper/blob/main/docs/technical-reference.md#desktop-build-requirements),
and [design guide](https://github.com/antono2/torus_trooper/blob/main/docs/learning-path.md).

## V development in Kakoune

[`vlang.kak`](https://github.com/antono2/vlang.kak) combines VLS/kak-lsp language
features with project navigation, diagnostics, testing, and local GDB debugging.
Managed setup and updates preserve personal settings. The README includes a
recorded IDE walkthrough and documents Linux setup, recovery, and limitations.

## Vulkan Video stack

| Layer | Project | Purpose |
| --- | --- | --- |
| Application | [`v_vulkan_video`](https://github.com/antono2/v_vulkan_video) | Hardware-accelerated H.264/MP4 playback and Vulkan presentation |
| Video formats | [`h264`](https://github.com/antono2/h264) · [`minimp4`](https://github.com/antono2/minimp4) | Bitstream syntax, parameter metadata, and MP4 container access |
| UI and windowing | [`imgui`](https://github.com/antono2/imgui) · [`glfw`](https://github.com/antono2/glfw) | Dear ImGui/ImPlot and focused GLFW bindings |
| Resource management | [`vulkan_memory_allocator`](https://github.com/antono2/vulkan_memory_allocator) (`vkmemalloc`) | V-native, budget-aware memory placement, block suballocation, upload rings, and diagnostics |
| Vulkan API | [`vulkan`](https://github.com/antono2/vulkan) | Generated Vulkan and Vulkan Video bindings with an opt-in ergonomic API |
| Generation | [`v_vulkan_bindings`](https://github.com/antono2/v_vulkan_bindings) | Reproducible generation from Khronos `vk.xml` |

The `vulkan` module keeps the complete generated API accessible while adding
opt-in typed lifecycle, device, queue, memory, buffer, and command-pool helpers.
See its releases and compatibility notes for the current registry and compiler
matrix.

The video player's [Linux prerelease](https://github.com/antono2/v_vulkan_video/releases/tag/v0.3.0-rc1)
adds current-stack integration, H.264 correctness fixes, and hardware decode
comparisons against FFmpeg. It requires a driver with Vulkan Video H.264 decode;
Windows hardware playback remains unverified. See each project's platform notes
rather than assuming every application supports every CI target.

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
core does not depend on Vulkan; synchronized range and buddy variants support
shared allocation metadata. The V-native Vulkan allocator uses this core for
GPU block suballocation; it is not a binding to AMD's Vulkan Memory Allocator.

## Examples and build health

- [`v_imgui_examples`](https://github.com/antono2/v_imgui_examples) — tested
  GLFW/Vulkan demo, widget gallery, ImPlot dashboard and Android examples.

[![Vulkan bindings](https://github.com/antono2/vulkan/actions/workflows/generated-bindings-ci.yml/badge.svg)](https://github.com/antono2/vulkan/actions)
[![Vulkan generator](https://github.com/antono2/v_vulkan_bindings/actions/workflows/update_bindings_and_push_to_vulkan.yml/badge.svg)](https://github.com/antono2/v_vulkan_bindings/actions)
[![Vulkan Video](https://github.com/antono2/v_vulkan_video/actions/workflows/release-ci.yml/badge.svg)](https://github.com/antono2/v_vulkan_video/actions)
[![ImGui](https://github.com/antono2/imgui/actions/workflows/demo-release.yml/badge.svg)](https://github.com/antono2/imgui/actions)
[![OpenCL](https://github.com/antono2/opencl/actions/workflows/test.yml/badge.svg)](https://github.com/antono2/opencl/actions)

Each project README documents its supported scope, native dependencies, and
the shortest path to a working build.

## Support the work

The software and its documentation remain freely available. If you would like
to support continued work on the game, developer tools, bindings, tests, and
documentation, visit [oreskin.de/support](https://oreskin.de/dono_en.php).

## Choosing a starting point

| Goal | Start here | Role |
| --- | --- | --- |
| Play a game | [Torus Trooper](https://github.com/antono2/torus_trooper) | Application with release downloads |
| Study hardware video decoding | [Vulkan Video player](https://github.com/antono2/v_vulkan_video) | Application and implementation guide |
| Build a graphical UI | [ImGui](https://github.com/antono2/imgui) and [examples](https://github.com/antono2/v_imgui_examples) | Library plus gallery, dashboard and platform examples |
| Use graphics or compute APIs | [Vulkan](https://github.com/antono2/vulkan) or [OpenCL](https://github.com/antono2/opencl) | Published modules for applications |
| Update generated API declarations | [Vulkan generator](https://github.com/antono2/v_vulkan_bindings) or [OpenCL generator](https://github.com/antono2/v_opencl_bindings) | Maintainer tools; regenerate before publishing |

Start with each project's README for its supported platforms and setup path.
Generated bindings expose an API surface; the installed driver still determines
which GPU features are available at runtime.
