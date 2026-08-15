---
title: "HDR Experience in Ubuntu 26.04 with NVIDIA RTX 2080 over HDMI 2.0b"
date: 2026-08-15 23:15:00 +0800
categories: [Tech Analysis, Linux]
tags: [Ubuntu, HDR, NVIDIA, RTX 2080, HDMI, OLED]
pin: false
math: false
toc: true
published: true
image:
  path: assets/2026-08-15-hdr-experience-in-ubuntu/display_settings_cropped.png
---

Quick notes on running HDR10 on Ubuntu 26.04 LTS using KDE Plasma 6 (Wayland) and NVIDIA GeForce RTX 2080.

## Hardware & Setup

- **OS / Desktop**: Ubuntu 26.04 LTS with KDE Plasma 6 (KWin Wayland)
- **GPU**: NVIDIA GeForce RTX 2080 (Turing)
- **Display / TV**: Samsung S95F 65" QD-OLED TV
  - On Windows and macOS, I normally use it at `4K 120Hz 4:4:4 10-bit with HDR on`
  - The TV supports up to 165 Hz (I haven't tested the bit depth and chroma sampling at this mode)

> **Cable Matters Adapter Issue (Windows vs. Linux):**
> - On **Windows**, a `Cable Matters USB-C (DP 1.4 Alt Mode) to HDMI 2.1 adapter (Model 201428)` drives `4K 120Hz 4:4:4 10-bit HDR`.
> - On **Linux**, this adapter fails to expose HDR (the HDR toggle does not appear in KDE display settings).
> - **Workaround**: Connected directly via native **RTX 2080 HDMI 2.0b port** to the TV for HDR to be recognized.
{: .prompt-warning }

## Display Configuration

![Ubuntu HDR Display Settings](assets/2026-08-15-hdr-experience-in-ubuntu/display_settings_cropped.png)
_KDE Plasma Display Configuration panel._

- **HDMI Bandwidth**: 18.0 Gbps (HDMI 2.0b max limit)
- **4K 60Hz 4:4:4 10-bit**: Exceeds HDMI 2.0b bandwidth limit (~20.05 Gbps required); requires chroma subsampling (4:2:2/4:2:0) or 8-bit dithered color

> **TODO:** Test if 10b and 444 chroma sampling are working
{: .prompt-info }
