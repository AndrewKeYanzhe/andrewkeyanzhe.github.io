---
title: HDR to SDR ratio of different smartphones
date: 2026-07-13 23:55:00 +0800
categories: [Tech Analysis]
tags: [Android, iPhone, HDR]
pin: false
math: true
toc: false
published: true
image:
  path: assets/2026-07-13-hdr-sdr-ratio-of-different-android-phones/IMG_3574_thumbnail.avif
---
<!-- The aspect ratio of the post thumbnails is 40/21 (which is approximately 1.905:1 or 1.9:1). -->

**As a reference, the iPhone 14 Pro Max has a maximum HDR to SDR ratio of 8.0** (Source: [Explore HDR rendering with EDR - WWDC21 at timestamp 5:08](https://developer.apple.com/videos/play/wwdc2021/10161/?time=308)).

> iPhone with Super Retina XDR display: Up to 8x SDR

### Lightroom on iPhone

I believe Lightroom supports HDR image preview on all OLED iPhones.

The maximum HDR to SDR ratio for Lightroom on iPhone is `8.0`. In the screenshot, we can see that the histogram shows 3 bars of HDR headroom, so HDR pixels 3 stops above SDR white can be displayed. The 4th bar of HDR headroom in the histogram shows a lighter gray color, so this section exceeds the HDR 8.0 luminance ratio limit. Pixels brighter than 8x SDR will be clipped.

![iPhone 14 Pro Max Lightroom](assets/2026-07-13-hdr-sdr-ratio-of-different-android-phones/iPhone%2014%20Pro%20Max%20Lightroom.png){: width="300"}

The screenshot was captured on an iPhone 14 Pro Max.


### Android compositor behavior

On Android, it appears that the maximum HDR to SDR ratio is `5.0 for images`, and `8.0 for videos`. However, I have not tested every Android configuration and I cannot say for certain if there exists any Android device with a higher HDR to SDR ratio for photos or videos.

<u>This section is a work in progress.</u>

### Lightroom on Android

Lightroom on Android seems to enable HDR on certain devices using a whitelist system.

As of July 2026, the list only includes Google devices since the Pixel 7, and Samsung devices since the S24.


> So, there are many Android devices that do support mixed HDR SDR composition, but are unable to utilise Lightroom's HDR image preview due to the whitelist system. See the section on the Honor Magic V3.
{: .prompt-warning }

The full list is here: [https://helpx.adobe.com/ie/lightroom-cc/using/hdr-android.html#hdr-compatible](https://helpx.adobe.com/ie/lightroom-cc/using/hdr-android.html#hdr-compatible)


### Google Pixel 7 Pro (Android 16)

**The maximum HDR to SDR ratio is <u>4.92 for HDR photos viewed in Chrome</u>**

This maximum HDR to SDR ratio of 4.92 can be maintained up to around SDR=140 nits (visual estimate). The HDR/SDR ratio overlay can be enabled in `developer options` for devices running Android 15 or newer.



**The maximum HDR to SDR ratio is <u>7.99 for videos</u>**

This maximum HDR to SDR ratio of 7.99 can be maintained up to around SDR=100 nits (visual estimate).

{: .d-flex .justify-content-center style="gap: 2rem; margin-left: 0rem;" }
![Pixel 7 Pro Chrome photo](assets/2026-07-13-hdr-sdr-ratio-of-different-android-phones/Pixel%207%20Pro%20Chrome%20photo.avif){: .normal width="300"}
![Pixel 7 Pro YouTube video](assets/2026-07-13-hdr-sdr-ratio-of-different-android-phones/Pixel%207%20Pro%20YouTube%20video.avif){: .normal width="300"}

> This article contains HDR photos which are best viewed on an HDR-capable device and browser. Recommended setups:
- Windows 11 + HDR ON + Chrome
- Macbook Pro with internal XDR display + Chrome
- iPhone running iOS 26
- a recent Android device with mixed HDR SDR composition support and running Chrome
{: .prompt-tip }

### Samsung Galaxy S26+

**The maximum HDR to SDR ratio is <u>5.0 for photos</u>**

![HDR SDR Ratio Image](assets/2026-07-13-hdr-sdr-ratio-of-different-android-phones/IMG_3574.avif){: width="300"}

### Honor Magic V3

This is a foldable phone from Honor, utilising the Snapdragon 8 Gen 3. The phone is running Android 16. Tested in July 2026.

The maximum HDR to SDR ratios are:
- Photos (viewed in Chrome): 4.92
- Videos (viewed in YouTube): 7.46

Lightroom says `HDR Unavailable`.

![Honor Magic V3 Lightroom HDR Unavailable](assets/2026-07-13-hdr-sdr-ratio-of-different-android-phones/Honor%20Magic%20V3%20Lightroom%20HDR%20unavailable.jpg){: width="400"}



