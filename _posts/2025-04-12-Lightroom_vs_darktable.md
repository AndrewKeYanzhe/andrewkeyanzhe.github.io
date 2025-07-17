---
title: Lightroom vs darktable RAW to HDR development color accuracy
# description: Examples of text, typography, math equations, diagrams, flowcharts, pictures, videos, and more.
# author: Andrew Ke
date: 2025-04-12 10:00:00 +0000
categories: [Tech Analysis]
tags: [HDR, Lightroom, darktable, Panasonic Lumix S5ii]
# pin: true
math: true
# mermaid: true

# media_subpath: posts/2019-08-08-text-and-typography/
# media_subpath: 

---

HDR images best viewed on an HDR capable device + browser. Recommended setup: Macbook Pro 16 with XDR display + Google Chrome.

An HDR YouTube video was displayed on the M1 Macbook Pro 16 and the Panasonic Lumix S5II was used to take a photo of the screen. The raw files were then converted into HDR AVIF by Lightroom 14.2 (Camera Raw 17.2) and darktable 5.0.1. You can download the raw file [here](https://drive.google.com/drive/u/0/folders/1YIhkxHvp77HHTaanyFJ5LXX28jH74Rau). The settings used to develop the photos will be given at the end of this post.


Zebra indicators on the S5II and raw overexposure indicators in darktable confirm that no overexposure is present.


The image from Lightroom appears desaturated. A discussion has been created on the Adobe forum [https://community.adobe.com/t5/lightroom-classic-discussions/wide-gamut-hdr-colours-are-desaturated/m-p/15352803](https://community.adobe.com/t5/lightroom-classic-discussions/wide-gamut-hdr-colours-are-desaturated/m-p/15352803). It may very well be possible that I am unware of a setting in Lightroom that avoids the desaturation. If you have any ideas, feel free to add to the discussion on the Adobe forum.

<div style="text-align: center;">
  <h4>RAW image shot on the S5ii and converted to HDR AVIF</h4>
</div>
<!-- #### RAW image shot on the S5ii and converted to HDR AVIF -->

{: .d-flex .justify-content-center style="margin-bottom: 0rem; "}
<!-- ![img-description](assets/2025-04-12-Lightroom_vs_darktable/P1123045_lr_web_adobe_color.avif){: .normal .mw-50 .me-2} -->
![img-description](assets/2025-04-12-Lightroom_vs_darktable/P1123045_lr_web_adobe_color.avif){: .normal .mw-50}
![img-description](assets/2025-04-12-Lightroom_vs_darktable/P1123045_dt_web.avif){: .normal .mw-50}


<div class="d-flex justify-content-center" style="gap: 0.5rem;" style="margin-bottom: 1rem; color:#6d6c6c;">
  <div style="width: 50%; text-align: center; font-size:80%;">Lightroom (Adobe Color)</div>
  <div style="width: 50%; text-align: center; font-size:80%;">Darktable</div>
</div>


<div style="text-align: center;">
  <h4>Screenshot of the HDR content (displayed on Macbook Pro 16)</h4>
</div>
<!-- #### Screenshot of the HDR content (displayed on Macbook Pro 16) -->


<!-- ![img-description](assets/2025-04-12-Lightroom_vs_darktable/smoke grenades_1.1.1 +1ev.avif){: width="50%" .justify-content-center} -->
![img-description](assets/2025-04-12-Lightroom_vs_darktable/smoke grenades_1.1.1 +1ev.avif){: .w-50}
_Original image. Credit: [Colored Smoke Grenades](https://youtu.be/0FYjApop7Mk?si=S-cXCX-0hyAvsTpp&t=23) by Jacob + Katie Schwarz_
<!-- _Image Caption_ -->


The following settings are used for Lightroom in addition to the default settings
- Profile: Adobe Color
- HDR editing: On
- Exposure: +3.4 stops

The following settings are used for darktable in addition to the default settings
- Filmic module: Disabled
- Output colour space: PQ BT2020
- Exposure: increased such that it matches the HDR video

Lightroom mobile v. 10.3.1 71F6C8/202 running on the iPhone 14 Pro Max exhibits a similar behaviour to Lightroom Classic.

I have also tried the Adobe Neutral color profile and the orange color is similarly desaturated:

![img-description](assets/2025-04-12-Lightroom_vs_darktable/P1123045_lr_web_adobe_neutral.avif){: .w-50}
_Lightroom with Adobe Neutral profile_
