# SANG NOIR -- SOFTWARE SETUP
## Step-by-Step Beginner Guides

> You have never used most of this software. That is fine. This document tells you exactly what to click, in order, with no assumed knowledge. Read each section fully before touching the software.
>
> No coding. No command lines. Every step is clicks and menus only.
>
> Software order: Blender first. Everything else after. Blender is the core tool — everything feeds into it or out of it.

---

## SOFTWARE ORDER OF USE

Before reading the individual guides, understand how all of these tools connect:

1. **Krita** — draw the clan symbol and character concept art first (before building anything)
2. **VRoid Studio** — build character models using concept art as reference
3. **Krita** — paint custom textures (mark, scar, environment textures)
4. **Blender** — the main production tool: import characters, build environments, apply shaders, animate, render
5. **Audacity** — build and export SFX
6. **Suno** — generate music tracks
7. **DaVinci Resolve** — assemble everything: rendered images + audio + music = final episode video
8. **ElevenLabs** — voice lines only (Phase 2, after visuals are complete)

---

---

# SECTION 1 — BLENDER

**Download:** blender.org → Download → Latest stable release (not LTS, not beta) → Windows Installer

---

## 1.1 Installation

1. Go to **blender.org/download**
2. Click the big download button — it defaults to Windows
3. Run the installer
4. Click through all defaults — do not change the install path
5. Launch Blender from the Start Menu or desktop shortcut

---

## 1.2 First Launch — Interface Overview

When Blender opens you will see a lot of panels. Here is what each area does:

```
┌─────────────────────────────────────────────────────┐
│  TOP BAR — menus (File, Edit, Render, Window)       │
├───────────────────────┬─────────────────────────────┤
│                       │  PROPERTIES PANEL           │
│   3D VIEWPORT         │  (right side — tabs for     │
│   (the main window    │  render, scene, object,     │
│   where you see and   │  material settings etc.)    │
│   navigate your scene)│                             │
│                       ├─────────────────────────────┤
│                       │  OUTLINER                   │
│                       │  (top right — lists every   │
│                       │  object in your scene)      │
├───────────────────────┴─────────────────────────────┤
│  TIMELINE (bottom — animation frames)               │
└─────────────────────────────────────────────────────┘
```

**The Properties Panel tabs (right side, icon column):**
Going from top to bottom — render camera icon, output icon, scene icon, world icon, object icon, modifier icon, particles icon, physics icon, constraints icon, data icon, material icon, texture icon. You will use render, material, and modifier the most.

---

## 1.3 Navigating the 3D Viewport

You must know these before anything else. Practice until they are automatic:

| Action | How |
|---|---|
| Rotate the view | Hold **Middle Mouse Button** and drag |
| Zoom in/out | **Scroll wheel** |
| Pan (slide) the view | Hold **Shift + Middle Mouse Button** and drag |
| Front view | Press **Numpad 1** |
| Side view | Press **Numpad 3** |
| Top view | Press **Numpad 7** |
| Camera view | Press **Numpad 0** |
| Focus on selected object | Press **Numpad .** (dot) |

> **If you have no numpad:** Go to Edit > Preferences > Input > tick "Emulate Numpad" — this maps the number row to numpad functions.

---

## 1.4 Selecting and Moving Objects

| Action | How |
|---|---|
| Select an object | **Left click** on it |
| Select all | Press **A** |
| Deselect all | Press **Alt + A** |
| Delete selected | Press **X**, then confirm |
| Move selected object | Press **G** (grab), move mouse, left click to confirm |
| Rotate selected | Press **R**, move mouse, left click to confirm |
| Scale selected | Press **S**, move mouse, left click to confirm |
| Move on one axis only | Press **G** then **X**, **Y**, or **Z** to lock to that axis |
| Undo | **Ctrl + Z** |

---

## 1.5 First Launch Configuration

When Blender opens for the very first time, a splash screen appears with configuration options:

- **Select a theme:** Choose **Dark**
- **Spacebar action:** Choose **Search**
- Click **Save New Settings**

If you missed this or want to change it later: **Edit > Preferences > Keymap** for spacebar, **Edit > Preferences > Themes** for theme.

---

## 1.6 Install the VRM Add-on (for VRoid characters)

Blender does not natively open VRoid (.vrm) files. You need an add-on:

**Step 1 — Download the add-on:**
1. Go to: **github.com/saturday06/VRM-Addon-for-Blender**
2. Click the green **Code** button → **Download ZIP**
3. Save the zip file somewhere you can find it (Desktop is fine)

**Step 2 — Install in Blender:**
1. In Blender: **Edit > Preferences**
2. Click **Add-ons** in the left column
3. Click the **Install** button (top right of the add-ons panel)
4. Navigate to the ZIP file you downloaded, select it, click **Install Add-on**
5. In the search box, type **VRM**
6. You will see "Import-Export: VRM format" — tick the checkbox to enable it
7. Close Preferences

**Verify it worked:**
- Go to **File > Import** — you should see **VRM (.vrm)** in the list

---

## 1.7 Set Render Engine to EEVEE

Every new scene must have EEVEE set as the render engine. Do this before anything else in any new file:

1. Look at the **Properties Panel** on the right side
2. Click the **camera icon** tab (first tab at the top — Render Properties)
3. At the top you'll see **Render Engine** with a dropdown
4. Click the dropdown and select **EEVEE**

---

## 1.8 EEVEE Render Settings — Set These Once

With EEVEE selected in Render Properties, scroll down and set:

**Sampling section:**
- Render: **64**
- Viewport: **16**

**Ambient Occlusion section:**
- Click the checkbox to turn it **ON**
- Distance: **0.2m**
- Factor: **1.0**

**Bloom section:**
- Leave **OFF** (default) — you will turn this on per-shot only when needed

**Screen Space Reflections section:**
- Turn **ON** — needed for wet street reflections

**Motion Blur section:**
- Turn **ON**
- Shutter: **0.5**
- Steps: **2**

**Save these as your default startup:**
- **File > Defaults > Save Startup File**
- Click **Save Startup File** in the confirmation box

Now every new Blender file will open with these settings already applied.

---

## 1.9 Set Up the Output Settings (Where Renders Save)

Before rendering anything, tell Blender where to save and in what format:

1. In Properties Panel — click the **printer icon** tab (Output Properties)
2. **Resolution:** X = 1920, Y = 1080
3. **Frame Rate:** 24
4. **Output section:**
   - Click the folder icon next to the path box
   - Navigate to your `renders/ep01/` folder inside the Anime project
   - Select it
5. **File Format:** Change from PNG to... actually keep it **PNG**
6. **Colour** (under the format): **RGBA**
7. **Compression:** 15

> **Why PNG sequences and not a video file:** If Blender crashes mid-render, you lose nothing — only re-render from where it stopped. Always render to PNG sequences. DaVinci Resolve assembles them into a video later.

---

## 1.10 Understanding Scenes and Files

**One .blend file per scene.** Do not put the entire episode in one file. It will become too heavy and too slow.

Name your files: `ep01_sc01_estate_exterior.blend`, `ep01_sc04_flat_kitchen.blend`

Store them in: `assets/environments/ep01/`

---

## 1.11 Building a Simple Object (How Modelling Works)

Everything in Blender starts as a primitive shape that you modify. Here is how:

**Add an object:**
- In the 3D Viewport, press **Shift + A**
- A menu appears: Mesh > Cube, Sphere, Plane, Cylinder, Cone, etc.
- Click one to add it to the scene

**Switch to Edit Mode to change its shape:**
- With the object selected, press **Tab** to toggle between Object Mode and Edit Mode
- In Edit Mode you can move, scale, and shape individual vertices, edges, and faces

**The three selection modes in Edit Mode (top left of viewport):**
- **Vertex mode** (dot icon): select individual points
- **Edge mode** (line icon): select edges
- **Face mode** (square icon): select flat surfaces

**Key modelling actions in Edit Mode:**
- **Extrude** (E): pull a face outward to extend the shape — how you make walls, floors, ledges
- **Loop Cut** (Ctrl + R): add a new edge loop around a shape — for detail
- **Scale on one axis** (S then X/Y/Z): resize in one direction only — for walls, flat surfaces
- **Press Tab** to return to Object Mode when done

---

## 1.12 Setting Up Materials and the Toon Shader

Every object in Blender needs a material — this tells Blender what colour and surface properties the object has.

**Access the Material tab:**
1. Select the object
2. In the Properties Panel, click the **sphere icon** (Material Properties)
3. Click **New** to add a new material
4. A basic material is created

**To actually build the toon shader, you need the Shader Editor:**
1. Your screen shows the 3D Viewport by default
2. At the top-left corner of the 3D Viewport, there is a small **icon that looks like a grid/mesh**
3. Click that icon — a dropdown of editor types appears
4. Select **Shader Editor**
5. The 3D Viewport changes to the Shader Editor

**You will now see two boxes connected by a line — these are "nodes":**
- Left node: **Principled BSDF** (the default shader)
- Right node: **Material Output**

---

## 1.13 Building the SANG NOIR Toon Shader (Step by Step)

This shader gives you the hard two-tone anime shading (dark shadow, flat lit areas, no gradients).

**Step 1 — Delete the Principled BSDF:**
1. Click on the Principled BSDF node to select it (it gets an orange outline)
2. Press **X** to delete it

**Step 2 — Add a Diffuse BSDF node:**
1. Press **Shift + A** in the Shader Editor (same as adding objects in 3D view)
2. Go to **Shader > Diffuse BSDF**
3. It appears in the editor — click to place it

**Step 3 — Add a Shader to RGB node:**
1. Press **Shift + A > Converter > Shader to RGB**
2. Place it to the right of the Diffuse BSDF

**Step 4 — Add a ColorRamp node:**
1. Press **Shift + A > Converter > ColorRamp**
2. Place it to the right of the Shader to RGB

**Step 5 — Connect the nodes:**
1. Click and drag from the **BSDF dot** on the right side of the Diffuse BSDF
2. Drag it to the **Shader dot** on the left side of Shader to RGB
3. Click and drag from the **Color dot** on the right side of Shader to RGB
4. Drag it to the **Fac dot** on the left side of ColorRamp
5. Click and drag from the **Color dot** on the right side of ColorRamp
6. Drag it to the **Surface dot** on the Material Output

**Step 6 — Configure the ColorRamp:**
1. Click the ColorRamp node to select it
2. You will see a gradient bar with two small markers (triangles) at each end
3. Click the **Interpolation dropdown** (says "Linear") — change it to **Constant**
4. Click the **left marker** (dark end, position 0.0):
   - Below the gradient, check the colour box — set to very dark grey: **#1A1A1A**
5. Click the **right marker** (light end):
   - Drag it left to position **0.5**
   - Set colour to the character's skin/clothing base colour (e.g., #3A3A3A for Tré's hoodie)

**Step 7 — Set the Diffuse BSDF base colour:**
1. Click the Diffuse BSDF node
2. Click the **Color** swatch (white square)
3. In the colour picker, enter the hex code for this material (e.g., #3A3A3A for Tré's hoodie)

**Result:** You now have a hard two-tone toon shader. The object will have a flat lit area and a hard dark shadow with no gradient between them.

**Save this as a material preset so you don't rebuild it every time:**
1. In the Material Properties (sphere icon in Properties Panel)
2. Next to the material name, click the **down arrow / browse icon**
3. Click the **shield icon** next to the material name to give it a Fake User (keeps it saved)
4. Rename the material: **ToonShader_Base**

---

## 1.14 Setting Up Freestyle Outlines

Freestyle adds the black ink outlines around objects — essential for the anime look.

1. Go to Properties Panel > **Render Properties** (camera icon)
2. Scroll down to find the **Freestyle** section
3. Tick the checkbox to enable **Freestyle**

**Configure the line style:**
1. Go to Properties Panel > **Scene Properties** (cone/triangle icon tab)
2. You will see **Freestyle Line Set** — expand it
3. Under **Edge Types**, make sure only these are ticked:
   - **Crease** — tick ON
   - **External Contour** — tick ON
   - All others (Silhouette, Border, etc.) — tick OFF
4. Set **Crease Angle** to **45°**

**Set line thickness:**
1. Still in Scene Properties, look for **Freestyle Line Style**
2. Under **Strokes**, find **Base Thickness** — set to **2.5px**
3. Under **Color**, click the colour swatch — set to pure black **#000000**

**Impact frame lines (4px) are set per-shot when you need them** — change this value only for those specific render setups.

---

## 1.15 Importing a VRoid Character into Blender

Once you have a .vrm file exported from VRoid Studio:

1. In Blender: **File > Import > VRM (.vrm)**
2. Navigate to `assets/characters/`
3. Select the .vrm file (e.g., `tre_pourfendeur.vrm`)
4. Click **Import VRM**

**What happens after import:**
- The character appears in the viewport
- It comes with its own armature (skeleton) already attached
- The character will look flat/grey until you apply the toon shader to each material

**Apply the toon shader to the imported character:**
1. Click on the character mesh in the viewport (or Outliner)
2. In the Properties Panel > Material Properties
3. The character will have multiple material slots (skin, eyes, hair, clothing etc.)
4. Click each material slot and rebuild the toon shader for each, using the correct colour for that surface
5. Repeat for all material slots

---

## 1.16 Setting Up a Camera

Every scene needs a camera before you can render:

1. Press **Shift + A > Camera** to add a camera
2. The camera appears as a triangle with a line in the viewport
3. To position it: select the camera, press **G** to move it, **R** to rotate it
4. Press **Numpad 0** to see the camera's view (what will be rendered)
5. You can now move the camera in this view by pressing **G** while in camera view

**For more control — lock camera to view:**
1. Press **N** in the viewport to open the side panel
2. Go to **View** tab
3. Tick **Lock Camera to View**
4. Now when you navigate in the viewport while in camera view, the camera moves with you
5. Untick it when you are happy with the position

---

## 1.17 Setting Up Lighting

Lights tell Blender where the light sources are in your scene. Without them, everything is flat grey.

**Add a light:**
- Press **Shift + A > Light** — choose from: Point, Sun, Spot, Area

| Light Type | Use |
|---|---|
| **Point** | A bulb — orange sodium streetlight, a lamp, a phone screen glow |
| **Sun** | Directional light — use for wide ambient fill (moonlight etc.) |
| **Spot** | Cone-shaped — stairwell light, torch beam |
| **Area** | Flat panel — fluorescent kitchen strip light |

**Configure a light:**
1. Select the light object
2. Properties Panel > **Object Data Properties** (green dot / light-bulb icon tab)
3. **Colour:** click the white swatch, enter hex code (e.g., #B87020 for sodium orange)
4. **Power:** increase or decrease the brightness (in Watts — start at 100W and adjust by eye)
5. **Radius:** for Point/Spot lights — controls how soft the shadow edges are

**Checking your lighting:**
- Press **Z** in the viewport — select **Rendered** from the pie menu
- The viewport now shows an approximate preview of the final rendered look
- Press **Z > Solid** to go back to the normal working view

---

## 1.18 Rendering

**Render a single test frame:**
- Set your frame number in the Timeline at the bottom
- Press **F12**
- A new window opens showing the rendered frame
- Check it looks correct
- Close the render window when done

**Render the full sequence:**
- Make sure Output Settings are set correctly (Section 1.9)
- Press **Ctrl + F12**
- Blender will render every frame and save PNG files to your output folder
- Do not close Blender while rendering
- If you need to stop: press **Esc** (you can resume later — PNG files already rendered are saved)

---

---

# SECTION 2 — VROID STUDIO

**Download:** vroid.com/en/studio → Download → VRoid Studio for Windows

---

## 2.1 What VRoid Studio Does

VRoid creates anime-style characters. You customise their face, body proportions, hair, and clothing. The output is a .vrm file which imports directly into Blender. You do not model characters in Blender — you build them here.

---

## 2.2 Interface Overview

When VRoid opens you land on the main character editor:

- **Left panel:** Category tabs — Face, Body, Hairstyle, Outfit, Accessories, Look
- **Centre:** 3D preview of your character — drag to rotate, scroll to zoom
- **Right panel:** Sliders and options for whatever category is selected
- **Top bar:** Options to create new, load, save, export

---

## 2.3 Creating a New Character

1. On the VRoid main screen, click **Create New Character**
2. Choose **Masculine** or **Feminine** body base — for Tré and Gabriel choose Masculine
3. The default character loads in the editor

---

## 2.4 Body Proportions

1. Click the **Body** tab on the left panel
2. Scroll through the **Body Shape** sliders
3. For Tré (5'11", medium build):
   - Overall height: push toward taller end
   - Body width: medium — not lean, not bulky
4. For Gabriel (5'9", slim build):
   - Height: slightly shorter than Tré
   - Body width: push toward slimmer

**Note:** VRoid's body sliders are relative, not absolute. You are setting proportions, not exact measurements. Match the spirit of the character sheet — lean and deliberate for Gabriel, solid and present for Tré.

---

## 2.5 Face Editing

1. Click the **Face** tab
2. The sliders on the right control facial features: eye shape, nose, jaw, etc.
3. Use your character reference art (from Krita) and the character sheets as target
4. **Skin tone:** Look for **Skin Color** in the Face tab — click the colour swatch and enter the hex code from the character sheet (#8B5E3C range for the brothers)

**Key adjustments for Tré:**
- Jaw: medium — not sharp, not round. Mature face.
- Default expression setting: alert, guarded — adjust eye openness to read that way at rest

**Key adjustments for Gabriel:**
- Eyes: set slightly lighter in tone than Tré's
- Default expression: neutral, watchful. Less eye openness than Tré — he blinks less.

---

## 2.6 Hair

1. Click the **Hairstyle** tab
2. **For Tré:** Search or browse for "twists" or "locs" style options. VRoid has limited natural hair options — you may need to use a short close-cropped base and adjust. Set hair colour to #1A1410 (very dark brown-black).
3. **For Gabriel:** Cornrows — flat, tight, close to the head. Find the closest flat braid base in VRoid. Set colour to #1A1410.

> **VRoid hair limitation:** VRoid's default hair options lean toward East Asian anime styles. Getting tight coil or cornrow styles requires either finding a community hair preset or approximating with the closest available option. Search the VRoid Hub (hub.vroid.com) for community-created hair styles — search "braids" or "locs".

---

## 2.7 Clothing / Outfit

1. Click the **Outfit** tab
2. VRoid has default outfit templates — use these as a base and change the colours

**For Tré:**
- Use a hoodie-style top base — set colour to #3A3A3A (charcoal grey)
- Use jogger/tracksuit bottoms — set colour to #1A1A1A (black)
- Shoes: trainers base, set to off-white #F0F0F0

**For Gabriel:**
- Tracksuit top — set to #1A2035 (dark navy)
- Tracksuit bottoms — same dark navy
- Puffer jacket layer over the top — set to #1C1C1C (matte black)

**Colour adjustments:** Each clothing piece has a colour picker. Click the swatch and either use the colour wheel or enter the hex code directly.

---

## 2.8 Custom Textures (Scar and Mark)

To add Tré's scar and the clan mark on the forearm, you paint these in Krita first (Section 3) and then apply them in VRoid as a texture overlay:

1. In VRoid, go to **Face** tab for the scar, or **Body/Outfit** tab for the forearm mark
2. Look for the **texture paint** option on the relevant body part
3. There will be a section saying "Custom Texture" or a paint brush icon
4. Click it — you can import a PNG image you painted in Krita
5. Adjust the placement and scale so it sits correctly on the skin

**This requires you to first complete the Krita texture work (Section 3.4) before this step.**

---

## 2.9 Exporting as .vrm

When the character is ready:

1. Click the **Export** button (top right area of VRoid)
2. Choose **Export as VRM**
3. A settings window appears — leave all defaults as-is
4. Set **Reduce Polygon Count:** Off (keep full quality for SANG NOIR's close-up shots)
5. Click **Export**
6. Navigate to `assets/characters/` in the save dialog
7. Name the file exactly: `tre_pourfendeur.vrm` (or appropriate name)
8. Click **Save**

The .vrm file is now ready to import into Blender (Section 1.15).

---

---

# SECTION 3 — KRITA

**Download:** krita.org → Download → Windows 64-bit installer

---

## 3.1 What Krita Does in This Project

Krita is used for three things:
1. **Concept art** — draw the clan symbol and character designs before building in VRoid/Blender
2. **Textures** — paint the clan mark, Tré's scar, and environment surfaces (concrete, brick, floor)  
3. **Storyboard panels** — rough drawings from the storyboard notes

---

## 3.2 Interface Overview

- **Left panel:** Tool options for the selected tool
- **Right panel:** Layers panel (top) + Brushes panel (bottom)
- **Top bar:** Menus
- **Centre:** The canvas (your drawing area)
- **Toolbox** (left vertical strip): drawing tools — brush, eraser, fill, selection etc.

---

## 3.3 Creating a New Canvas

For concept art and storyboards:
1. **File > New**
2. In the dialog: Width **1920**, Height **1080**, Resolution **72 dpi**, Colour space **sRGB**
3. Click **OK**

For textures (character skin, clothing, props):
1. **File > New**
2. Width **2048**, Height **2048**, Resolution **72 dpi**, Colour space **sRGB**
3. Click **OK**

---

## 3.4 Designing the Clan Symbol (Do This First)

The clan symbol — a knife with angel wings — must be designed before you paint it onto the character marks or weapons. This is the visual anchor of the entire show.

**How to draw it:**
1. Create a new 2048×2048 canvas
2. Create a new layer (**Layer > New > Paint Layer** — name it "sketch")
3. Select the **Freehand Brush Tool** (keyboard shortcut: **B**)
4. In the top brush options, choose a hard round brush, size ~10–15px
5. Draw the clan symbol rough first — knife blade (narrow, pointed), handle, and wings spreading either side
6. The style: **angular, not decorative**. Sharp angles. Not soft curves. This is a weapon, not a logo.
7. The inscription "Les morts ne vivront pas" runs along the blade (you don't need to include legible text in the symbol — suggest it with a line of marks)

**Refining:**
1. Lower the sketch layer opacity (click the layer in the layers panel, find the Opacity slider at the top of the panel — drag to ~30%)
2. Create a **new layer** above it (name it "clean")
3. Trace over your rough sketch cleanly with crisp lines
4. When satisfied, delete the sketch layer
5. Fill the symbol in black (#000000) using the **Fill Tool** (bucket icon, or press **F**)

**Export:**
1. **File > Export As**
2. Choose **PNG**
3. Save as `assets/characters/clan_symbol_master.png`

This master file is used to create the mark textures, weapon textures, and storyboard panel art.

---

## 3.5 Painting the Clan Mark Texture (for Forearm)

The mark goes on both brothers' forearms. You need to paint it onto a skin-coloured texture background.

1. Create a new 2048×2048 canvas
2. **Fill the background** with the skin colour: select the Fill Tool, click the colour swatch at the bottom of the toolbox, enter **#8B5E3C**, then click the canvas
3. Create a **new layer** above the background
4. Open the clan symbol file you made (File > Open — open `clan_symbol_master.png`)
5. **Select all** (Ctrl + A) and **Copy** (Ctrl + C)
6. Go back to your mark texture, click the new layer, **Paste** (Ctrl + V)
7. The symbol appears — use the **Transform Tool** (T) to scale and position it in the centre-lower portion of the canvas (representing the inner forearm area)
8. Adjust the symbol colour — it should be **#4A2E1A** (dark brownish-grey, not black, so it reads as skin-level mark not ink)
9. Lower the symbol layer opacity slightly (~85%) so it looks like it is IN the skin, not ON it
10. **File > Export As PNG** — save as `assets/characters/tre_mark_forearm.png`
11. For Gabriel's mark: **Image > Mirror Image > Horizontal** — export as `assets/characters/gabriel_mark_forearm.png`

---

## 3.6 Painting Tré's Scar Texture

The scar is above the left eyebrow. It needs to be painted onto a face texture:

1. In VRoid, go to Face > Custom Texture — look for an export option to get the face UV template (a flat map of the face surface)
2. Open the UV template in Krita
3. Create a new layer above it
4. Find the left eyebrow area on the UV map
5. Paint a narrow horizontal scar line: slightly lighter than the skin (#9E6E4A on #8B5E3C base), with a very slight raised-edge look (add a 1px darker line below the main scar line)
6. Export as PNG: `assets/characters/tre_face_scar.png`

---

## 3.7 Drawing Storyboard Panels

1. Create a new 1920×1080 canvas
2. Rough sketch only — clarity of composition matters, not finish quality
3. Use layers: one layer per panel if you are doing multiple panels per page
4. Keep lines loose and readable: the goal is to communicate shots to yourself during the Blender build, not to create finished art
5. Save as **.kra** format (Krita's native format preserves layers) during work: **File > Save**
6. When complete, export the page as PNG: **File > Export As > PNG**
7. Save storyboard pages to: `episodes/ep01/storyboard_pages/` (create this folder)

---

---

# SECTION 4 — DAVINCI RESOLVE

**Download:** blackmagicdesign.com/products/davinciresolve → Click "DaVinci Resolve" (NOT Resolve Studio — the free one)

> Registration required. Fill in any details and download.

---

## 4.1 What DaVinci Resolve Does

DaVinci is where you assemble the final episode. Blender outputs hundreds of individual PNG image files (one per frame). DaVinci takes all of those images, plays them in sequence at 24fps, and you add music and sound on top. Final output is an MP4 video file ready to upload.

---

## 4.2 Interface Overview

DaVinci has multiple pages — accessed via icons at the bottom of the screen:

| Icon | Page | What it does |
|---|---|---|
| Cut (scissors) | Cut page | Quick editing |
| Edit (timeline) | Edit page | Main editing workspace — use this one |
| Fusion (nodes) | Fusion page | Advanced VFX compositing — ignore for now |
| Color (circle) | Color page | Colour grading |
| Fairlight (wave) | Fairlight page | Audio mixing |
| Deliver (rocket) | Deliver page | Export final video |

**You will work primarily in the Edit page.**

---

## 4.3 Create the SANG NOIR Project

1. When DaVinci opens, you see the Project Manager
2. Click **New Project**
3. Name it: **SANG NOIR**
4. Click **Create**
5. The project opens — you see the Edit page with an empty timeline

**Set Project Settings (do this immediately):**
1. Click the **gear icon** in the very bottom-right corner of the screen
2. **Master Settings** tab:
   - Timeline Resolution: **1920 × 1080 HD**
   - Timeline Frame Rate: **24**
   - Playback Frame Rate: **24**
3. Click **Save**

---

## 4.4 Importing a PNG Sequence (Blender Renders)

Blender outputs hundreds of PNG files (e.g., frame0001.png, frame0002.png etc.). DaVinci needs to treat all of them as one clip:

1. Go to the **Media Pool** (top-left panel in Edit page)
2. Right-click inside the Media Pool > **Import Media**
3. Navigate to your render folder (e.g., `renders/ep01/scene01/`)
4. You will see all the PNG files listed
5. **Important:** Before clicking Open — look at the bottom of the file browser. There should be an option called **"Show Individual Frames"** or a checkbox for image sequences. Make sure this is **OFF** — DaVinci should detect the sequence automatically as a single clip.
6. Click on the **first frame** of the sequence (e.g., frame0001.png)
7. DaVinci recognises the numbered sequence and imports all frames as one clip
8. The clip appears in the Media Pool

**If DaVinci imports them as individual images instead of one sequence:**
1. Select all the PNG files in the Media Pool (Ctrl + A)
2. Right-click > **Create New Timeline Using Selected Clips** or look for a "Sequence" option
3. Alternatively: go back to the import dialog, look for **"Import image sequence"** option in the bottom toolbar of the file browser

---

## 4.5 Building the Edit Timeline

1. Click the **Edit** page icon at the bottom
2. You'll see the timeline at the bottom half of the screen — video tracks (V1, V2) and audio tracks (A1, A2)
3. Drag a clip from the Media Pool down to the **V1 track** in the timeline
4. The clip appears as a block on the timeline
5. Drag the next scene clip and place it directly after the first
6. Continue for all scenes

**Basic timeline editing:**
| Action | How |
|---|---|
| Move a clip | Click and drag it on the timeline |
| Trim the end of a clip | Hover over the right edge until cursor changes to trim icon, then drag |
| Delete a clip | Click to select, press Delete |
| Zoom timeline in/out | Scroll while hovering over the timeline |
| Play/pause | Press **Space** |

---

## 4.6 Adding Audio (Music and SFX)

1. Import your audio files the same way as video: right-click Media Pool > Import Media
2. Select your .mp3 or .wav files from `assets/music/` and `assets/audio/`
3. They appear in the Media Pool
4. Drag them to the **A1 audio track** in the timeline (below the video tracks)
5. Move them along the timeline to align with the correct video moments

**Adjusting volume:**
1. Click the audio clip on the timeline
2. In the **Inspector** panel (top-right) you'll see Volume controls
3. Drag the volume slider or type a value (0 dB = original volume, -6dB = quieter, etc.)

---

## 4.7 Colour Grading (Basic)

The colour grade is what gives each location its consistent mood (cold blue for the estate, harsh yellow for the Underground).

1. Click the **Color** page icon at the bottom
2. You see your timeline at the bottom, and the node editor in the middle
3. Click a clip in the timeline to select it
4. In the **Primaries Wheels** (three colour wheels — Lift, Gamma, Gain):
   - **Lift** = affects the dark/shadow areas
   - **Gamma** = affects the midtones
   - **Gain** = affects the highlights
5. **For estate night scenes (cold blue):**
   - Select a scene clip
   - Drag the Lift wheel slightly toward blue (drag the centre dot toward the blue edge)
   - Reduce overall brightness slightly — the estate is dark
6. To apply the same grade to multiple clips from the same scene:
   - Right-click the graded clip > **Grab Still** (saves the grade)
   - Select the other clips > right-click > **Apply Grade**

---

## 4.8 Exporting the Final Video

1. Click the **Deliver** page icon at the bottom
2. In the **Render Settings** panel on the left:
   - **Format:** MP4
   - **Codec:** H.264
   - **Resolution:** 1920 × 1080 (or 1080 × 1920 for TikTok)
   - **Frame Rate:** 24
   - **Quality:** Restrict to **35,000 Kbps** for YouTube, **20,000 Kbps** for TikTok
3. Under **File**, set the output filename: `SANG_NOIR_EP01_YT.mp4`
4. Set the output location: `renders/ep01/`
5. Click **Add to Render Queue**
6. Click **Render All** — DaVinci exports the final video

---

## 4.9 TikTok 9:16 Version

Create a separate timeline for TikTok:

1. In the Edit page, right-click in the Media Pool > **New Timeline**
2. Name it: `EP01_TIKTOK`
3. In Timeline Settings: Change resolution to **1080 × 1920**
4. Re-edit the episode for TikTok in this timeline — use only the shots marked **[SOCIAL]** in the shot list
5. Trim to the most impactful 60–90 seconds for TikTok
6. Export with the deliver settings above (1080 × 1920, 20,000 Kbps)

---

---

# SECTION 5 — AUDACITY

**Download:** audacityteam.org → Download → Windows

---

## 5.1 What Audacity Does

Audacity creates and edits audio for the series. The main uses:
- Custom SFX: the shadow detonation sound, ambient estate sounds
- The Malgris leitmotif (piano note + bass drop)
- Trimming and processing downloaded sound effects

---

## 5.2 First-Time Setup

1. Open Audacity
2. **Edit > Preferences > Quality**:
   - Default Sample Rate: **44100 Hz**
   - Default Sample Format: **32-bit float**
3. Click **OK**

---

## 5.3 Interface Overview

- **Top bar:** Playback controls (Play, Stop, Record)
- **Main area:** Audio tracks displayed as waveforms (the visual shape of the sound)
- **Timeline at top:** Frame numbers / time markers
- **Toolbox:** Selection tool (arrow), envelope tool (for volume curves), cut tool

---

## 5.4 Importing an Existing Sound to Edit

1. **File > Import > Audio**
2. Select your file (.mp3, .wav, .mp4 audio etc.)
3. The sound appears as a waveform track
4. Press **Space** to play it and hear it
5. Click on the waveform to set the playback position

---

## 5.5 Trimming a Sound Clip

1. Select the **Selection Tool** (I-beam cursor) — first tool in the toolbox
2. Click and drag across the part of the waveform you want to **keep** (it highlights in blue)
3. **Edit > Trim Audio** — everything outside your selection is removed
4. Or: select the part you want to **delete** and press **Delete**

---

## 5.6 Building the Malgris Leitmotif

The spec from SOUNDTRACK_DIRECTION.md: a single low piano note (F2 or E2), held 4–6 seconds, then a deep bass drop.

**You need a piano note audio file first:**
- Download a free piano sample: search "piano F2 note free wav" or "salamander piano samples" (free download)
- Import the F2 note into Audacity (File > Import > Audio)

**Build the sequence:**
1. Import the piano note — it appears as a waveform
2. **Effect > Fade Out** — select the last 1 second of the note and apply a fade out
3. Create a new track: **Track > Add New > Mono Track**
4. You will add the bass drop to this second track
5. For the bass: search "808 bass hit free wav" or "sub bass hit free wav" and download one
6. Import it: **File > Import > Audio** — it adds as a new track
7. Position the bass hit to start just as the piano note is ending (at around 4–5 seconds in)
8. Move the bass track along the timeline by pressing **F6** to switch to the Time Shift tool — click and drag the bass track to the right position

**Export:**
1. **File > Export > Export as WAV**
2. Save to: `assets/audio/malgris_leitmotif_v1.wav`

---

## 5.7 Exporting All SFX

Always export as WAV (not MP3) to keep quality:
- **File > Export > Export as WAV**
- 44100 Hz, 32-bit float
- Save to: `assets/audio/` with descriptive names

---

---

# SECTION 6 — SUNO

**Access:** suno.com (web browser — no download)

---

## 6.1 Setup

1. Go to **suno.com**
2. Click **Sign Up** — use a Google or Discord account to sign in
3. The free tier gives you a set number of credits per day to generate music
4. Credits reset daily — plan your sessions accordingly

---

## 6.2 How to Generate Music

1. On the Suno home page, click **Create**
2. You see a prompt box — this is where you describe the music you want
3. You can choose **Custom Mode** (recommended) which lets you control more:
   - **Lyrics:** Leave blank for instrumental (music only, no vocals)
   - **Style of Music:** This is the most important field — describe the genre and mood in detail
   - **Title:** Give it a working title

---

## 6.3 Prompt Writing for SANG NOIR

Suno responds well to specific genre/mood descriptions. Use the prompts from `SOUNDTRACK_DIRECTION.md`. Examples:

**Estate walk / character scene:**
```
Style: UK Drill instrumental, cold and sparse, heavy 808 bass, minimal hi-hats, slow BPM around 70, dark ambient, South London atmosphere, no vocals
```

**Combat track:**
```
Style: Trap 808 drums combined with taiko percussion, aggressive, fast BPM 140-160, heavy bass, cinematic tension, anime action soundtrack, no vocals
```

**Demon arrival:**
```
Style: Deep orchestral strings, very sparse, slow, sudden low bass tones, horror ambient, near-silent with single dramatic notes, no melody, no vocals
```

---

## 6.4 Generating and Downloading

1. Type your prompt
2. Click **Create** — Suno generates 2 variations
3. Listen to both using the play buttons
4. If you want more options: click **Create** again with the same or adjusted prompt
5. When you find one you want to keep:
   - Click the **three dots** (…) next to the track
   - Click **Download** → **Audio (.mp3)**
6. Save to: `assets/music/` with a descriptive name

---

## 6.5 What Suno Cannot Do

- Guarantee the same track again — each generation is unique
- Create the Malgris leitmotif (the piano + bass drop must be built in Audacity — it is too specific for AI generation)
- Produce perfectly looping ambient tracks (trim and crossfade in DaVinci)

---

---

# SECTION 7 — ELEVENLABS (Phase 2 Only)

**Do not use this section until Episode 1 visuals are complete.**

When you are ready:

1. Go to **elevenlabs.io**
2. Sign up for a free account
3. Free tier gives limited characters per month — plan voice sessions to not exceed it

**Using it:**
1. Go to **Speech Synthesis** in the dashboard
2. In the Voice dropdown, browse and pick a voice that matches the character
3. For Tré: deep, South London accent, steady. For Gabriel: slightly lighter, measured.
4. Paste the dialogue line in the text box
5. Click **Generate**
6. Download as MP3: `ep01_tre_line01.mp3` — save to `assets/audio/voices/`

**Voice consistency:** Once you pick a voice for a character, note the exact voice name and settings. Always use the same voice for the same character across all episodes.
