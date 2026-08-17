---
title: "Memory bandwidth comparison across devices"
date: 2026-08-14 23:55:00 +0800
categories: [Tech Analysis]
tags: [Memory, Hardware, Benchmarks, Apple Silicon, GPU]
published: true
---

A comparison of theoretical peak memory bandwidth, bus widths, and memory standards across mobile SoCs, laptop workstations, desktop PCs, and discrete laptop GPUs:

| Device /<br>Processor | Peak<br>bandwidth | Memory bus<br>width | Memory<br>standard |
| :--- | :--- | :--- | :--- |
| **iPhone 14 Pro**<br>(A16 Bionic) | 51.2 GB/s | 64-bit<br>(4 × 16-bit) | LPDDR5-6400<br>(6,400 MT/s) |
| **iPhone 15 Pro**<br>(A17 Pro) | 51.2 GB/s | 64-bit<br>(4 × 16-bit) | LPDDR5-6400<br>(6,400 MT/s) |
| **iPhone 16 Pro**<br>(A18 Pro) | 60.0 GB/s | 64-bit<br>(4 × 16-bit) | LPDDR5X-7500<br>(7,500 MT/s) |
| **Dell Precision 7680**<br>(13th Gen Intel) | 89.6 GB/s | 128-bit<br>(Dual-channel) | DDR5-5600 |
| **Desktop PC**<br>(Dual-channel DDR5) | 102.4 GB/s | 128-bit<br>(Dual-channel) | DDR5-6400<br>(6,400 MT/s) |
| **MacBook Pro**<br>(M1 Pro) | 200.0 GB/s | 256-bit<br>(4 × 64-bit) | LPDDR5-6400<br>(6,400 MT/s) |
| **RTX 4060**<br>(Laptop GPU) | 256.0 GB/s | 128-bit<br>(4 × 32-bit) | GDDR6<br>(16 Gbps) |

*Note: The RTX 4060 Laptop GPU comes configured with **8 GB** of dedicated GDDR6 VRAM.*

## Key observations

* **Smartphone SoCs:** Moving from LPDDR5-6400 to LPDDR5X-7500 on the A18 Pro brings memory bandwidth to 60.0 GB/s without widening the 64-bit bus.
* **Desktop DDR5:** Standard dual-channel DDR5-6400 on a desktop platform achieves 102.4 GB/s of memory bandwidth across its 128-bit bus.
* **Apple Silicon unified memory:** The M1 Pro achieves 200 GB/s by employing a wide 256-bit bus, feeding both CPU and GPU from a shared high-bandwidth pool.
* **Discrete GPUs vs. host RAM:** While standard dual-channel DDR5 delivers ~76–102 GB/s, discrete GPUs like the RTX 4060 utilize high-speed GDDR6 to reach 256 GB/s over a 128-bit bus.
