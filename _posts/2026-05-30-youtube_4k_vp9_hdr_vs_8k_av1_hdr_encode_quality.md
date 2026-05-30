---
title: YouTube 4K VP9 HDR vs 8K AV1 HDR encode quality
date: 2026-05-30 12:00:00 +0800  
categories: [Tech Analysis]  
tags: [YouTube, VP9, AV1, HDR]  
pin: false  
math: true  
toc: false
published: true

image:
  path: assets/2026-05-30-youtube_4k_vp9_hdr_vs_8k_av1_hdr_encode_quality/Screenshot%202026-05-30%2011-59-53%204K%20VP9%20HDR.png
---

<style>
  #post-wrapper .preview-img {
    display: none;
  }
</style>


**Comparison of YouTube's HDR encoding quality: 4K VP9 HDR vs 8K AV1 HDR vs original 4K export**



YouTube has encoded the video [Fire performance at Homerton College, HDR](https://www.youtube.com/watch?v=5kjcrVJUZY8) into the following formats:
- **4K VP9 HDR (337)**: 22.6 Mbps (vp9.2, webm, 30 fps)
- **8K AV1 HDR (702)**: 39.7 Mbps (av01, mp4, 30 fps)



We will compare it with the original 4K 30 fps HEVC export from DaVinci Resolve which is 233 Mbps.

HDR screenshots best viewed on a HDR capable device (Windows 11 + HDR ON + Chrome, Macbook Pro with XDR display, iPhone on iOS 26, newer Android phones with mixed HDR SDR composition E.g. Samsung Galaxy S25 or newer)

#### **100% crops (Face)**

The 8K AV1 HDR encode shows less compression artifacts compared to the 4K VP9 HDR encode, though it still resolves significantly less detail than the original 4K HEVC export.

<div class="d-flex justify-content-center">
  <img src="assets/2026-05-30-youtube_4k_vp9_hdr_vs_8k_av1_hdr_encode_quality/Screenshot%202026-05-30%2011-59-53%204K%20VP9%20HDR.png"
       style="width: 300px; height: 337px; object-fit: none; object-position: 56% 52%; margin-right: 0.5rem;"
       alt="4K VP9 HDR">
  <img src="assets/2026-05-30-youtube_4k_vp9_hdr_vs_8k_av1_hdr_encode_quality/Screenshot%202026-05-30%2012-00-15%208K%20AV1%20HDR.png"
       style="width: 300px; height: 337px; object-fit: none; object-position: 56% 52%; margin-right: 0.5rem;"
       alt="8K AV1 HDR">
  <img src="assets/2026-05-30-youtube_4k_vp9_hdr_vs_8k_av1_hdr_encode_quality/Screenshot%202026-05-30%2012-00-26%20MPV.png"
       style="width: 300px; height: 337px; object-fit: none; object-position: 56% 52%;"
       alt="MPV">
</div>

<div class="d-flex justify-content-center" style="gap: 0.5rem; margin-bottom: 1.5rem;">
  <div style="width: 300px; text-align: center;">1. 4K VP9 HDR (YouTube)</div>
  <div style="width: 300px; text-align: center;">2. 8K AV1 HDR (YouTube)</div>
  <div style="width: 300px; text-align: center;">3. Original 4K export</div>
</div>

#### **100% crops (Left upper arm)**

Surprisingly, we can see some macroblocking artefacts on the 8K AV1 HDR video which does not exist on the 4K VP9 HDR video. 

<div class="d-flex justify-content-center">
  <img src="assets/2026-05-30-youtube_4k_vp9_hdr_vs_8k_av1_hdr_encode_quality/Screenshot%202026-05-30%2011-59-53%204K%20VP9%20HDR.png"
       style="width: 300px; height: 337px; object-fit: none; object-position: 65% 75%; margin-right: 0.5rem;"
       alt="4K VP9 HDR">
  <img src="assets/2026-05-30-youtube_4k_vp9_hdr_vs_8k_av1_hdr_encode_quality/Screenshot%202026-05-30%2012-00-15%208K%20AV1%20HDR.png"
       style="width: 300px; height: 337px; object-fit: none; object-position: 65% 75%; margin-right: 0.5rem;"
       alt="8K AV1 HDR">
  <img src="assets/2026-05-30-youtube_4k_vp9_hdr_vs_8k_av1_hdr_encode_quality/Screenshot%202026-05-30%2012-00-26%20MPV.png"
       style="width: 300px; height: 337px; object-fit: none; object-position: 65% 75%;"
       alt="MPV">
</div>

<div class="d-flex justify-content-center" style="gap: 0.5rem; margin-bottom: 1.5rem;">
  <div style="width: 300px; text-align: center;">1. 4K VP9 HDR (YouTube)</div>
  <div style="width: 300px; text-align: center;">2. 8K AV1 HDR (YouTube)</div>
  <div style="width: 300px; text-align: center;">3. Original 4K export</div>
</div>

#### **100% crops (Left flame)**

The 4K VP9 HDR encode shows more compression artefacts.

<div class="d-flex justify-content-center">
  <img src="assets/2026-05-30-youtube_4k_vp9_hdr_vs_8k_av1_hdr_encode_quality/Screenshot%202026-05-30%2011-59-53%204K%20VP9%20HDR.png"
       style="width: 300px; height: 337px; object-fit: none; object-position: 27% 38%; margin-right: 0.5rem;"
       alt="4K VP9 HDR">
  <img src="assets/2026-05-30-youtube_4k_vp9_hdr_vs_8k_av1_hdr_encode_quality/Screenshot%202026-05-30%2012-00-15%208K%20AV1%20HDR.png"
       style="width: 300px; height: 337px; object-fit: none; object-position: 27% 38%; margin-right: 0.5rem;"
       alt="8K AV1 HDR">
  <img src="assets/2026-05-30-youtube_4k_vp9_hdr_vs_8k_av1_hdr_encode_quality/Screenshot%202026-05-30%2012-00-26%20MPV.png"
       style="width: 300px; height: 337px; object-fit: none; object-position: 27% 38%;"
       alt="MPV">
</div>

<div class="d-flex justify-content-center" style="gap: 0.5rem; margin-bottom: 1.5rem;">
  <div style="width: 300px; text-align: center;">1. 4K VP9 HDR (YouTube)</div>
  <div style="width: 300px; text-align: center;">2. 8K AV1 HDR (YouTube)</div>
  <div style="width: 300px; text-align: center;">3. Original 4K export</div>
</div>

#### **Full size screenshots**

#### **1. 4K VP9 HDR (22.6 Mbps)**
![4K VP9 HDR](assets/2026-05-30-youtube_4k_vp9_hdr_vs_8k_av1_hdr_encode_quality/Screenshot%202026-05-30%2011-59-53%204K%20VP9%20HDR.png)

#### **2. 8K AV1 HDR (39.7 Mbps)**
![8K AV1 HDR](assets/2026-05-30-youtube_4k_vp9_hdr_vs_8k_av1_hdr_encode_quality/Screenshot%202026-05-30%2012-00-15%208K%20AV1%20HDR.png)

#### **3. 4K HEVC export from DaVinci Resolve (233 Mbps)**
![MPV](assets/2026-05-30-youtube_4k_vp9_hdr_vs_8k_av1_hdr_encode_quality/Screenshot%202026-05-30%2012-00-26%20MPV.png)
