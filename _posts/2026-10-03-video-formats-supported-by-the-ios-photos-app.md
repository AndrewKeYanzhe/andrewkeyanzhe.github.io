---
title: "Video formats supported by the iOS Photos app"
date: 2026-10-03 00:00:00 +0800
categories: [Tech Analysis]
tags: [iOS, Photos, iPhone, Video, HDR]
toc: true
published: true
---

This post records video format support tested in the iOS Photos app.

## Test setup

- **Device**: iPhone 14 Pro Max
- **Operating system**: iOS 27.0
- **App**: Photos

## Supported video formats

The Photos app supports **4K, 10-bit, 4:2:2 HDR video with PQ and BT.2020** and **4K, 10-bit, 4:4:4 HDR video with PQ and BT.2020** on the iPhone 14 Pro Max running iOS 27.0.

| Resolution | Bit<br>depth | Chroma<br>sampling | Dynamic<br>range | Transfer<br>function | Color<br>primaries | Support |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 4K | 10-bit | 4:2:2 | HDR | PQ | BT.2020 | ✅ Supported |
| 4K | 10-bit | 4:4:4 | HDR | PQ | BT.2020 | ✅ Supported |
