---
title: "Codex and iOS ChatGPT Remote’s handling of HDR images attached to the conversation"
date: 2026-11-20 12:27:00 +0800
categories: [Tech Analysis]
tags: [Codex, ChatGPT, HDR, iOS, AVIF, PNG, PQ, BT.2020]
toc: false
published: true
---

A 10-bit BT.2020/PQ HDR AVIF image without a gain map was inserted by the LLM agent into the Codex Windows conversation.

## Example reply returned to the harness

```markdown
Here is the HDR image you wanted.

[Open the HDR image](<C:/example/hdr-image.avif>)
```

| Property | Source image on Windows | Image retrieved from ChatGPT Remote on iOS |
|---|---|---|
| File format | AVIF | PNG |
| Dimensions | 2218 × 1469 | 2218 × 1469 |
| Pixel format | 10-bit full-range YUV 4:4:4 | 16-bit full-range RGB |
| Color primaries | BT.2020 | BT.2020 |
| Transfer function | SMPTE ST 2084 PQ | SMPTE ST 2084 PQ |
| Gain map | None | None |
| Brightest sampled pixel | 107.9 nits | 108.0 nits |
