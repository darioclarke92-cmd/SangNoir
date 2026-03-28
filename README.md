# SANG NOIR

**"Blood Remembers"**

A South London anime series. Two French-British brothers discover they are the last of a legendary demon-hunting bloodline as the ancient warlord who destroyed their clan in medieval France rises again to finish the job in England.

---

## Repository Structure

```
SangNoir/
├── README.md                        This file
├── SERIES_BIBLE.md                  Full series bible - start here
├── WORLD_BUILDING.md                Locations, atmosphere, world rules
├── VISUAL_STYLE_GUIDE.md            EEVEE shading, colour palette, visual spec
├── SOUNDTRACK_DIRECTION.md          Music and sound direction per scene type
├── lore/
│   ├── CLAN_HISTORY.md              Pourfendeur clan - medieval France to London
│   └── MALGRIS_HISTORY.md           The warlord - history, motivation, power
├── characters/
│   ├── TRE_POURFENDEUR.md           Protagonist - full production sheet
│   ├── GABRIEL_POURFENDEUR.md       Brother / anti-hero - full production sheet
│   ├── MALGRIS.md                   Main antagonist - full production sheet
│   ├── MADELEINE_POURFENDEUR.md     Ancestor guide - full production sheet
│   ├── DOG_TAMER.md                 First antagonist - full production sheet
│   └── REMY_POURFENDEUR.md          The father (deceased) - full production sheet
├── episodes/
│   └── ep01/
│       ├── SCRIPT.md                Full formatted screenplay
│       ├── SHOT_LIST.md             Numbered shots - camera, action, lighting
│       ├── STORYBOARD_NOTES.md      Panel descriptions for every key beat
│       └── ASSET_LIST.md            Every character, prop, location, VFX for Ep1
├── production/
│   ├── SOFTWARE_SETUP.md            Step-by-step install and config (beginner)
│   ├── RENDER_SETTINGS.md           Blender EEVEE settings for mid-range GPU
│   ├── VFX_SPEC.md                  Shadow power build in Blender - full spec
│   ├── SOUND_DESIGN.md              SFX design per character/event/environment
│   ├── EXPORT_SPEC.md               YouTube 16:9 and TikTok 9:16 export pipeline
│   └── WORKFLOW.md                  Full production pipeline, step by step
├── references/
│   ├── locations/                   Drop location photos here
│   ├── clothing/                    Character clothing references for VRoid
│   ├── vfx/                         Shadow/smoke/explosion visual references
│   └── animation/                   Afro Samurai frames, impact references
├── assets/
│   ├── characters/                  VRoid .vrm files and Blender character rigs
│   ├── environments/                Blender .blend environment files
│   ├── vfx/                         Shadow particle systems and shader assets
│   ├── audio/                       Audacity SFX exports (.wav)
│   └── music/                       Suno music exports (.mp3/.wav)
└── renders/
    └── ep01/
        ├── 16x9/                    YouTube master renders (1920x1080)
        └── 9x16/                    TikTok/Reels cuts (1080x1920)
```

---

## Document Order - Read Before Building

| Priority | Document | Purpose |
|---|---|---|
| 1 | SERIES_BIBLE.md | Foundation - every other doc checks against this |
| 2 | VISUAL_STYLE_GUIDE.md | Locks the look before any modelling starts |
| 3 | WORLD_BUILDING.md | Location and atmosphere detail for Blender |
| 4 | lore/CLAN_HISTORY.md | Required before writing Ep3, Ep10 scripts |
| 5 | lore/MALGRIS_HISTORY.md | Required before writing Ep9, Ep10, Ep12 |
| 6 | Character sheets x6 | Informed by style guide - model from these |
| 7 | production/VFX_SPEC.md | Lock shadow power approach before Ep1 asset list |
| 8 | episodes/ep01/SCRIPT.md | Script comes before everything below it |
| 9 | episodes/ep01/SHOT_LIST.md | Script must exist first |
| 10 | episodes/ep01/STORYBOARD_NOTES.md | Shot list must exist first |
| 11 | episodes/ep01/ASSET_LIST.md | Shot list reveals every asset needed |
| 12 | Production docs | Before Blender is opened |

---

## Software Stack

| Tool | Purpose | Download |
|---|---|---|
| Blender (EEVEE renderer) | 3D animation + rendering | blender.org |
| VRoid Studio | Anime character creation | vroid.com |
| Krita | Concept art / texture painting / storyboards | krita.org |
| DaVinci Resolve | Video editing + colour grading | blackmagicdesign.com |
| Audacity | SFX recording and editing | audacityteam.org |
| Suno | AI music generation | suno.com |
| ElevenLabs | AI voice acting (Phase 2) | elevenlabs.io |

All free.

---

## Technical Specs

- Render engine: Blender EEVEE (not Cycles)
- Target GPU: GTX 1070-3070 / RX 580-6700
- RAM: 16GB
- YouTube output: 1920x1080, 24fps, H.264
- TikTok output: 1080x1920, 24fps, H.264
- Episode length: 2-3 minutes each

---

## Current Status

- [x] Series bible locked
- [x] Episode map approved (12 episodes)
- [x] Characters confirmed
- [x] Repo structure created
- [ ] All pre-production documents written
- [ ] Episode 1 script
- [ ] Character models built
- [ ] Episode 1 rendered

---

## Series Overview

Season 1 - "Blood Remembers" - 12 episodes. 2-3 minutes each. Cold open, no OP sequence.

Tre and Gabriel Pourfendeur - two brothers from Peckham, South London - have never heard of the Pourfendeur clan. Their father died when they were young. Their mother told them he left.

When a demon general called the Dog Tamer arrives at their estate and kills their mother, something in their blood wakes up. The shadow was always there. It just needed a reason.

The demon warlord Malgris - who destroyed the Pourfendeur clan in 1300s France - has tracked the last of the bloodline to London. He sends champions first. He wants to see what they have become before he ends it himself. He will not make that mistake twice.

SANG NOIR. The blood is black. It remembers everything.
