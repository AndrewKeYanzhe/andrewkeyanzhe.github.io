---
title: "HDR photo support across social media platforms"
date: 2026-09-06 09:45:00 +0800
categories: [Tech Analysis]
tags: [HDR, Social Media, Instagram, AVIF, JPEG XL, JXL, PQ, BT.2020, Direct Message]
pin: false
math: false
toc: true
published: true
---

A test of HDR and next-generation still image format support across social media platforms.

Testing was conducted on **September 6, 2026**.

---

## Summary table

<style>
  .table-wrapper table th,
  .table-wrapper table td {
    white-space: normal !important;
  }
  .table-wrapper table th:first-child,
  .table-wrapper table td:first-child {
    white-space: nowrap !important;
  }
</style>

| Platform | Notes |
| :--- | :--- |
| **Instagram Direct Message**<br>(Tested on September 6, 2026) | - **HDR AVIF (PQ BT2020 no gain map)**: ❌ Not supported. Interpreted as SDR after sending. The resulting image shows up in a flat, washed-out "log footage" appearance.<br>- **SDR JXL**: ✅ Supported; uploads and renders correctly. |
