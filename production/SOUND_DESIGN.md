# SANG NOIR -- SOUND DESIGN
## SFX Specification

> This document covers SFX and ambient design.
> For music direction, see SOUNDTRACK_DIRECTION.md.

---

## Core Principle

In SANG NOIR, SFX often does more work than music -- especially in action sequences where music drops. The silence around a hit is as designed as the hit itself.

---

## Shadow Power SFX

### Activation (both brothers)
- Sound: Very slight air displacement. A breath pulled inward. No bass, no dramatic swell.
- Duration: 0.5-1 second
- Audacity method: Record near-silence with slight air movement. Apply gentle low-pass filter. Normalize to -12dB.

### Shadow Smoke Phase (movement)
- Sound: Near-inaudible electrical hiss at very low volume (-40dB). Audience does not consciously hear it.
- Purpose: Creates subliminal wrongness during shadow use.

### Shadow Detonation Impact
- Sound: Low, bass-heavy concussive THUD. Not a crack, not a boom. Felt, not heard.
- Dominant frequency: 60-120Hz range
- Duration: 0.1 second impact + 0.2 second fade
- Reverb: Very short and tight. The energy absorbs, not bounces.
- Audacity method: Layer 80Hz sine wave burst (0.3 sec) under a short percussive thud transient.
- Free source: freesound.org -- search "low impact", "concussive hit", "bass thud"

### Tre's Greatsword -- Emergence
- Sound: Deep resonant scrape (shadow mass becoming metal) + sustained low hum while active
- Duration of emergence: 1-1.5 seconds

### Gabriel's Dual Daggers -- Emergence
- Sound: Two rapid metallic hisses + two short sharp clicks (hilts forming)
- Duration: 0.5 seconds total (much faster than Tre's sword, slightly higher pitch)

### Weapon Impact on Demon
- Against demon flesh: Wet tearing sound with subharmonic undertone
- Against demon armour: Short sharp metallic concussion (not a ring)

---

## Dog Tamer SFX

### Ambient Frequency Effect
When Dog Tamer enters a scene: apply notch filter cutting 4kHz-8kHz from the ambient audio.
Do this in DaVinci EQ on the ambient room tone clip. Activation: on frame he enters.
Result: scene feels slightly wrong before the audience knows why.

### Movement
- Footsteps: Attenuated 60% from normal. Near-silent for his size.
- Coat: Zero fabric sound. No rustling.

### Demon Hounds
- Footsteps: Padded, muffled. Heavy low-pass filter. Wrong rhythm.
  - Audacity method: Record 4 even footfalls. Nudge each 2-3% off the beat. Export.
- Breathing: Slow exhales only. 4-second intervals. Slightly wet. Low pitch.
- Attack: **Silence before contact.** No warning sound. Then impact.
- Impact: Same low concussive thud as shadow detonation -- without the bass sine tone.

---

## Malgris SFX

### Human Form
- Footsteps: Perfect. Normal. Full human sound. No wrongness. That is the point.
- Voice (Phase 2): ElevenLabs. No processing. Sounds exactly human.

### Demon Form Transition (Episode 11)
- Suit fragmenting: Sequence of small precise sounds. Not a tear. Like cloth being folded wrong.
- Armour assembling: Deep grinding compression sound. Low. Sustained 3-5 seconds.
- First step in demon form: Ground under pressure. Concrete impact doubled.

### Demon Form Combat
- Movement: Heavy. Every step significant. Double the ground impact of large human.
- Attacks: Lower frequency than brothers' shadow. More sustained. Pressure, not impact.

---

## Location Ambient Design

### Peckham Estate -- Night (all episodes here)
Layer simultaneously:
1. Distant traffic -- low, constant, never foreground
2. Sound bleed from other flats -- indistinct, low
3. Rain on concrete -- medium, consistent
4. Wind on walkway -- gentle hiss
5. Distant siren -- once per 2-3 minutes, not timed to action

### London Underground (empty platform)
1. Ventilation hum -- constant, low, slight pulse
2. Distant train in other tunnel -- once per 90 seconds, very muffled
3. Tannoy feedback, distant -- barely audible
4. Footsteps: Add short reverb (0.3 second decay, tile character) to every footstep here

### Canary Wharf -- Night
1. Channelled wind between buildings -- slightly whistling
2. Distant water feature -- very low
3. Air conditioning hum from towers -- constant medium-low

### Spiritual/Shadow Dimension
1. Very low sub-bass hum (30-40Hz) -- felt more than heard
2. Occasional muffled real-world bleed -- dreamlike
3. No natural environment sounds

### Tower Bridge -- Night, Rain
1. Heavy rain on stone -- prominent
2. Thames wind -- strong, directional
3. Water on metal bridge structure -- low hum
4. City ambient -- present but far

---

## Free SFX Sources

- freesound.org -- filter by CC0 licence for commercial use
- zapsplat.com -- free with account
- sonniss.com/gameaudiogdc -- annual free game audio pack

Build a source library at assets/audio/source_library/ with raw downloaded sounds before processing.
