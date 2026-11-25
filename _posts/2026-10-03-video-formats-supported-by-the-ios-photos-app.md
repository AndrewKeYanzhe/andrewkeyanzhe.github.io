---
title: "Video formats supported by Photos on iOS and macOS"
date: 2026-10-03 00:00:00 +0800
categories: [Tech Analysis]
tags: [iOS, macOS, Photos, iPhone, Video, HDR]
toc: true
published: true
---

This post records video import tests in Photos on iOS and macOS.

## Initial iOS test setup

- **Device**: iPhone 14 Pro Max
- **Operating system**: iOS 27.0
- **App**: Photos

## Supported video formats on iOS

On the iPhone 14 Pro Max running iOS 27.0, Photos imported examples of **4K, 10-bit, 4:2:2 HDR video with PQ and BT.2020** and **4K, 10-bit, 4:4:4 HDR video with PQ and BT.2020**.

| Resolution | Bit<br>depth | Chroma<br>sampling | Transfer<br>function | Color<br>primaries | Supported |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 4K | 10-bit | 4:2:2 | PQ | BT.2020 | ✅  |
| 4K | 10-bit | 4:4:4 | PQ | BT.2020 | ✅  |

## Detailed import tests

Two Log Cam videos (4K, 10-bit, 4:4:4 HEVC, roughly 240 Mb/s) as well as their re-encoded 4:4:4 PQ BT.2020 HDR versions were tested for import into the iPhone Photos app.

The device was an iPhone 14 Pro Max running iOS 27.2.1.

Only one of the two re-encoded PQ videos was imported successfully.

- The two re-encoded PQ videos have the same HEVC decoder configuration and color tags.
- The re-encoded bus stop video has a much higher average video bitrate (591 vs. 172 Mb/s for the fountain video), so that could be a possible reason it failed to import.

Nonetheless, the exact cause of the iOS import failures remains unverified.

| Video | Signaled HEVC level | Average video bitrate | iOS Photos import |
| :--- | :--- | ---: | :--- |
| Fountain original | 7.1 (`213`) | 247.2 Mb/s | Failed |
| Fountain PQ | 5.1 (`153`) | 171.6 Mb/s | Succeeded |
| Bus stop original | 7.1 (`213`) | 247.0 Mb/s | Failed |
| Bus stop PQ | 5.1 (`153`) | 591.1 Mb/s | Failed |

The test was done by dragging the videos from the Files app onto the Photos app. This message was displayed when an import failed:

> Some Items Not Imported
>
> One or more items are not supported by Photos and cannot be imported into your library.

When Apple’s API was used to save a video to iOS Photos, this error was displayed on failure:

> PHPhotosErrorDomain error 3302

> **Photos on macOS 27.3.** All four clips imported successfully as referenced files.
{: .prompt-info }
