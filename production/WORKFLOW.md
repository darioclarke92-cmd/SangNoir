# SANG NOIR -- PRODUCTION WORKFLOW
## Full Step-by-Step Pipeline

---

## The Golden Rule

No step begins until the step before it is locked. Script before shot list. Shot list before asset list. Asset list before Blender. In order.

---

## Phase 0: Pre-Production (Current Phase)

### Documents
- [x] Series Bible
- [x] Visual Style Guide
- [x] World Building
- [x] Lore documents
- [x] Character sheets (all 6)
- [x] VFX Spec
- [ ] Episode 1 Script -- episodes/ep01/SCRIPT.md
- [ ] Episode 1 Shot List -- episodes/ep01/SHOT_LIST.md
- [ ] Episode 1 Storyboard Notes -- episodes/ep01/STORYBOARD_NOTES.md
- [ ] Episode 1 Asset List -- episodes/ep01/ASSET_LIST.md

### References to Collect
- [ ] Location photos (see README.md for full list)
- [ ] Clothing references for VRoid
- [ ] VFX references (smoke, shadow, impact)
- [ ] Afro Samurai frames

---

## Phase 1: Concept Art (Krita)

Draw rough concept versions of each asset before building in VRoid/Blender.

Character concept art:
- [ ] Tre -- front view, side view
- [ ] Gabriel -- front view, side view
- [ ] Malgris (human form) -- front view
- [ ] Dog Tamer -- silhouette focus
- [ ] Madeleine -- front view

Location thumbnails (rough, no detail):
- [ ] Estate exterior night
- [ ] Estate flat interior
- [ ] Brixton arch
- [ ] Underground platform

Save in assets/characters/concepts/ and assets/environments/concepts/

---

## Phase 2: Character Build (VRoid Studio)

Build in order of appearance in Episode 1:
1. Tre Pourfendeur
2. Gabriel Pourfendeur
3. Dog Tamer
4. Mother (minor model)

Per character:
- [ ] Build from character sheet specification
- [ ] Export as .vrm to assets/characters/
- [ ] Test import into Blender
- [ ] Check proportions against character sheet

Do NOT begin animation until all Episode 1 characters pass Blender import test.

---

## Phase 3: Texture Work (Krita + Blender)

Per character:
- Tre: Scar facial texture, left forearm mark texture
- Gabriel: Right forearm mark texture
- Madeleine: Forearm and collarbone clan mark textures

Environment textures (Episode 1):
- Concrete wall tile
- Wet tarmac ground
- Estate door

Save in assets/characters/textures/ or assets/environments/textures/

---

## Phase 4: Environment Build (Blender)

Build Episode 1 environments as separate .blend files:
- [ ] ep01_sc01_estate_exterior.blend
- [ ] ep01_sc02_flat_interior.blend
- [ ] ep01_sc03_walkway_night.blend

Per environment:
- [ ] Test render with lighting
- [ ] Compare to references in references/locations/
- [ ] Adjust until location reads correctly

---

## Phase 5: VFX Build (Blender)

Build and test all VFX systems before episode animation begins:
- [ ] Shadow particle system Tre -- 5 second test render
- [ ] Shadow particle system Gabriel -- 5 second test render
- [ ] Impact detonation system -- single impact test render
- [ ] Greatsword model + emergence animation
- [ ] Dual dagger models + emergence animation
- [ ] Demon hound shadow leak particles

Store in assets/vfx/ -- these are reusable across all episodes.

---

## Phase 6: Animation (Blender)

Work scene by scene, in script order.

Per scene:
1. Load environment .blend
2. Link character assets (File > Link)
3. Pose first frame
4. Keyframe animation following SHOT_LIST.md
5. Reference SCRIPT.md for dialogue scenes
6. Reference STORYBOARD_NOTES.md for action beats

Animation style notes:
- 24fps throughout
- Hold key poses for 2-4 frames at impact/reaction moments
- Movement cuts -- it is not smooth. This is correct.
- Fast action: "twos" (new pose every 2 frames)
- Dialogue/slow scenes: "eights" or "sixteens"

---

## Phase 7: Render (Blender)

After each scene animation is locked:
1. Set output path to renders/ep01/16x9/sc[##]/
2. Output format: PNG
3. Start render: Render > Render Animation
4. Monitor first 10 frames for errors
5. Let render run (overnight if needed)

Do NOT render audio from Blender. Video PNG only. All audio added in DaVinci.

---

## Phase 8: Assembly (DaVinci Resolve)

After all scenes for Episode 1 are rendered:
1. Import all PNG sequences
2. Assemble in timeline order
3. Add music (assets/music/) per SOUNDTRACK_DIRECTION.md
4. Add SFX (assets/audio/) per SOUND_DESIGN.md
5. Colour grade per location (VISUAL_STYLE_GUIDE.md)
6. Review against SCRIPT.md
7. Export YouTube version
8. Create TikTok cut
9. Final review. Lock.

---

## Phase 9: Voice (ElevenLabs) -- Phase 2

After visual is locked per episode:
1. Extract all dialogue from SCRIPT.md
2. Record each line via ElevenLabs
3. Import to DaVinci, sync to animation
4. Adjust mouth animation in Blender if sync is off
5. Re-export final version with voice

---

## Quality Check Before Export

**Story:**
- [ ] Every scene in SCRIPT.md is present
- [ ] Character action matches SCRIPT.md

**Visual:**
- [ ] Colour palette matches VISUAL_STYLE_GUIDE.md location specs
- [ ] Toon outlines consistent
- [ ] Shadow power consistent (Tre vs Gabriel correctly different)
- [ ] No characters with wrong eye/skin colour vs character sheets

**Audio:**
- [ ] No audio clipping (no peaks above -3dB)
- [ ] Music matches SOUNDTRACK_DIRECTION.md
- [ ] Ambient design present for all locations
- [ ] Impact SFX weight correct

**Technical:**
- [ ] Correct resolution and frame rate
- [ ] No missing frames in PNG render sequences
- [ ] Export file size reasonable (300-600MB per 3-minute episode is normal for YouTube)
