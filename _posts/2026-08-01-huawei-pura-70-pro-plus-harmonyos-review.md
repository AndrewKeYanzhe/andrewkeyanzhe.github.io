---
title: "Huawei Pura 70 Pro+ HarmonyOS Review"
date: 2026-08-01 11:00:00 +0800
categories: [Tech Analysis]
tags: [Huawei, 华为, 华为手机, Pura 70 Pro+, HarmonyOS, HarmonyOS 7, HarmonyOS 6, 鸿蒙, 鸿蒙OS, 鸿蒙系统, 纯血鸿蒙, Smartphone, Review]
published: true
image:
  path: assets/2026-08-01-huawei-pura-70-pro-plus-harmonyos-review/pura-70-pro-plus-white-front-and-back padded 40x21.png
---

![Huawei Pura 70 Pro+](assets/2026-08-01-huawei-pura-70-pro-plus-harmonyos-review/pura-70-pro-plus-white-front-and-back.jpg){: width="400"}

<u>This post is a work in progress.</u>

## HarmonyOS 7

Tested on HarmonyOS 7.0.0.111 SP10.

### Video playback

VLC through `卓易通`:
- HEVC HDR playback works and displays in HDR.
- The VP9 HDR file does not display in HDR and appears to be tone mapped to SDR.

This records the observed playback behavior only. It does not establish whether the difference is caused by VLC's VP9 software-decoding/rendering path, `卓易通`, or another part of the video pipeline.

## HarmonyOS 6

Tested on HarmonyOS 6.1.0.117.

### App compatibility

Fortnite ❌
- The app installs via `卓易通`, but after it downloads about 4GB of game data, it crashes to the home screen 
- When re-launched, Fortnite crashes to the home screen every time and is unable to load into the lobby menu.
- Tested on 1 Aug 2026

GTA: San Andreas (Android version)
- Works with Xbox Series X controller.
- FPS is a bit unstable; visually does not look like it is maintaining 30 fps.

异环
- Does not support Xbox Series X controller.

三角洲行动
- Does not support Xbox Series X controller.


### Video Recording

HDR video recording is only available up to 4K 30fps. At 4K 60fps, it becomes SDR.
