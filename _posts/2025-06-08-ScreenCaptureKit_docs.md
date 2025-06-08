---
title: Apple ScreenCaptureKit Documentation  
date: 2025-06-08 22:03:00 +0100  
categories: [Tech Analysis]  
tags: [HDR, ScreenCaptureKit, Apple]  
pin: true  
math: true  
toc: false

---

This post is a work in progress. If you notice any errors or have suggestions, feel free to contact me on LinkedIn.

---

### SCStreamConfiguration Preset Options  
[SCStreamConfiguration.Preset – Apple Developer](https://developer.apple.com/documentation/screencapturekit/scstreamconfiguration/preset)

#### Option 1: `captureHDRStreamCanonicalDisplay`
- No tonemapping is applied during screen recording.
- However, if an application performs its own tonemapping, that will appear in the recording. For example:
  - **Chrome** displays PQ HDR AVIF with tonemapping to the panel's HDR peak brightness (e.g., 200 nits on MacBook Air, which has an EDR ratio of 2).
  - **Lightroom** shows PQ HDR AVIF without tonemapping—it applies the PQ EOTF directly but clips at the panel's peak brightness. Screen recordings will show highlight details above panel peak as clipped.
  - I developed a Metal-based app using EDR rendering with tonemapping set to none ([Apple documentation: Perform your own tone mapping](https://developer.apple.com/documentation/metal/performing-your-own-tone-mapping)). Screen recordings from this app preserve full highlight detail.

#### Option 2: `captureHDRStreamLocalDisplay`
- This preset applies tonemapping in the screen recording.
- On a MacBook Air with an EDR ratio of 2.0 (200 nits), the recording is tone-mapped to 200 nits.

---

### Additional Observations (M1 MacBook Air)

- **Preview.app**
  - Does not utilize EDR when displaying HDR images.
  - Verified via macOS Console logs: `Display 1 setting display headroom hint to 1` (should be 2 for HDR content).
  - Displays PQ HDR PNGs with noticeably reduced exposure in the SDR range.
    - For an HDR screen recording, SDR white (255) appears as 188 (checked using Digital Color Meter).

- **Chrome**
  - Displays PQ HDR PNGs with tonemapping, and the SDR range shows slightly reduced exposure.
    - Within an HDR recording, SDR white (255) appears as 221.

- **Lightroom**
  - Displays PQ HDR PNGs without any tonemapping.
  - For an HDR  screen recording, SDR white (255) remains 255.
  - Best option for accurate HDR screenshot viewing. This should match the original image displayed by the hardware display
