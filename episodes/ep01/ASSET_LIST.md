# SANG NOIR — EPISODE 1
## Asset List — "The Night the Lights Went Out"

**Purpose:** Every asset that must be built before Episode 1 can be rendered. Organised by category. Each entry includes what it is, what software builds it, and what reference file to use.

Build nothing that is not on this list for Episode 1.

---

## STATUS KEY

| Status | Meaning |
|---|---|
| [ ] | Not started |
| [WIP] | In progress |
| [DONE] | Complete and tested in scene |

---

## 1. CHARACTERS

### 1A. Tré Pourfendeur — VRoid Model
- **Software:** VRoid Studio → export .vrm → import to Blender via VRM add-on
- **Reference:** `characters/TRE_POURFENDEUR.md`, `references/clothing/tre_*`
- **Spec:**
  - Height: 5'11" — set via VRoid body sliders
  - Skin: medium-dark brown (#8B5E3C)
  - Hair: short twists, dark brown-black (#1A1410)
  - Eyes: dark brown, alert default expression
  - Scar: above left eyebrow — add as face texture detail in Krita, apply as face texture overlay in VRoid
  - Clothing: charcoal grey hoodie (#3A3A3A), black joggers (#1A1A1A), off-white Air Force 1s (#F0F0F0)
  - Mark: left forearm inner side — add as forearm texture in Krita (dark brownish-grey on skin, angular pattern), import as texture layer in VRoid
- **Checklist:**
  - [ ] Base model created in VRoid
  - [ ] Clothing textured (hoodie, joggers, trainers)
  - [ ] Scar texture applied
  - [ ] Mark texture applied (forearm)
  - [ ] Exported as .vrm
  - [ ] Imported into Blender and tested

---

### 1B. Gabriel Pourfendeur — VRoid Model
- **Software:** VRoid Studio → export .vrm → import to Blender
- **Reference:** `characters/GABRIEL_POURFENDEUR.md`, `references/clothing/gabriel_*`
- **Spec:**
  - Height: 5'9" — slightly shorter, leaner build than Tré
  - Skin: same base as Tré (#8B5E3C range)
  - Hair: cornrows — flat, tight, close to head. Dark (#1A1410). Apply as close-crop hair with tight row texture in VRoid.
  - Eyes: slightly lighter brown than Tré. Neutral, watchful default expression — blinks less than normal.
  - Clothing: dark navy tracksuit top and bottoms (#1A2035), matte black puffer jacket (#1C1C1C)
  - Mark: right forearm inner side — mirror of Tré's (apply same texture, flip horizontally)
- **Checklist:**
  - [ ] Base model created in VRoid
  - [ ] Clothing textured (tracksuit, puffer)
  - [ ] Mark texture applied (forearm — RIGHT arm, mirrored)
  - [ ] Exported as .vrm
  - [ ] Imported into Blender and tested

---

### 1C. Katalina Pourfendeur — VRoid Model
- **Software:** VRoid Studio → export .vrm → import to Blender
- **Spec:**
  - Woman, early 40s. Warm brown skin, same family tone as the brothers. Hair: natural, pulled back loosely — she's home, not going out.
  - Clothing: home clothes — a dark cardigan over a plain top. She was in for the evening.
  - No mark. No power. She is only in Ep1 and flashback (Ep3 brief).
- **Note:** Katalina's screen time in Ep1 is approximately 30 seconds. Keep her build lightweight — no need for high complexity. Make her face warm and human and recognisably the mother of these two men.
- **Checklist:**
  - [ ] Base model created in VRoid
  - [ ] Clothing textured
  - [ ] Exported as .vrm
  - [ ] Imported into Blender and tested

---

### 1D. The Dog Tamer — VRoid + Blender Modification
- **Software:** VRoid Studio (base proportions) → Blender (proportion distortion + cloth sim)
- **Reference:** `characters/DOG_TAMER.md`, `references/clothing/dog_tamer_*`
- **Spec:**
  - Tall — 6'8"+. In VRoid, use max height. In Blender, scale up further.
  - Wrong proportions: slightly too long in the limbs, head slightly too large. Adjust in Blender after import.
  - Face: always in shadow in Ep1 — does not need high face detail. Keep it simple; lighting hides it.
  - Clothing: long dark coat (#1A0A1A). Does not move in wind — cloth simulation disabled or set to no wind influence.
  - No facial animation needed in Ep1. He does not speak.
- **Checklist:**
  - [ ] Base model in VRoid
  - [ ] Proportion adjustments in Blender (height, limb length)
  - [ ] Coat modelled and textured
  - [ ] Still test: coat does not react to wind force fields
  - [ ] Imported and tested in scene

---

## 2. ENVIRONMENTS

### 2A. Peckham Estate Exterior — Night
- **Software:** Blender (modular build)
- **Reference:** `references/locations/peckham_estate_blocks_*`, `references/locations/estate_flat_exterior_*`
- **What to build:**
  - Block face: flat modular wall sections, stacked. Concrete texture from Krita or free texture source.
  - Walkways: horizontal slabs at each floor level, metal railing
  - Stairwell light fitting: a single strip light or bulkhead light above a door. Flickering animation.
  - Ground: wet concrete/tarmac. SSR (screen-space reflection) ON for wet surface reflections.
  - Background block: one additional block further back — does not need interior detail
- **Scope for Ep1:** Only need the following areas:
  - The main entrance walkway (Scene 2 — where Dog Tamer stands)
  - The ground level front (Scene 1 wide shot)
  - Third-floor corridor exterior (brief)
- **Lighting:** Sodium streetlight colour (#B87020 at low intensity). Cold blue ambient fill. One or two lit flat windows.
- **Checklist:**
  - [ ] Block face modelled (modular sections)
  - [ ] Ground modelled and SSR texture applied
  - [ ] Walkway modelled (at least ground-floor and third-floor)
  - [ ] Streetlight asset placed (see Asset 4A)
  - [ ] Stairwell door + light modelled
  - [ ] Test render — confirm sodium light colour and wet reflection

---

### 2B. Third-Floor Corridor — Night
- **Software:** Blender
- **Reference:** `references/locations/estate_flat_exterior_*`
- **What to build:**
  - A long corridor: concrete walls, worn lino or concrete floor, metal doors at intervals
  - Overhead strip lights: dead for most of the corridor. One working at the far stairwell end — flickering.
  - The flat door: slightly ajar (animation on door — starts closed, already open when they arrive)
- **Lighting:** Almost none — just the far stairwell light. One working strip for ambient. Gabriel's phone torch is a separate light object (spot, narrow, warm white, attached to Gabriel's hand in animation).
- **Checklist:**
  - [ ] Corridor geometry (walls, floor, ceiling)
  - [ ] Doors modelled (flat door + corridor doors)
  - [ ] Flickering light animated (keyframed energy value)
  - [ ] Phone torch light object set up

---

### 2C. Katalina's Flat — Kitchen and Hallway
- **Software:** Blender
- **Reference:** `references/locations/estate_flat_interior_*`
- **What to build (kitchen):**
  - Kitchen units along one wall (low + high, simple block geometry)
  - Worktop with a few dressing details: a pot, a tea towel, a mug
  - Overhead strip light (fluorescent — harsh, cold white)
  - Linoleum floor (worn pattern)
  - A small window (dark outside, net curtain)
- **What to build (hallway):**
  - Short hallway: a coat rack with coats on it, a photo or two on the wall (dark frames — no need for photo detail, just the frame shape), a door at the end (open into kitchen)
- **Scope:** The hallway is used in one tracking shot only — it does not need full detailing. Kitchen needs more care — it holds the emotional weight of the episode.
- **Lighting:**
  - Kitchen: strip light overhead (cold white, #E8E0C0). Flickers and goes out at Scene 4 end — animated energy keyframe.
  - Hallway: dark. Only the kitchen light pulling through the doorway at the end.
  - Scene 5 (after light out): only Gabriel's phone glow object active — face down on the lino, emitting soft cool light upward.
- **Checklist:**
  - [ ] Kitchen modelled (units, worktop, details)
  - [ ] Kitchen light modelled + flicker animation
  - [ ] Hallway modelled (coat rack, picture frames, door)
  - [ ] Floor linoleum texture from Krita or free source
  - [ ] Phone glow light object set up (soft, cool, low)
  - [ ] Test render — confirm kitchen fluorescent feel vs Scene 5 darkness

---

## 3. PROPS

### 3A. The Package (Delivery item — weed run)
- **Software:** Blender
- **Spec:** A small wrapped package, cling-film or plastic. Nondescript. Pocket-sized. Referenced in Scene 1 montage hand-off.
- **Detail level:** Low. It is in shot for half a second, close but not detailed. A simple block with a wrap texture.
- **Checklist:**
  - [ ] Modelled
  - [ ] Texture applied (transparent wrap look)

---

### 3B. Folded Bank Notes
- **Software:** Blender or 2D plane with texture
- **Spec:** UK banknotes, folded once. Appear in Tré's hands during the montage count.
- **Detail level:** Low–medium. They are in ECU so need to read as money, but not perfectly photorealistic.
- **Checklist:**
  - [ ] Modelled or flat plane with note texture
  - [ ] Test in ECU shot — reads as money

---

### 3C. Gabriel's Phone
- **Software:** Blender
- **Spec:** Generic smartphone. All-black. Used face-down on the kitchen floor in Scene 5 — only needs to emit a low cool light from the screen edge.
- **Light setup:** Place a very low-intensity area light (cool white, #D0E8FF, intensity ~0.3) at floor level under the phone position.
- **Checklist:**
  - [ ] Phone modelled (simple slab, black)
  - [ ] Floor light object placed and tested

---

## 4. LIGHTING ASSETS

### 4A. Sodium Streetlight
- **Software:** Blender
- **Spec:**
  - Lamp post geometry: simple pole, old concrete or metal. Estate standard.
  - Light type: Point light or Spot light, amber-orange (#B87020), intensity to taste for scene
  - Radius: wide spread, low intensity — sodium lights are not bright
- **Use:** Scene 1 and 2 exteriors. Multiple instances.
- **Checklist:**
  - [ ] Lamp post modelled
  - [ ] Light object configured (colour, intensity, radius)
  - [ ] Test in exterior night scene

---

## 5. VFX ASSETS

### 5A. Shadow Particle System — Tré (Movement Phase)
- **Software:** Blender particle system
- **Reference:** `production/VFX_SPEC.md` — Technique 1, Tré settings
- **Spec:**
  - Particle type: Object (small flattened sphere)
  - Shader: black emission (#000000), alpha falloff at edges
  - Count: 200/sec, Lifetime: 20–30 frames
  - Velocity: 0.5–1.0 m/s
  - Vortex force field: strength 0.3 (creates the coil)
  - Gravity: disabled
- **In Ep1:** Used only in Scene 5 — the first activation. Low intensity. One tendril only.
- **Checklist:**
  - [ ] Particle system built and shaded
  - [ ] Vortex force field configured
  - [ ] Test render: smoke coils upward from forearm emitter
  - [ ] Placed on Tré's forearm in scene

---

### 5B. Shadow Pressure — Gabriel (Dark Air Effect)
- **Software:** Blender — shader-driven plane mesh around hands
- **Reference:** `production/VFX_SPEC.md` — Technique 5
- **Spec:**
  - A low-poly sphere or halo geometry around each fist
  - Shader: Volume Absorption or transparent emission — the darkening effect
  - In Ep1: subtle — the air around his fists just noticeably darker. Not the full eruption effect — that comes in Episode 4.
- **Checklist:**
  - [ ] Hand shadow geometry built
  - [ ] Shader configured (dark, soft-edged)
  - [ ] Test render: fists read as darker than surrounding dark

---

### 5C. Mark Texture — Tré (Left Forearm)
- **Software:** Krita (texture painting) → VRoid (texture import)
- **Reference:** `lore/CLAN_HISTORY.md` — clan symbol description
- **Spec:**
  - Angular clan symbol — knife with angel wings
  - Colour: dark brownish-grey (#4A2E1A) on skin base (#8B5E3C)
  - Slightly raised appearance: achieve via normal map adjustment in Blender after VRoid import if needed
  - Size: covers approximately 1/3 of the inner forearm length
- **Checklist:**
  - [ ] Symbol designed in Krita (rough sketch first, then clean)
  - [ ] Painted onto Tré's forearm texture in Krita
  - [ ] Applied in VRoid texture slot
  - [ ] Test import to Blender: mark visible in EEVEE render

---

### 5D. Mark Texture — Gabriel (Right Forearm)
- **Software:** Krita → VRoid
- **Spec:** Mirror of Tré's mark. Same symbol, horizontally flipped. Right forearm inner side.
- **Checklist:**
  - [ ] Tré's mark texture flipped horizontally in Krita
  - [ ] Applied to Gabriel's right forearm texture in VRoid
  - [ ] Test import to Blender

---

## 6. DEMON ASSETS

### 6A. Demon Hounds (Pack of 8)
- **Software:** Blender (model from scratch — no VRoid equivalent)
- **Reference:** `characters/DOG_TAMER.md` — hound visual spec
- **Spec:**
  - Corpse-like dog form. Wrong proportions — too large, joints at wrong angles
  - Shadow leaking from joints and wound-like gaps in the body
  - Fur: none or vestigial. The body reads as rotting, not living.
  - Shadow leak: particle emitter at each major joint (shoulder, hip, knee) — low count, low velocity. The shadow does not erupt — it seeps.
  - Movement: footsteps deliberately slightly off-beat. Achieved in animation via slightly uneven step timing.
- **Ep1 scope:** Hounds only seen in Scenes 2 and 6 — low to the ground, partially in shadow. Do not need to be fully detailed for Ep1 — the lighting hides them. Build enough that they read as wrong.
- **Checklist:**
  - [ ] One hound model built and tested
  - [ ] Shadow seep particle system applied to joints
  - [ ] Duplicated ×8 (use linked duplicates — edit one, all update)
  - [ ] Test in scene: reads as wrong, not as a normal dog

---

## 7. TOON SHADER SETUP

### 7A. Character Toon Shader
- **Software:** Blender (Shader Editor)
- **Reference:** `VISUAL_STYLE_GUIDE.md` — EEVEE shader section
- **Spec:** Diffuse BSDF → Shader to RGB → ColorRamp (Constant interpolation, 2 stops: shadow at #1A1A1A, light at character skin tone)
- **Apply to:** Tré, Gabriel, Katalina. The Dog Tamer uses a darker variant.
- **Checklist:**
  - [ ] Toon shader built and saved as material preset
  - [ ] Applied to Tré — test render
  - [ ] Applied to Gabriel — test render
  - [ ] Applied to Katalina — test render
  - [ ] Dog Tamer variant (darker light stop) built and applied

---

### 7B. Freestyle Outline
- **Software:** Blender (Render Properties → Freestyle)
- **Reference:** `production/RENDER_SETTINGS.md`
- **Spec:** 2.5px standard, pure black (#000000), Crease + External Contour only
- **Checklist:**
  - [ ] Freestyle enabled in render settings
  - [ ] Line style configured (2.5px, black, crease + contour)
  - [ ] Test render on Tré: outline reads cleanly
  - [ ] Test render on Dog Tamer: outline reads — check against dark coat

---

## ASSET BUILD ORDER

Build in this order — each depends on the previous:

1. **Toon shader + Freestyle** — set this up first. Every character render depends on it.
2. **Tré VRoid model** — protagonist. Needs the most refinement. Build first.
3. **Gabriel VRoid model** — second character. Shares some textures with Tré.
4. **Katalina VRoid model** — simpler. Build third.
5. **Mark textures (Krita)** — design the symbol, paint both mark textures before applying to models.
6. **Kitchen environment** — the most emotionally critical environment. Build before the less important exterior.
7. **Third-floor corridor** — moderate complexity.
8. **Estate exterior** — for Scenes 1 and 2. Build last of the environments as it is the most modular.
9. **Shadow particle system (Tré)** — set up and test before the Scene 5 animation.
10. **Gabriel shadow effect** — simpler than Tré's particles. Build after.
11. **Dog Tamer model** — build after the brothers are done.
12. **Demon hounds** — build last. Only needed in background shots in Ep1.
13. **Props** — the package, notes, phone. Fast builds. Do these alongside environments.

---

## ASSETS NOT NEEDED IN EP1

The following are locked in the series bible but are NOT built for Episode 1:

- Tré's greatsword (first full emergence is Episode 6)
- Gabriel's daggers (first use is Episode 4)
- Underground platform environment (Episode 6)
- Canary Wharf environment (Episode 7)
- Tower Bridge environment (Episodes 11–12)
- Malgris model (Episode 7 first appearance)
- Madeleine model (Episode 2 first contact — may need for Ep2 build)

Do not build these now. Build what Episode 1 needs. Then move to Episode 2 asset list.
