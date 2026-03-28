# SANG NOIR -- VISUAL STYLE GUIDE

> Primary reference: Afro Samurai -- stylish, brutal, heavy contrast, cinematic weight.

---

## Core Visual Philosophy

Every frame must look intentional. No accidental lighting. No generic anime glow. The world is dark, cold, and South London. The power is black. The threat is ancient. The style must carry all of that before a single line of dialogue is spoken.

This guide defines every visual decision for Blender EEVEE. When in doubt, go darker, go higher contrast, go simpler.

---

## Toon Shader Settings (Blender EEVEE)

### Base Setup
- Enable Freestyle (Render Properties > Freestyle): ON
- Render engine: EEVEE
- Bloom: ON (used sparingly -- only for shadow detonation impact frames)
- Ambient Occlusion: ON -- helps sell depth in night scenes
- Screen Space Reflections: ON (for rain-wet streets)

### Toon Shader Node Setup (per character/object)
1. Add a Diffuse BSDF shader
2. Plug colour output into a ColorRamp node
   - Set ColorRamp to: 2 stops, hard edge (no gradient)
   - Stop 1 (pos 0.0): Shadow colour -- darker version of base colour
   - Stop 2 (pos 0.5): Base colour -- flat, unlit version
   - Interpolation: Constant (hard toon edge, not smooth)
3. Plug ColorRamp into Shader to RGB, then Material Output

### Outline (Freestyle)
- Line thickness: 2.5px for characters, 1.5px for environment, 4px for impact frames
- Line colour: Pure black (#000000) always -- never coloured outlines
- Edge types: Crease + External Contour only
- Crease angle: 45 degrees

---

## Colour Palettes

### Characters -- Base Colours

**Tre Pourfendeur**
- Skin: Medium dark brown -- warm undertone (#8B5E3C range)
- Hoodie: Charcoal grey (#3A3A3A)
- Joggers: Black (#1A1A1A)
- Air Force 1s: Off-white (#F0F0F0) with grey sole
- Shadow power: #000000 -- absolute black, no tint
- Scar: Slightly lighter tone than surrounding skin, faint

**Gabriel Pourfendeur**
- Skin: Same base as Tre (brothers)
- Tracksuit: Dark navy (#1A2035) -- NOT black, important distinction
- Puffer jacket: Matte black with dark grey panels (#1C1C1C / #2A2A2A)
- Shadow power: Same black as Tre but applied more aggressively, less controlled

**Malgris (Human Form)**
- Suit: True black (#000000) -- tailored, perfect. Stands out against the shadow-blacks around him because it is the ONLY clean black in a scene
- Pocket square: Dark red (#8B0000) -- his only colour. Used sparingly.
- Skin: Deep brown, immaculate, no visible marks
- Eyes: Dark brown -- nothing supernatural in human form until he chooses

**Malgris (Demon Form)**
- Compressed shadow armour: Layered dark greys and blacks (#0A0A0A, #1A1A1A, #2A2A2A) with cracks emitting deep dark red light (#5C0000)
- Face: Stone-grey cracked surface with red-orange light bleeding through the cracks
- Eyes: Solid dark red (#8B0000), no pupil

**Madeleine Pourfendeur**
- Warrior cloth: Deep charcoal and dark brown layers (#2A2A2A, #3D2B1F)
- Skin: Deep brown, marked with old clan symbols in darker pigment
- Spirit presence: She is slightly desaturated vs the environment -- never fully solid-looking
- Eyes: Pale gold (#BFA060) -- the only warm colour on her

**Dog Tamer**
- Long coat: Black but slightly wrong -- use a slightly purple-shifted black (#1A0A1A)
- Skin: Grey-brown, wrong texture
- Eyes: None visible, face in shadow always
- Silhouette: Too tall. Wrong proportions. Build him to be unsettling at rest.

**Demon Hounds**
- Base: Rotting grey-brown (#2A1F1A) -- decayed animal texture
- Shadow leaks: Pure black smoke erupting from joints, wounds, eye sockets
- Eyes: Two points of dim red (#5C0000), barely visible
- Size: Larger than real dogs -- shoulder height to mid-thigh on a standing adult

---

## Location Colour Moods

### Peckham/Brixton Estates (Episodes 1-4, 8)
- Dominant: Blue-grey cold (#8A9BAD, #5A6B7A tones)
- Light sources: Orange sodium street lights -- used as warm accent against cold environment
- Rain on tarmac: Reflective -- use Screen Space Reflections
- Shadow areas: Near-black -- do not light the dark. Let it be dark.
- Sky: Always overcast. Cloud cover. No visible stars. London at night.

### London Underground (Episodes 5-6)
- Dominant: Harsh fluorescent yellow-white (#F5F0D0)
- Tunnels: Total darkness beyond the platform -- absolute black
- Steel surfaces: Cold grey with fluorescent bounce
- This is the most hostile visual environment -- flat ugly light vs absolute dark tunnel void
- Purpose: Makes the shadow power MORE visible as pure darkness vs the harsh artificial light

### Canary Wharf (Episode 7)
- Glass and steel. Night. Artificial light everywhere.
- Cold blue-white (#D0DCEA) from building interiors
- Malgris is the darkest object in the frame. He stands still in a place where everything else is lit.

### Graveyard (Episode 9)
- Moonlight only. Blue-silver (#B8C8D8)
- Stone: Cold grey, wet
- The one location where the colour is almost beautiful -- and it is where the most painful revelation lands

### Spiritual/Shadow Dimension (Episodes 3, 10)
- All colour drained -- desaturated to near-greyscale
- Background: Floating fragments of clan memory -- pieces of stone, armour, burning scenes from medieval France
- Light: Deep dark red at the edges (#3A0000) -- like a dying fire far away
- Madeleine: Fully visible here. Slightly brighter than everything else. The only solid presence.
- Malgris in Ep10: Shows the brothers this space. He is more powerful here than anywhere. He fills it.

### Tower Bridge (Episodes 11-12)
- Night. Rain.
- The Thames below: Black water, city light reflections
- The bridge: Dark grey stone, orange lamp glow at intervals
- Fight lighting: Shadow power creates pools of absolute black against the wet lit stone
- Malgris demon form reveal: The only moment in the series where something red is used as a PRIMARY light rather than accent

---

## Shadow Power Visual Specification

### Movement Phase (smoke)
- Particle system: Fluid-style, slow-moving black particles
- Behaviour: Coils, wraps around limbs, reaches forward like a tendril
- Duration: 0.5-1 second before impact
- Sound: Near-silence. Small air displacement sound only.
- No glow, no colour. Pure black particles with slight transparency at edges.

### Impact Phase (detonation)
- Geometry: On impact, shadow EXPANDS outward in a burst
- Visual: Quick hard flash of expanding black mass -- like a shadow explosion
- Duration: 3-5 frames (very fast)
- Bloom: ONE frame of very slight bloom on impact frame only, then cut
- Sound: Deep, low concussive hit -- bass-heavy

### Weapon Emergence
- Tre's greatsword: Rises from a dark pool forming on the ground beneath him. Assembles from shadow mass. No glow, no sparkle. Just black metal that was not there and then is.
- Gabriel's dual daggers: Formed from the shadow coiling at his hands -- faster, more violent emergence than Tre's. Less ceremony.
- Weapons in ambient state: Slightly reflective black. The only difference from the shadow is that they have hard edges.

### Cost Visual (extended use)
- As power is held too long: Tre's skin at the edges of the mark shows a slight dark grey spread -- like shadow is bleeding into him
- His eyes: Lose expression. Not blackened -- just empty. Wrong.
- Gabriel in late season: The spread is further. He does not notice. Madeleine does.

---

## Impact Frame Direction

Key hits should hold for 2-4 frames with:
- Exaggerated outline thickness (4-5px)
- High contrast -- everything in the frame either black or near-white
- Motion blur on the striking object, frozen on impact
- Afro Samurai reference: The way that series freezes on impact and lets the linework do the work

Do not use particle explosions of colour. Do not use lens flares. Do not use energy glow.
The violence is black and silent and hits hard. That is the rule.

---

## What to Avoid

- DO NOT use glowing auras (blue, white, gold energy effects -- this is not that kind of anime)
- DO NOT use warm-tinted environments -- South London at night is cold
- DO NOT overlight characters -- shadows on faces are story information
- DO NOT use Cycles renderer -- EEVEE only on this hardware
- DO NOT use bloom on anything except 1-frame shadow impact moments
- DO NOT give Malgris (human form) anything supernatural-looking until his demon reveal
- DO NOT make the demon hounds fast or erratic -- they are wrong, not frantic
