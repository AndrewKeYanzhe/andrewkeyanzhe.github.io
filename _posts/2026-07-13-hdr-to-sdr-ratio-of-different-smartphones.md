---
title: "HDR headroom and compositor behavior: Android vs iPhone"
date: 2026-07-13 23:55:00 +0800
categories: [Tech Analysis]
tags: [Android, iPhone, Lightroom, HDR]
pin: false
math: true
toc: false
published: true
redirect_from:
  - /posts/hdr-sdr-ratio-of-different-android-phones/
  - /posts/hdr-sdr-ratio-of-different-smartphones/
image:
  path: assets/2026-07-13-hdr-to-sdr-ratio-of-different-smartphones/IMG_3574_thumbnail.avif
---
<!-- The aspect ratio of the post thumbnails is 40/21 (which is approximately 1.905:1 or 1.9:1). -->

**As a reference, the iPhone 14 Pro Max has a maximum HDR to SDR ratio of 8.0** (Source: [Explore HDR rendering with EDR - WWDC21 at timestamp 5:08](https://developer.apple.com/videos/play/wwdc2021/10161/?time=308)).

> iPhone with Super Retina XDR display: Up to 8x SDR

### Lightroom on iPhone

I believe Lightroom supports HDR image preview on all OLED iPhones.

The maximum HDR to SDR ratio for Lightroom on iPhone is `8.0`. In the screenshot, we can see that the histogram shows 3 bars of HDR headroom, so HDR pixels 3 stops above SDR white can be displayed. The 4th bar of HDR headroom in the histogram shows a lighter gray color, so this section exceeds the HDR 8.0 luminance ratio limit. Pixels brighter than 8x SDR will be clipped.

![iPhone 14 Pro Max Lightroom](assets/2026-07-13-hdr-to-sdr-ratio-of-different-smartphones/iPhone%2014%20Pro%20Max%20Lightroom.png){: width="300"}

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
![Pixel 7 Pro Chrome photo](assets/2026-07-13-hdr-to-sdr-ratio-of-different-smartphones/Pixel%207%20Pro%20Chrome%20photo.avif){: .normal width="300"}
![Pixel 7 Pro YouTube video](assets/2026-07-13-hdr-to-sdr-ratio-of-different-smartphones/Pixel%207%20Pro%20YouTube%20video.avif){: .normal width="300"}

> This article contains HDR photos which are best viewed on an HDR-capable device and browser. Recommended setups:
- Windows 11 + HDR ON + Chrome
- Macbook Pro with internal XDR display + Chrome
- iPhone running iOS 26
- a recent Android device with mixed HDR SDR composition support and running Chrome
{: .prompt-tip }

### Samsung Galaxy S26+

**The maximum HDR to SDR ratio is <u>5.0 for photos</u>**

![HDR SDR Ratio Image](assets/2026-07-13-hdr-to-sdr-ratio-of-different-smartphones/IMG_3574.avif){: width="300"}

### Honor Magic V3

This is a foldable phone from Honor, utilising the Snapdragon 8 Gen 3. The phone is running Android 16. Tested in July 2026.

The maximum HDR to SDR ratios are:
- Photos (viewed in Chrome): 4.92
- Videos (viewed in YouTube): 7.46

Lightroom says `HDR Unavailable`.

![Honor Magic V3 Lightroom HDR Unavailable](assets/2026-07-13-hdr-to-sdr-ratio-of-different-smartphones/Honor%20Magic%20V3%20Lightroom%20HDR%20unavailable.jpg){: width="400"}

### Technical deep-dive: How Android manages HDR headroom

So, is there a hard limit in Android restricting photos to ~5.0x SDR and videos to ~8.0x SDR?

<u>This section is still a work in progress. </u>

<!-- TODO add TLDR conclusion, after i have checked -->
<!-- The short answer is **no**. The Android OS framework itself doesn't impose a hard-coded cap of 5.0 or 8.0: -->

* **AOSP Framework Capabilities**: In Android 15 (API level 35), the [`SurfaceView.setDesiredHdrHeadroom`](https://developer.android.com/reference/android/view/SurfaceView#setDesiredHdrHeadroom(float)) API allows applications to request headroom values anywhere from `1.0f` (pure SDR) up to `10000.0f`.


#### Who decides the headroom on real devices?

<u>This section is still a work in progress. </u>

The actual HDR headroom isn't fixed globally; it's calculated and enforced dynamically at runtime by **device OEMs** on a per-model basis:

In AOSP [`DisplayDeviceConfig.java`](https://android.googlesource.com/platform/frameworks/base/+/refs/heads/main/services/core/java/com/android/server/display/DisplayDeviceConfig.java), Android has a function `getHdrBrightnessFromSdr` that returns a float `hdrBrightness`, which I believe is a `0.0-1.0` float representing the Android software brightness value (non-linear mapping to physical nits). This function takes into account the SDR brightness level, the content's desired HDR to SDR ratio, and the OEM configuration in `mHbmData`.

`getHdrBrightnessFromSdr` is an overloaded function that is typically called with 2 arguments `brightness` and `maxDesiredHdrSdrRatio`. This function then calls another overload of itself with 3 arguments `brightness`, `maxDesiredHdrSdrRatio`, and `sdrToHdrSpline`.



```java
// 2 argument function

/**
 * Calculate the HDR brightness for the
 * specified SDR brightness, restricted by the
 * maxDesiredHdrSdrRatio (the ratio between
 * the HDR luminance and SDR luminance)
 *
 * @return the HDR brightness or
 * BRIGHTNESS_INVALID when no mapping exists.
 */
public float getHdrBrightnessFromSdr(
        float brightness,
        float maxDesiredHdrSdrRatio) {
    Spline sdrToHdrSpline =
        mHbmData != null
        ? mHbmData.sdrToHdrRatioSpline : null;
    return getHdrBrightnessFromSdr(
        brightness,
        maxDesiredHdrSdrRatio,
        sdrToHdrSpline);
}

// 3 argument function
    public float getHdrBrightnessFromSdr(float brightness, float maxDesiredHdrSdrRatio,
            @Nullable Spline sdrToHdrSpline) {
...

        return hdrBrightness;
    }
```



* **OEM Vendor Config**: `mHbmData` holds the display configuration written by the OEM for that specific phone model (loaded from `/vendor/etc/displayconfig/display_config_*.xml`).
* **The Spline Curve (`sdrToHdrRatioSpline`)**: The spline acts as a lookup curve (storing parallel control-point arrays for SDR nits and HDR ratios) to interpolate values smoothly.
* **Return Value**: `hdrBrightness` — an Android software brightness value (`0.0‑1.0`
, non-linear mapping to physical nits) representing the peak HDR brightness ceiling for the current SDR brightness level.


<!-- TODO. check this part for accuracy -->

<!-- #### Why do photos cap at ~5.0 while videos reach ~8.0?

The reason photos and videos exhibit different headroom comes down to hardware composition pipelines:

* **Photos (Chrome / Gallery / GPU Composition)**: Static images (both Ultra HDR gain maps and 10-bit PQ AVIFs) are rendered as static GPU layers (GLES / Vulkan / Skia). To preserve SDR UI text contrast, conserve battery, and protect against OLED burn-in during static viewing, OEM profile maps limit static image HDR headroom to roughly **5.0x SDR white** (~500 nits over 100 nits SDR white).
* **Videos (`SurfaceView` / Hardware Overlays)**: Video players output frames via `SurfaceView`, which SurfaceFlinger routes directly to dedicated Hardware Composer (HWC) video overlay planes. Because moving video carries no burn-in risk and bypasses GPU composition, OEM configurations allow video overlays to burst up to **8.0x SDR white** (~800 to 1000 nits over 100 nits SDR white). -->








