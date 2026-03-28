# SANG NOIR -- RENDER SETTINGS
## Blender EEVEE -- Optimised for Mid-Range GPU

> Target hardware: GTX 1070-3070 / RX 580-6700, 16GB RAM

---

## Core Render Settings

Access via: Properties Panel (right side) > Render Properties (camera icon)

### Engine
- Render Engine: **EEVEE** (NOT Cycles -- Cycles will be 10-20x slower on this hardware)

### Sampling
- Render: **64** (increase to 128 if noise visible. Do not go above 256.)
- Viewport: **16**

### Ambient Occlusion
- Enable: ON, Distance: 0.2m, Factor: 1.0, Bent Normals: OFF

### Bloom
- Enable: **OFF by default**
- Enable ONLY for shots containing shadow detonation impact frames
- When enabled: Threshold 0.8, Intensity 0.05, Radius 2, Clamp 1.0

### Screen Space Reflections
- Enable: ON, Max Roughness: 0.5, Half Resolution Trace: ON

### Motion Blur
- Enable: ON, Position: Center on Frame, Shutter: 0.5, Steps: 2

### Shadows
- Cube Size: **512** (reducing from 1024 saves VRAM significantly)
- Cascade Size: 1024, High Bitdepth: ON, Soft Shadows: ON

### Color Management
- Color Space: sRGB
- Look: **Medium High Contrast** (boosts dramatic contrast of the visual style)
- Exposure: 0.0, Gamma: 1.0

---

## Output Settings

### Resolution
- X: **1920** px, Y: **1080** px, 100%
- (For TikTok renders: X: 1080, Y: 1920)

### Frame Rate
- 24 fps

### Output Path
Set per episode/scene. Example for Episode 1:
- Path: renders/ep01/16x9/ (relative to repo root)
- File format: **PNG** sequence (NOT video)
- PNG colour: **RGBA**, PNG compression: 15%

**Why PNG sequence not video:**
If a render crashes at frame 400, you only re-render from frame 400. Always render to PNG.

---

## Scene Optimisation

### Interior/Estate Flat
- Shadow Cube Size: 256, Particle counts: below 200 active
- Estimated render time per frame: 8-15 seconds

### Exterior Estate/Street
- Shadow Cube Size: 512, Particle counts: below 400 active
- Screen Space Reflections: ON (wet street)
- Estimated render time per frame: 15-25 seconds

### Underground Platform
- Shadow Cube Size: 512, Bloom OFF (unless scripted impact frame)
- Estimated render time per frame: 12-20 seconds

### Combat (VFX-heavy)
- Shadow Cube Size: 512, Bloom ON for impact frames only
- Particle counts: up to 500 total (watch performance)
- Estimated render time per frame: 20-40 seconds
- If frame exceeds 60 seconds: reduce particle count, not sample count

### Spiritual/Shadow Dimension
- Shadow Cube Size: 256, Ambient Occlusion: OFF
- Particles: 50-100 total only
- Estimated render time per frame: 5-10 seconds

---

## Memory Management

If Blender crashes or runs out of VRAM:
1. Reduce particle counts first
2. Then reduce Shadow Cube Size from 512 to 256
3. Close other applications while rendering

**VRAM usage guide:**
- Simple scene with 2 characters: ~2-3GB VRAM
- VFX scene with particles: ~3-5GB VRAM
- Full combat with environment and VFX: ~5-7GB VRAM

If you have GTX 1070 (8GB): Combat scenes should still fit.
If you have GTX 3070 (8GB) or RX 6700 (10-12GB): No issues.

---

## Freestyle Settings

- Enable Freestyle: ON
- Line Thickness Mode: Absolute
- Line Thickness: **2.5px** standard, **4px** for impact frames
- Line colour: #000000
- Edge Types: Crease ON (45 degrees), External Contour ON, all others OFF

---

## Render Time Planning

Episode length: 2-3 minutes at 24fps = 2880-4320 frames per episode.
Average render time per frame: 20 seconds.
Estimated total render time per episode: 16-24 hours.

**Strategy: Render overnight in scene chunks.**
- Name render folders by scene: ep01_scene01/, ep01_scene02/ etc.
- Assemble in DaVinci after all scenes are rendered.

---

## Blender File Management

One .blend file per scene (not one file for the whole episode).

Naming: `ep01_sc01_estate_exterior.blend`, `ep01_sc02_flat_interior.blend`
Store in: `assets/environments/ep01/`

Characters are linked assets -- do not duplicate the character mesh into every scene file.
