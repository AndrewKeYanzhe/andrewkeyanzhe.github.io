---
title: Davinci Resolve for Windows shows HDR content 20% too dark
date: 2026-03-29 01:30:00 +0800  
categories: [Tech Analysis]  
tags: [DaVinci Resolve, HDR]  
pin: false  
math: true  
toc: false
published: true
---

Davinci Resolve 20.3.1 for Windows shows HDR content that is 20% too dark. As a result, there is a mismatch in luminance between the HDR viewer in Resolve, and the exported video (which has the correct luminance.)

I suspect it is because Davinci Resolve scales PQ HDR values using 100 nits = 1.0, while [Windows DWM displays 1.0 as 80 nits in HDR](https://learn.microsoft.com/en-us/windows/win32/direct3darticles/high-dynamic-range#system-composition-using-a-high-bit-depth-canonical-color-space-1).

This was verified by generating a 100 nit PQ BT2020 test pattern in Davinci Resolve, using Color Space Transform: clip at 100 nits. The exported test pattern is available at [here](https://drive.google.com/drive/u/0/folders/1iqx9VpY8ciYglu35SklKOdoVovZW_P2V).

The 100 nit test pattern was played side by side in MPV video player and Davinci Resolve. We can see that the 100 nits pattern looks darker in Davinci Resolve.

![img-description](assets/2026-03-29-Davinci_Resolve_Windows_HDR_too_dark/mpv_resolve_side_by_side.jpg)

OBS was then used to record the screen in HDR (PQ BT2020), and the screen recording was imported back into Davinci Resolve. The screen recording was zoomed in so we can see the luminance of the white pattern using the scopes.

![img-description](assets/2026-03-29-Davinci_Resolve_Windows_HDR_too_dark/video_zoomed.png)

In Resolve's ST2084 HDR scopes, we can see that the 100 nit test pattern played in MPV (on the left) renders at 100 nits, while the test pattern in Resolve (on the right) renders at 80 nits.

![img-description](assets/2026-03-29-Davinci_Resolve_Windows_HDR_too_dark/scopes, left-mpv at 100 nits, right-resolve at 80 nits.png)