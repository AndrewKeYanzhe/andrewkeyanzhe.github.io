---
title: "HDR video exposure normalisation behavior across platforms"
date: 2026-07-28 15:37:00 +0800
categories: [Tech Analysis]
tags: [Display Compositor, HDR, Chrome, Windows]
published: true
image:
  path: assets/2026-07-28-hdr-video-exposure-normalisation-behavior-across-platforms/Still 2026-07-29 081521_1.1.1 padded 40x21.png
---

<u>This post is a work in progress. </u>




### Website with PQ and HLG HDR video test charts

[https://andrewkeyanzhe.github.io/100_203_nits_PQ_HLG_patterns/4_compare.html](https://andrewkeyanzhe.github.io/100_203_nits_PQ_HLG_patterns/4_compare.html)

### Behaviour of Chrome on Windows

These settings are used:
- HDR is `enabled` in Windows settings
- The Windows `OS SDR brightness` is set to `100 nits` (5% on the slider)

> The following screenshot will show the correct nits when viewed on a device with SDR brightness set to 100 nits
- on Windows, set SDR brightness to 5%
- on MacBooks, set the brightness setting to in between 7 and 8 clicks from the bottom (out of 16)
{: .prompt-tip }

- We can see that for Chrome on Windows, PQ HDR videos are displayed without normalising to `OS SDR brightness in nits`, so video pixels' nit values sent to the display matches that encoded in the video
- However, HLG HDR videos are normalised to `OS SDR brightness in nits`, using a factor of `OS SDR brightness in nits/203`. So the 100 nit HLG pattern is shown at around 49 nits. **⚠️ This does not match the pixel nits as encoded in the HLG video, when one assumes the 1000 nit HLG transfer function** (commonly used by reference displays and DaVinci Resolve) 


![img-description](assets/2026-07-28-hdr-video-exposure-normalisation-behavior-across-platforms/Still 2026-07-29 081521_1.1.1 cropped.png){: width="600" style="box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15); border-radius: 6px;"}
_Comparison of PQ and HLG video test pattern rendering in Chrome on Windows_{: style="font-size: 1rem;"}