---
title: iPhone HEIC vs ProRaw vs bayer raw
# description: Examples of text, typography, math equations, diagrams, flowcharts, pictures, videos, and more.
# author: Andrew Ke
# Daylight savings should use GMT+1
date: 2025-04-14 18:03:00 +0100
# categories: [Blogging, Demo]
# tags: [typography]
pin: true
math: true
# mermaid: true

# media_subpath: posts/2019-08-08-text-and-typography/
# media_subpath: 

---

<!-- https://github.com/cotes2020/jekyll-theme-chirpy/blob/master/_posts/2019-08-08-text-and-typography.md -->

HDR images best viewed on an HDR capable device + browser. Recommended setup: Macbook Pro 16 with XDR display + Google Chrome.

All images are captured on the iPhone 14 Pro Max's ultra wide angle camera.

<!-- {: .d-flex .justify-content-center }
![heif](assets/2025-04-14-iPhone_ProRaw_vs_bayer/IMG_5587.AVIF){: .normal .mw-33 .me-2}
![proRaw](assets/2025-04-14-iPhone_ProRaw_vs_bayer/IMG_5586.AVIF){: .normal .mw-33 .me-2}
![bayer_raw](assets/2025-04-14-iPhone_ProRaw_vs_bayer/IMG_5585.AVIF){: .normal .mw-33}

{: .d-flex .justify-content-center }
_abc_

<p>
<img
  src="https://assets.digitalocean.com/articles/alligator/css/object-fit/example-object-fit.jpg"
  width="600"
  height="337"
  style="width: 300px; height: 337px; object-fit: cover; object-position: 100% 0;"

/>
</p> -->



<div class="d-flex justify-content-center">
  <img src="assets/2025-04-14-iPhone_ProRaw_vs_bayer/IMG_5587.AVIF"
       style="width: 300px; height: 337px; object-fit: none; object-position: 80% 48%; margin-right: 0.5rem;"
       alt="HEIF format image">
  <img src="assets/2025-04-14-iPhone_ProRaw_vs_bayer/IMG_5586.AVIF"
       style="width: 300px; height: 337px; object-fit: none; object-position: 79% 44%; margin-right: 0.5rem;"
       alt="ProRAW format image">
  <img src="assets/2025-04-14-iPhone_ProRaw_vs_bayer/IMG_5585.AVIF"
       style="width: 300px; height: 337px; object-fit: none; object-position: 80% 45%;"
       alt="Bayer RAW format image">
</div>

<!-- mt2 adds a bit of spacing before element -->
<!-- <div class="d-flex justify-content-center mt-2" style="gap: 0.5rem;"> -->
<div class="d-flex justify-content-center" style="gap: 0.5rem;" style="margin-bottom: 1rem;">
  <div style="width: 300px; text-align: center;">1. HEIF</div>
  <div style="width: 300px; text-align: center;">2. ProRAW with 0 sharpening</div>
  <div style="width: 300px; text-align: center;">3. AVIF from Bayer RAW</div>
</div>


<div class="d-flex justify-content-center">
  <img src="assets/2025-04-14-iPhone_ProRaw_vs_bayer/IMG_5587.AVIF"
       style="width: 300px; height: 337px; object-fit: none; object-position: 88% 58%; margin-right: 0.5rem;"
       alt="HEIF format image">
  <img src="assets/2025-04-14-iPhone_ProRaw_vs_bayer/IMG_5586.AVIF"
       style="width: 300px; height: 337px; object-fit: none; object-position: 87% 54%; margin-right: 0.5rem;"
       alt="ProRAW format image">
  <img src="assets/2025-04-14-iPhone_ProRaw_vs_bayer/IMG_5585.AVIF"
       style="width: 300px; height: 337px; object-fit: none; object-position: 88% 55%;"
       alt="Bayer RAW format image">
</div>

<!-- mt2 adds a bit of spacing before element -->
<!-- <div class="d-flex justify-content-center mt-2" style="gap: 0.5rem;"> -->
<div class="d-flex justify-content-center" style="gap: 0.5rem;">
  <div style="width: 300px; text-align: center;">1. HEIF</div>
  <div style="width: 300px; text-align: center;">2. ProRAW with 0 sharpening</div>
  <div style="width: 300px; text-align: center;">3. AVIF from Bayer RAW</div>
</div>

#### **1. HEIF image captured by the stock camera app**
The HEIF image is converted into HDR AVIF by Lightroom (Chrome doesn't support HEIF). The converted image looks identical to the original HEIF when viewed in the iPhone Photos app.
![heif](assets/2025-04-14-iPhone_ProRaw_vs_bayer/IMG_5587.AVIF)
_abc_

#### **2. ProRaw image captured by the stock camera app**
The ProRaw image is converted into HDR AVIF by Lightroom with sharpening set to 0. 
![proRaw](assets/2025-04-14-iPhone_ProRaw_vs_bayer/IMG_5586.AVIF)

#### **3. Bayer raw image converted to HDR AVIF**
The bayer raw image is captured by the No Fusion-Powerful Pro Cam app and converted to HDR AVIF by Lightroom using the Adobe neutral profile. Sharpening and noise reduction are set to 0.
![bayer_raw](assets/2025-04-14-iPhone_ProRaw_vs_bayer/IMG_5585.AVIF)


#### **4. SDR HEIF converted from bayer raw (No Fusion app)**
This is the HEIF image captured by the No Fusion-Powerful Pro Cam app, using the bayer raw as source (HEIF+ option). Sharpening is set to 0, but we can observe some noise reduction being applied. The HEIF file is converted to JPG for viewing in Chrome.
![bayer_heif](assets/2025-04-14-iPhone_ProRaw_vs_bayer/IMG_5589.JPG)



<!-- _Image Caption_ -->


