# SANG NOIR -- WORLD BUILDING

---

## South London as a Character

South London is not backdrop. It is a presence. The concrete, the rain, the sodium light on wet tarmac, the tube lines running underground through the dark -- this is all load-bearing. The visual language of Peckham, Brixton, and the Underground carries the tone before any demon appears.

The key principle: London does not react to the supernatural. The city has always had darkness under it. It does not notice.

---

## Locations

### Peckham Estate (Episodes 1-4)

**What it is:**
High-rise council estate. Flat concrete walkways exposed to weather. Stairwells poorly lit. Metal railings, painted over many times. Individual flat doors close together. Small windows. The kind of place where you can hear neighbours through the walls.

**Atmosphere:**
Sodium orange lights that do not reach the corners. Wet concrete. Long shots down walkways at night show nothing but orange pools of light with absolute dark between them. The Dog Tamer first appears at the far end of one of these walkways. He is at the edge of a light pool. He does not move into the light.

**Key spaces:**
- The brothers' flat: Second or third floor. Small lounge, narrow kitchen. The mother's presence is in every object. After Episode 1, the flat is a crime scene that they go back to anyway.
- The walkway: Where the mother is killed. Open air. Rain. The estate is quiet because it is 2am.
- The courtyard below: Where Gabriel goes after Episode 1. Sits on a bench in the rain. Does not move for a long time.

**Blender notes:**
Build as modular components -- walkway section, stairwell, flat interior. Repeat with variation. London estates are modular by design. EEVEE rain achieved via particle system falling from above with wet material on ground plane. Orange sodium lights: Area lights, warm orange (#FF8C30), low height, cast hard shadows.

---

### Brixton Back Streets (Episodes 4, 8)

**What it is:**
Secondary streets and alleys behind the main Brixton drag. Under the railway arches. Industrial units closed at night. Some through-roads with residences above. Old brick, graffiti, a sense that these streets are for people who know where they are going.

**Atmosphere:**
The Dog Tamer fight (Ep4) happens in a stretch under railway arches. This is deliberate: the arches create natural frames. The Dog Tamer can be at the far arch and the brothers at the near arch and the fight happens in the tunnel of space between. Brick, darkness, no civilian witnesses.

**The Brixton Burns fight (Ep8):**
A different stretch -- more residential. The Second Champion is not hiding. The wake of this fight leaves marks on buildings. Gabriel does not stop when the Champion is down. That is the scene.

**Blender notes:**
Victorian brick arches. Build one arch span as modular unit. Stack and repeat. Brick texture from Krita or free texture library. Under-arch lighting: one or two working lights, several broken ones. The fight moves through the lit and unlit sections deliberately.

---

### London Underground (Episodes 5-6)

**What it is:**
Deep-level Tube station. Not a modern station -- one of the old ones. Low ceilings, curved tiled walls, narrow platforms. The specific visual reference is stations like Stockwell or Clapham Common on the Victoria line.

**Atmosphere:**
The platform is empty because it is past service hours. The only light is the harsh fluorescent strips that run the platform ceiling. Beyond the platform edge: total darkness. The tunnels are absolute black. Sounds carry differently here -- every footstep echoes but the dark tunnels swallow sounds that go too far.

**Why this location works for Episode 6:**
The First Champion is comfortable in the tunnels -- comes through them. Tre is not comfortable underground. The fight happens in the lit zone (platform) and the dark zone (tunnel) and the contrast between them is the visual language. Shadow power is most visible in the lit zone -- pure black against the harsh white light. In the tunnels it disappears.

**Blender notes:**
Tube tunnel is a cylinder with the top half and platform side opened out. Tile texture (curved tiled panels -- the classic London Underground look) in Krita. Fluorescent strips: Emission material along ceiling. The dark tunnel beyond: Do not model it. Just let it be dark. Ray distance set so nothing renders past 10-15m into the tunnel mouth.

---

### Canary Wharf (Episode 7)

**What it is:**
Glass and steel financial district. At night it is almost empty of people. Corporate towers lit from within. Fountain plazas, wide paved areas that feel too clean for the city around them.

**Atmosphere:**
Malgris walks Canary Wharf in Episode 7. He is the most composed person in any space he occupies. Here he walks through a place built from the idea that money is civilisation -- and he is older than money, older than whatever this district thinks civilisation is. He is not impressed. He is not disdainful. He simply is here.

The moral choice between brothers involves a civilian. Canary Wharf is chosen because it represents something the brothers have no connection to -- wealth, glass, distance from Peckham. The choice being forced here makes it harder. There is no home-ground advantage.

**Blender notes:**
Glass tower face: reflective glass material, lit from inside (emission material on inside faces). Ground: polished stone, highly reflective. Night sky reflected in the glass. Keep geometry simple -- this is background architecture, not the focus.

---

### Graveyard (Episode 9)

**What it is:**
Old South London churchyard. Victorian headstones, some tilted. Old trees, dense. Not a modern cemetery -- old, crowded, with history.

**Atmosphere:**
The mother is buried here. The father's truth is revealed here -- not a grave visit scene but a conversation between the brothers at the grave that becomes a reckoning. Moonlight only. The graveyard is the quietest location in the series. The scene before the storm.

**Blender notes:**
Old stone headstones as instances on a ground plane -- vary scale and tilt slightly per instance. Tree canopy: particle system hair objects (simplified leaf clusters) for performance. Moonlight: Single directional light, blue-silver, low angle, hard shadows.

---

### Tower Bridge (Episodes 11-12)

**What it is:**
The most iconic structure in London. At night. The final battle location is earned -- the brothers have come from the back streets of Peckham to the centre of the city.

**Atmosphere:**
Rain. The Thames visible below. The bridge's stone walkways and towers. The final battle starts on the road surface between the towers and moves upward. Malgris transforms on the bridge. His demon form is revealed when he decides the fight has earned it -- he respects them enough to stop holding back.

**Key visuals:**
- The brothers, back to back, surrounded by the last remaining champions before Malgris
- Malgris transforming: the black suit fragments. Underneath is not flesh -- it is compressed shadow armour assembling around him room.
- Madeleine manifesting physically for the first and only time -- she steps out of Tre's mark and into the world
- The Thames below, black water, the city spread out behind the final fight

**Blender notes:**
Tower Bridge Gothic towers do not need full interior detail -- exterior silhouette is what matters. The road deck: stone-grey with wet reflections, interrupted by lamp posts with orange-amber globes. Build only what the camera sees. Camera sees: road surface forward to mid-towers, sky above, Thames below from rail if needed.

---

## The Shadow Dimension

Not a separate world. The dark face of this one.

When brothers access the shadow dimension:
- Same locations, identical geometry -- but all colour drained to near-greyscale
- Floating objects: fragments of stone, pieces of armour, burning embers that never go out -- echoes of the France massacre encoded in the bloodline memory
- Sound: Distant, muffled, like underwater
- Madeleine is HERE fully. She is more present here than in the physical world.
- Time is different -- a few seconds in the real world can be a longer conversation here

Visual spec in Blender:
- Desaturation post-process: DaVinci Resolve colour grade -- pull saturation to near-zero, keep slight warm tint on Madeleine only
- Floating fragments: Particle system emitter above, slow fall, loop
- Depth of field: More aggressive than physical world scenes -- edges soft, centre sharp

---

## The Demon Hierarchy

**Malgris** -- Warlord. Ancient. Operates through proxies for most of human history. Has been building toward this for centuries. His presence in London now, in person, is unprecedented. He does not usually need to come himself.

**Demon Generals** -- The Dog Tamer is one. There are others. Each commands a domain (hounds, tunnels, specific territories). Each has a different presentation of wrong-humanity.

**Champions** -- High-level combat demons. Sent by Malgris to test the brothers. Each is a different kind of threat, forcing the brothers to develop a different response.

**Standard demons** -- Exist at weak-point locations (tunnels, abandoned places). Not major narrative figures in Season 1.

---

## The Pourfendeur Bloodline in London

The bloodline came to London generations back -- not as fugitives, not knowingly. The family settled, married into London, became South London. The shadow inheritance went dormant. No one in the family knew they carried it until Remy -- who discovered it through a near-death encounter in his youth.

Remy hunted alone. He never told the boys what they were. His death was not abandonment -- it was the last protective act of someone who kept the danger pointed at himself for as long as he could.

There is at least one other Pourfendeur blood survivor. Unknown location. Unknown to the brothers. This will be a Season 2 thread. Do not introduce or hint in Season 1 -- let the brothers believe they are the last.

---

## What London Knows (Nothing)

The city does not know about demons. Individual witnesses remember events as random crime, accidents, something they do not want to think about. The silence is not enforced by anyone -- it is just how humans process things that do not fit.

The police are background. They appear in Episode 1 context after the mother's death. They do not feature in the supernatural story. Their investigation continues off-screen and has no effect on the brothers' world.
