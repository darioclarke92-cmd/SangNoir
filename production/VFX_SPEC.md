# SANG NOIR -- VFX SPECIFICATION
## Shadow Power Build in Blender EEVEE

---

## Overview

Shadow power is the signature visual of SANG NOIR. It must be handled consistently across all episodes. This document locks the technical approach before any scene is built.

The shadow power has two distinct phases with different technical builds:
1. **Movement phase (smoke)** -- particles and shader
2. **Impact phase (detonation)** -- geometry and shader burst

Both must work in EEVEE on a mid-range GPU (GTX 1070-3070 / RX 580-6700).

---

## Decision: EEVEE-Compatible Approach

Cycles simulation would produce better smoke. On this hardware, Cycles is too slow for a production pipeline. EEVEE cannot simulate real volumetric smoke well. The decision:

**Use shader-driven particle systems, not volumetric simulation.**

This is how most anime-style VFX handles black energy/shadow effects -- it is not physically accurate to real smoke, it is stylised. This works in our favour: SANG NOIR's shadow should look stylised, not like real smoke simulation.

---

## Technique 1: Shadow Movement (Smoke Phase)

### Approach: Particle System + Shader

**Setup:**
1. Create a particle system emitter object -- place it at the character's mark/hand/foot as needed
2. Particle type: Object (use a small flattened sphere as the particle mesh)
3. Particle shader: Emission material, pure black (#000000), slight alpha falloff at edges
   - Node setup: Emission colour (#000000) + Transparent mix based on particle age (fades out at end of life)
4. Particle settings:
   - Count: 200-400 per active second (adjust per scene -- less in controlled Tre, more in raw Gabriel)
   - Lifetime: 20-30 frames
   - Velocity: Low -- 0.5-1.5 m/s outward
   - Physics: Newtonian, gravity disabled (shadow does not fall)
   - Size: 0.05-0.15m, randomised per particle

**For the coiling/wrapping motion:**
- Add a Force Field (Vortex type) near the emitter
- Low strength -- creates the coiling behaviour without chaos
- Different vortex settings for Tre (tighter, more controlled) vs Gabriel (looser, more random)

**Colour:** Pure black (#000000). No tint. No blue-black or grey-black -- absolute black.

**Transparency:** Particles are slightly transparent at edges (alpha ~0.7 at edge). This prevents them looking like solid spheres and gives the smoke quality.

---

## Technique 2: Shadow Detonation (Impact Phase)

### Approach: Geometry Nodes + Shader

**Setup:**
1. Create a sphere at the impact point
2. Apply a Geometry Nodes modifier:
   - On impact frame: scale = 0
   - Over 3-5 frames: scale expands rapidly (use a curve modifier for ease-out)
   - On final frame: sphere visible at maximum scale
   - Frame after: visibility off
3. Shader: Black emission material with slight roughness variation at surface
4. Freestyle outline: Thicker (4-5px) on the detonation sphere -- makes it read as impact frame

**The "burst" visual:**
- In addition to the expanding sphere, add 8-12 flattened plane instances emitting outward from impact point (like a manga impact pattern in 3D)
- These planes: narrow, black, expand outward at high speed over 2-3 frames
- Same black shader as the sphere

**Duration:** 3-5 frames total. Very fast. The impact reads before it is consciously processed.

**Post-process in DaVinci:** Add a 1-frame bloom burst on the impact frame only. Desaturate to pure white then immediately fade. This sells the concussive weight without using persistent bloom.

---

## Technique 3: Weapon Emergence

### Tre's Greatsword
1. Model the greatsword in Blender (separate asset -- see ASSET_LIST for ep01)
2. Initially invisible (alpha = 0)
3. Apply an emergence animation:
   - Frame 1-5: Shadow particle system emits upward from ground near Tre's feet (same particle setup as movement phase)
   - Frame 5-15: Shadow mass "assembles" -- use shape keys on the sword model, expanding from a tight mass shape to full sword shape
   - Frame 15: Full sword visible, particles cease
4. Shader: Matte black material on sword. Slightly more reflective than the shadow particles -- gives it the hard-edge quality vs the smoke quality.

### Gabriel's Dual Daggers
Same approach but:
- Emerge from hands not ground
- 5-8 frames total (faster, more violent than Tre's)
- Two simultaneous emitters (left and right hand)

---

## Technique 4: Cost Visual (Extended Use)

### The Mark Spread
- As power is held too long, add a secondary particle emitter at the mark location
- Particles flow from the mark UP the arm (against gravity setting) -- very slow
- Low count, small size -- subtle
- This is a Blender material animation, not a separate VFX layer

### Eye Effect (Tre's hollowness)
- Post-process in DaVinci Resolve: very slight desaturation applied to close-up shots of Tre's face after extended power use
- Not visible in wide shots -- only in close-ups
- Duration: 3-5 seconds per occurrence. Then normal.

---

## Technique 5: Gabriel's Power Difference

Gabriel's shadow power is the same black as Tre's -- same colour, same particle shader. The DIFFERENCE is behavioural:

| Parameter | Tre | Gabriel |
|---|---|---|
| Vortex force field strength | Lower (0.3) | Higher (1.2) |
| Particle count per second | 200 | 500 |
| Particle velocity | 0.5-1.0 m/s | 2.0-4.0 m/s |
| Coil behaviour | Directed (toward target) | Erupting (outward, uncontained) |
| Detonation sphere scale | 1.0x | 1.6x |
| Detonation duration | 3-5 frames | 3 frames (faster, more violent) |
| Dagger emergence speed | -- | 40% faster than Tre's sword |
| Idle emission (late season) | None | From Ep8+: low-level smoke from mark at rest |

The visual result: Tre's shadow is a weapon he holds. Gabriel's shadow is a force he barely contains. By Episode 8, Gabriel's shadow starts leaking when he is not actively fighting -- the power is bleeding into his resting state. He does not notice. Tré does.

---

## EEVEE Performance Notes

**For GTX 1070-3070:**
- Particle count limit: Keep below 500 total active particles per frame across ALL emitters
- Shadow/visibility in EEVEE: Use Shadow mode = None on particle objects (they are shadow, they should not cast additional shadows)
- Render time target: Under 30 seconds per frame for particle-heavy shots
- If render time exceeds target: Reduce particle lifetime first, then count

**EEVEE settings for VFX work:**
- Ambient Occlusion: ON (needed for ground shadow under particle masses)
- Bloom: OFF by default. Enable ONLY for impact frame shots (render separately, composite in DaVinci).
- Motion blur: ON, steps = 2 (minimal but present -- helps sell fast impacts)

---

## VFX Asset Checklist

Before Episode 1 build starts, the following VFX assets must be created and tested:

- [ ] Shadow particle system (Tre version) -- test render 5 seconds
- [ ] Shadow particle system (Gabriel version) -- test render 5 seconds
- [ ] Impact detonation system -- test render single hit
- [ ] Greatsword model
- [ ] Greatsword emergence animation
- [ ] Dual dagger models (x2)
- [ ] Dagger emergence animation
- [ ] Mark spread overlay (Tre right forearm) -- for Ep6+ use
- [ ] Demon hound shadow leak particles -- reuse shadow particle system, adjusted

---

## References to Collect

Place in `references/vfx/`:
- Slow-motion black smoke footage -- search YouTube "slow motion black smoke"
- Ink in water footage -- search YouTube "ink water slow motion"
- Shadow silhouette photography -- reference for Blender lighting
- Afro Samurai energy effects screenshots -- primary style reference
- Manga impact frame scans -- for detonation burst pattern reference
