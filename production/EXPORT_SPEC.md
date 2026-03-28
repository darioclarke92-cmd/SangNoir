# SANG NOIR -- EXPORT SPECIFICATION
## YouTube 16:9 and TikTok 9:16 Pipeline

---

## Overview

SANG NOIR releases on two platforms:
- **YouTube:** 1920x1080 (16:9) -- primary master
- **TikTok / Instagram Reels:** 1080x1920 (9:16 vertical) -- social recut

---

## Master Export (YouTube)

### Blender Render Settings
- Resolution: 1920x1080, 24fps
- Output: PNG sequence to renders/ep01/16x9/

### DaVinci Resolve Export
- Format: MP4, Codec: H.264
- Quality: Restrict to 35,000 Kbps
- Audio: AAC, 48kHz, Stereo, 320kbps
- File name: `SANG_NOIR_EP01_v1.mp4`

**YouTube Upload:**
- Title format: `SANG NOIR | EP01 | "The Night the Lights Went Out"`
- Add to "SANG NOIR Season 1" playlist

---

## TikTok/Reels Export

TikTok cuts are NOT full episodes. They are 45-90 second hero moments: the best fight beat, the most striking scene.

For each episode, identify 1-2 moments during shot listing (mark as [SOCIAL] in SHOT_LIST.md).
These shots should be composed with key action in the centre 1080px of the 1920px frame.

### Safe Zone Guide

```
|<-------- 1920px (full 16:9) -------->|
|  420px  |<--- 1080px safe --->|  420px  |
|         |                     |         |
|         | KEY ACTION HERE     |         |
|         | for [SOCIAL] shots  |         |
|         |                     |         |
```

### DaVinci TikTok Workflow
1. Create new timeline in same project: `EP01_TIKTOK`
2. Timeline settings: 1080x1920, 24fps
3. Import same PNG sequences
4. Reframe using Transform controls
5. Add lower-third: `SANG NOIR | EP1` in white
6. Trim to 45-90 seconds

### DaVinci TikTok Export
- Format: MP4, Codec: H.264
- Quality: Restrict to 20,000 Kbps
- Audio: AAC, 44.1kHz, Stereo, 192kbps
- File name: `SANG_NOIR_EP01_TIKTOK_v1.mp4`

---

## Video Specs Summary

| Platform | Resolution | FPS | Format | Bitrate |
|---|---|---|---|---|
| YouTube | 1920x1080 | 24 | MP4 H.264 | 35,000 Kbps |
| TikTok | 1080x1920 | 24 | MP4 H.264 | 20,000 Kbps |

---

## Audio Specs

All audio mixed in DaVinci Resolve:
- Music: assets/music/ as MP3 or WAV
- SFX: assets/audio/ as WAV only
- Voices (Phase 2): assets/audio/voices/ as MP3
- Master audio peak: leave -3dB headroom

---

## File Naming Convention

| File | Format |
|---|---|
| YouTube master | SANG_NOIR_EP[##]_v[n].mp4 |
| TikTok cut | SANG_NOIR_EP[##]_TIKTOK_v[n].mp4 |
| PNG renders | ep[##]_sc[##]_[desc]_[frame].png |
| DaVinci project | SANG_NOIR_EP[##].drp |
