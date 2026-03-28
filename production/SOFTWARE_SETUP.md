# SANG NOIR -- SOFTWARE SETUP
## Step-by-Step Installation and Configuration

> This document assumes you are starting from scratch. Follow every step in order.

---

## 1. Blender

**Download:** blender.org -- get the latest stable release (not LTS, not beta)

### Installation
1. Go to blender.org/download
2. Download the Windows installer
3. Run installer, default settings, install to default path
4. Launch Blender

### First Launch Configuration
When Blender opens for the first time, it asks for configuration. Use these settings:
- Select Blender theme: **Dark** (easier on eyes for long sessions)
- Spacebar action: **Search** (lets you search for any function by name -- essential for beginners)
- Click **Next** and **Save**

### Enable Required Add-ons
In Blender: Edit > Preferences > Add-ons

Enable these (use the search box):
- **Import-Export: VRM** -- for VRoid character import. Search "VRM" and enable.
  - If VRM importer does not appear, download it separately from github.com/saturday06/VRM-Addon-for-Blender and install via Add-ons > Install button
- **Rigging: Rigify** -- for character rigging reference. Enable.
- **Mesh: Extra Objects** -- useful for scene building. Enable.

### Render Settings (EEVEE -- set immediately)
With no scene open, set these defaults:
- Properties panel (right side) > Render Properties
- Render Engine: **EEVEE**
- Sampling > Render: **64** (fast enough for most shots, still clean)
- Ambient Occlusion: **ON**
- Bloom: **OFF** (enable per shot only)
- Screen Space Reflections: **ON**
- Motion Blur: **ON**, Steps: **2**

Save these as defaults: File > Defaults > Save Startup File

---

## 2. VRoid Studio

**Download:** vroid.com/en/studio

### Installation
1. Go to vroid.com/en/studio
2. Download the Windows version
3. Extract and run the installer
4. Launch VRoid Studio

### First-Use Notes
- VRoid Studio creates anime-style characters. The output is a .vrm file.
- .vrm files are imported into Blender using the VRM add-on (installed above)
- You sculpt face, body, hair in VRoid. Clothing is layered on using their template system.
- Export settings: When exporting as .vrm, use default export settings. The VRM add-on in Blender will handle the import.

### Workflow for SANG NOIR Characters
1. Build each character in VRoid per their character sheet
2. Export as .vrm
3. Save in `assets/characters/` folder (e.g., `assets/characters/tre_pourfendeur.vrm`)
4. Import into Blender using File > Import > VRM

### Important VRoid Limitation
VRoid is for character creation only. Environments, weapons, VFX are built directly in Blender. Do not try to use VRoid for anything that is not a character.

---

## 3. Krita

**Download:** krita.org

### Installation
1. Go to krita.org/en/download
2. Download the Windows 64-bit installer
3. Install, default settings
4. Launch Krita

### Uses in SANG NOIR
- **Concept art:** Draw character designs before VRoid build to have a reference target
- **Texture painting:** Create custom textures (scar facial texture for Tre, clan mark overlays, brick/concrete wall textures for Blender)
- **Storyboards:** Draw rough panels from storyboard notes

### Krita Setup
- Canvas preset: 1920x1080 px, 72dpi (for storyboards and concept art)
- For textures: 1024x1024 px or 2048x2048 px, 72dpi
- Brush set: Default brushes are sufficient. The "Basic-1" and "Basic-2" round brushes cover most needs.

### Texture Export for Blender
When textures are ready for Blender:
- Export as PNG (File > Export > PNG)
- Save in `assets/characters/` or `assets/environments/` as appropriate
- In Blender: Material node > Image Texture node > load the PNG

---

## 4. DaVinci Resolve

**Download:** blackmagicdesign.com/products/davinciresolve

### Installation
1. Go to the link above
2. Click "DaVinci Resolve" (the free version -- NOT Resolve Studio which costs money)
3. Fill in registration form (they require it -- use any details)
4. Download Windows version
5. Install, default settings
6. Launch DaVinci Resolve

### First Project Setup for SANG NOIR
When you create a new project:
1. File > New Project > Name: "SANG NOIR EP01"
2. Project Settings (gear icon bottom right):
   - Timeline resolution: **1920x1080**
   - Timeline frame rate: **24fps**
   - Playback frame rate: **24fps**
   - Pixel aspect ratio: **Square**
3. Click Save

### TikTok/Reels Setup (separate timeline per episode)
After creating the main YouTube timeline:
1. Right-click in Media Pool > New Timeline > Name: "EP01_TIKTOK"
2. Timeline Settings: 1080x1920, 24fps
3. The TikTok cut is a separate edit. You will re-edit key shots from the main timeline here.

### Uses in SANG NOIR
- Import Blender renders (image sequences) and assemble into episodes
- Add music (from `assets/music/`)
- Add SFX (from `assets/audio/`)
- Colour grading -- apply consistent colour look per location (blue-cold for estate, harsh yellow for Underground, etc.)
- Export final video

---

## 5. Audacity

**Download:** audacityteam.org

### Installation
1. Go to audacityteam.org/download
2. Download Windows installer
3. Install, default settings
4. Launch Audacity

### Uses in SANG NOIR
- Create the Malgris leitmotif (piano note + bass fade -- see SOUNDTRACK_DIRECTION.md)
- Record and edit any custom SFX
- Process downloaded sounds (cut, fade, pitch shift)
- Export SFX as .WAV files to `assets/audio/`

### Audacity Setup
- Edit > Preferences > Quality:
  - Default Sample Rate: **44100 Hz**
  - Default Sample Format: **32-bit float**

---

## 6. Suno

**Access:** suno.com (web-based -- no download)

### Setup
1. Go to suno.com
2. Create a free account
3. Sign in

### Uses in SANG NOIR
- Generate all background music tracks
- Use the prompt directions from SOUNDTRACK_DIRECTION.md
- Download generated tracks as MP3
- Save in `assets/music/` with descriptive names

### Workflow
1. Write prompt from SOUNDTRACK_DIRECTION.md
2. Generate 3-5 variations
3. Download the best 1-2 per cue type
4. Name files clearly: `combat_standard_v1.mp3`, `estate_night_ambient_v1.mp3` etc.
5. Import into DaVinci Resolve as needed

---

## 7. ElevenLabs (Phase 2 only)

**Access:** elevenlabs.io (web-based)

Do not set up ElevenLabs until the visuals are complete for Episode 1. Voice is added in Phase 2 of production. Creating voices before the animation is done means you may need to re-record.

When ready:
1. Create a free account at elevenlabs.io
2. The free tier gives limited characters per month -- plan voice sessions accordingly
3. Character voices should each be assigned a consistent ElevenLabs voice clone
4. Export lines as .MP3, name them `ep01_tre_line01.mp3` etc., save in `assets/audio/voices/`

---

## Software Order of Use

The correct order to use these tools in production:

1. **Krita** -- concept art and character reference drawings
2. **VRoid Studio** -- build character models from concept art
3. **Krita** -- texture work (scars, marks, environment textures)
4. **Blender** -- import characters, build environments, VFX, animate, render
5. **Audacity** -- create SFX
6. **Suno** -- generate music
7. **DaVinci Resolve** -- assemble renders, add audio, grade, export
8. **ElevenLabs** -- voice lines (Phase 2)
