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
| **iPhone 17 Pro**<br>(A19 Pro) | 76.8 GB/s | 64-bit<br>(4 × 16-bit) | LPDDR5X-9600<br>(9,600 MT/s) |
| **Huawei Pura 70 Pro+**<br>(Kirin 9010) | 51.2 GB/s | 64-bit<br>(4 × 16-bit) | LPDDR5-6400<br>(6,400 MT/s) |
| **Dell Precision 7680**<br>(13th Gen Intel) | 89.6 GB/s | 128-bit<br>(Dual-channel) | DDR5-5600 |
| **Desktop PC**<br>(Dual-channel DDR5) | 102.4 GB/s | 128-bit<br>(Dual-channel) | DDR5-6400<br>(6,400 MT/s) |
| **MacBook Pro**<br>(M1 Pro) | 200.0 GB/s | 256-bit<br>(4 × 64-bit) | LPDDR5-6400<br>(6,400 MT/s) |
| **RTX 3500 Ada**<br>(Laptop GPU) | 432.0 GB/s | 192-bit<br>(6 × 32-bit) | GDDR6 |
| **GeForce RTX 3090** | 936.0 GB/s | 384-bit<br>(12 × 32-bit) | GDDR6X-19500<br>(19.5 Gb/s) |
| **GeForce RTX 4090** | 1,008.0 GB/s | 384-bit<br>(12 × 32-bit) | GDDR6X-21000<br>(21 Gb/s) |
| **GeForce RTX 5090** | 1,792.0 GB/s | 512-bit<br>(16 × 32-bit) | GDDR7-28000<br>(28 Gb/s) |

*Note: The NVIDIA RTX 3500 Ada Laptop GPU typically comes configured with **12 GB** of GDDR6 VRAM.*  
*Note: The Huawei Pura 70 Pro+ memory bandwidth figure (51.2 GB/s) is referenced from Wikipedia's HiSilicon processor database (calculated from 3,200 MHz / LPDDR5-6400 over a 64-bit bus). However, Wikipedia does not currently include a direct citation for this specific metric, and web searches have not yet yielded an authoritative primary source.*
*Note: NVIDIA specifies the RTX 3090 with 24 GB GDDR6X over a 384-bit interface; its 19.5 Gb/s effective memory rate gives 936 GB/s. The RTX 4090 uses 24 GB GDDR6X on the same 384-bit interface at 21 Gb/s, giving 1,008 GB/s. The RTX 5090 uses 32 GB GDDR7 on a 512-bit interface at 28 Gb/s, giving 1,792 GB/s. These are theoretical peak device-memory bandwidths: `(bus width ÷ 8) × effective data rate`.*

## Key observations

* **Smartphone SoCs:** Moving from LPDDR5-6400 (51.2 GB/s on A16/A17 Pro) to LPDDR5X-7500 (60.0 GB/s on A18 Pro) and LPDDR5X-9600 (76.8 GB/s on A19 Pro) steadily increases mobile memory bandwidth without widening the 64-bit bus. The Kirin 9010 on the Huawei Pura 70 Pro+ maintains 51.2 GB/s over a standard 64-bit quad-channel LPDDR5-6400 bus.
* **Desktop DDR5:** Standard dual-channel DDR5-6400 on a desktop platform achieves 102.4 GB/s of memory bandwidth across its 128-bit bus.
* **Apple Silicon unified memory:** The M1 Pro achieves 200 GB/s by employing a wide 256-bit bus, feeding both CPU and GPU from a shared high-bandwidth pool.
* **Discrete GPUs vs. host RAM:** While standard dual-channel DDR5 delivers ~76–102 GB/s, discrete GPUs use much wider, faster GDDR memory: 432 GB/s on the RTX 3500 Ada Laptop GPU, 936 GB/s on the RTX 3090, 1,008 GB/s on the RTX 4090, and 1,792 GB/s on the RTX 5090.
