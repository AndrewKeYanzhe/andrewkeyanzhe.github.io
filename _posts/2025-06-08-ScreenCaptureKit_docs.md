---
title: Apple ScreenCaptureKit Documentation  
date: 2025-06-08 22:03:00 +0100  
categories: [Tech Analysis]  
tags: [HDR, ScreenCaptureKit, macOS, Apple]  
pin: true  
math: true  
toc: false
published: false
---

This post is a work in progress

This post explores how Apple’s ScreenCaptureKit handles HDR screen recording. If you notice any errors or have suggestions, feel free to [open an issue](https://github.com/AndrewKeYanzhe/andrewkeyanzhe.github.io/issues) on this website’s GitHub repository.

**TL;DR**
- Use `captureHDRStreamCanonicalDisplay` for recordings without tonemapping.
- Use Lightroom to accurately view HDR screenshots.


---

### SCStreamConfiguration Preset Options  
[SCStreamConfiguration.Preset – Apple Developer](https://developer.apple.com/documentation/screencapturekit/scstreamconfiguration/preset)

#### Option 1: `captureHDRStreamCanonicalDisplay`
- No tonemapping is applied by ScreenCaptureKit.
- However, if an application performs its own tonemapping, that will appear in the recording. 

**Application tonemapping/clipping behaviour when showing HDR content:**
  - **Chrome** displays PQ HDR AVIF with tonemapping to the panel's HDR peak brightness (e.g., 200 nits on MacBook Air, which has an EDR ratio of 2).
  - **Lightroom** shows PQ HDR AVIF without tonemapping—it applies the PQ EOTF directly but **clips at the panel's peak brightness**. Screen recordings will show highlight details above panel peak as clipped.
  - 
  - I developed a Metal-based app using EDR rendering with tonemapping set to none ([Apple documentation: Perform your own tone mapping](https://developer.apple.com/documentation/metal/performing-your-own-tone-mapping)). Screen recordings from this app preserve full highlight detail without clipping.

#### Option 2: `captureHDRStreamLocalDisplay`
- Tonemapping is applied by ScreenCaptureKit.
- On a MacBook Air with an EDR ratio of 2.0 (200 nits), the recording is tone-mapped to 200 nits.
  - Within an HDR recording, SDR white (255) appears as 238 (PQ HDR PNG screenshot displayed in Lightroom and checked with Digital Color Meter)

---

### Application behaviour when displaying HDR screenshots (M1 MacBook Air)

- **Preview.app (macos Sequoia)**
  - Does not utilize EDR on the M1 Macbook Air when displaying HDR images.
    - Verified via macOS Console logs: `Display 1 setting display headroom hint to 1` (should be 2 for HDR content).
  - Displays PQ HDR PNGs with noticeably reduced exposure in the SDR range.
    - For an HDR screenshot, SDR white (255) appears as 188 (checked using Digital Color Meter).

- **Chrome**
  - Displays PQ HDR PNGs with tonemapping, and the SDR range shows slightly reduced exposure.
    - Within an HDR screenshot, SDR white (255) appears as 221.

- **Lightroom**
  - Displays PQ HDR PNGs without any tonemapping.
  - For an HDR screenshot, SDR white (255) remains 255.
  - Best option for accurate HDR screenshot viewing. This should match the original image displayed by the hardware display


Best way to test hdr local vs canonical:
Record screen recording of my hdr app (which does 0 tonemap or clipping)
use mac split screen. left is my app. right is white image (useful for checking screenshot exposure in davinci waveform)
then playback screen recording on macbook pro 16 reference mode To avoid tone mapping during playback.
Can also use davinci resolve to doublecheck. since canonical is 2.03x the brightness, we can match exposures in davinci and compare

**so. verified using davinci: canonical records at sdr = 203 nits**
**sck local records at sdr = sdr nits of the physical display**
e.g. if macbook is set as sdr equal to 300 nits, then the recording will contain sdr = 300 nits. This is verified using Apple console `commit brightness sdr`, and davinci resolve to check the screenshots

Recommendations
 - Record death stranding video: setting mac physical display sdr = 203 nits looks good. 
    - so, can use either local display or canonical
 - Record desktop video: set mac to 100 nits (either reference mode, or turn off auto brightness). record using sck local display.
    - however, the screenshot will look dark in chrome, lightroom etc since they interpret encoded 203 nits = EDR 1.0. TODO, maybe boost png screenshot brightness


sck local does not apply more tonemapping

exposure matched in davinci using nodes 
1. forward ootf
2. exposure
3. inverse ootf

tldr: just use sck with canonical tonemap. and then for the video, scale exposure by 1/2.03



with exposures matched, The wave form of the two images look very similar and HDR local doesn't seem to introduce additional clipping or highlight rolloff



note: with mbp reference mode, **quicktime** seems to show 100 nits pq as always 100 nits. so, if sdr is set to 203, pq displayed values are not scaled together