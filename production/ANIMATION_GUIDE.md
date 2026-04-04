# SANG NOIR — ANIMATION GUIDE
## Blender Animation for Beginners

> Animation is the hardest part of this project. It takes time to learn and time to do.
> This guide teaches you exactly what you need to animate SANG NOIR and nothing else.
> Read the whole guide once before you touch the Timeline.

---

## HOW ANIMATION WORKS IN BLENDER

Blender animation is **keyframe-based**. A keyframe is a recorded snapshot of a position, rotation, or value at a specific point in time.

You set keyframe A at frame 1 (character standing still).
You set keyframe B at frame 24 (character's arm raised).
Blender fills in all the frames between 1 and 24 automatically — the arm moves upward.

Everything animated in Blender works this way: positions, rotations, light brightness, camera movement, object visibility. If it can change, it can be keyframed.

---

## SECTION 1 — THE TIMELINE

At the bottom of Blender's screen is the **Timeline**. This is your frame counter and playback control.

**Timeline controls:**

| Action | How |
|---|---|
| Play / Pause animation | **Space** |
| Go to frame 1 | **Shift + Left Arrow** |
| Go to last frame | **Shift + Right Arrow** |
| Step forward one frame | **Right Arrow** |
| Step back one frame | **Left Arrow** |
| Set current frame manually | Click the frame number box in the Timeline header and type a number |

**Set your scene length:**
1. In the Timeline, find **Start** and **End** frame boxes (top of the Timeline)
2. For Episode 1 at 24fps:
   - A 3-minute episode = 4320 frames
   - Set End to **4320** (or per-scene — see Section below on per-scene files)
3. Set Start to **1**

**Per-scene files:** You are working one .blend file per scene (not the whole episode). Set Start and End per scene. A 10-second scene = 240 frames. Set End to 240.

---

## SECTION 2 — BONES AND POSING (HOW TO MOVE CHARACTERS)

VRoid characters come with a **skeleton** (called an Armature) already built in. Each bone in the skeleton controls part of the character's body. To animate a character, you pose their bones — not their mesh directly.

### 2.1 What the Armature Is

When you import a .vrm file into Blender, it creates:
1. The **mesh** — the visible character (skin, hair, clothing)
2. The **armature** — an invisible skeleton of bones inside the mesh

These two objects are linked. When you move a bone, the mesh follows it.

In the **Outliner** (top-right panel), you will see both objects listed:
- Something like `Armature` or `tre_pourfendeur_armature`
- Something like `Body_mesh` or the character name

---

### 2.2 Switching to Pose Mode

To move the character's bones:

1. In the **Outliner**, click on the **Armature** object (not the mesh)
2. In the 3D Viewport, the armature is now selected (you may see bones if they are visible)
3. Press **Tab** — this switches to **Edit Mode** (for editing bone shapes — you do not need this)
4. Press **Tab** again to return to **Object Mode**
5. Now press **Ctrl + Tab** — this opens a mode menu. Select **Pose Mode**

You are now in **Pose Mode**. The bones become selectable and moveable.

---

### 2.3 Selecting and Rotating Bones

In Pose Mode:

| Action | How |
|---|---|
| Select a bone | **Left click** on it in the viewport |
| Select multiple bones | **Shift + Left click** each one |
| Select all bones | Press **A** |
| Rotate a bone | Press **R**, move the mouse, left click to confirm |
| Rotate on one axis only | Press **R** then **X**, **Y**, or **Z** |
| Move a bone (only some bones can move) | Press **G**, move mouse, confirm |
| Reset a bone to default | Press **Alt + R** (reset rotation), **Alt + G** (reset position) |

**The most used bones for SANG NOIR:**
- `upper_arm_L` / `upper_arm_R` — upper arms
- `lower_arm_L` / `lower_arm_R` — forearms
- `hand_L` / `hand_R` — hands
- `head` — head rotation (looking up, down, turning)
- `neck` — neck lean
- `spine` / `spine_1` / `spine_2` — torso lean and twist
- `upper_leg_L` / `upper_leg_R` — upper legs
- `lower_leg_L` / `lower_leg_R` — knees
- `foot_L` / `foot_R` — feet

The exact bone names depend on the VRM export. Select bones visually — click on the arm to select the arm bone, not by name.

---

### 2.4 Setting a Keyframe

Once you have posed the character the way you want for this frame:

1. Make sure you are on the correct frame number in the Timeline
2. In Pose Mode with the armature selected:
3. Press **A** to select all bones
4. Press **I** (Insert Keyframe menu)
5. Select **Location & Rotation** (or just **Rotation** if only rotation changed)
6. A keyframe is set — you will see yellow marks appearing in the Timeline at the current frame

**Do this for every pose you create.**

---

### 2.5 Basic Workflow: Animating a Walk Cycle

The simplest character animation in SANG NOIR is the estate walk in Scene 1. Here is how to approach it:

**Step 1 — Set the rest pose (frame 1):**
1. Go to frame 1
2. Set the character in a neutral standing pose
3. Select all bones (A) and insert a keyframe (I > Location & Rotation)

**Step 2 — Set the mid-step pose (frame 12):**
1. Go to frame 12
2. Rotate the right leg forward (upper_leg_R bone)
3. Rotate the left leg back (upper_leg_L bone)
4. Right arm slightly forward (to match left leg — opposite arm, opposite leg)
5. Insert keyframe

**Step 3 — Set the full step pose (frame 24):**
1. Go to frame 24
2. Return to a similar-but-mirrored version of frame 1 (legs swapped)
3. Insert keyframe

**Step 4 — Loop it:**
1. Go to frame 25 and copy frame 1's pose: select all bones, press **Ctrl + C** (copy pose), go to frame 25, press **Ctrl + V** (paste pose), insert keyframe
2. This creates a one-second walk cycle that can repeat

**Walk cycle note for SANG NOIR:** The brothers' walk is deliberate, unhurried. Not a casual stroll but not tense. Tré slightly heavier in step. Gabriel lighter, quieter. Keep the spines mostly upright — these are two people who are comfortable.

---

## SECTION 3 — THE GRAPH EDITOR (CONTROLLING HOW MOVEMENT FEELS)

After keyframing, the movement between frames follows a curve. By default Blender uses an **easing curve** — movement starts slow, speeds up, then slows down again. This can feel floaty.

For SANG NOIR you mostly want **LINEAR movement** (constant speed) or **sharp impacts** (fast then stopped).

### 3.1 Opening the Graph Editor

1. In any panel, click the panel type icon (top-left corner of the panel)
2. Select **Graph Editor** from the dropdown
3. You now see curves for the selected object's animation

### 3.2 Changing Easing (Making Movement Linear)

1. In the Graph Editor, press **A** to select all keyframe points
2. Press **T** (handles type menu)
3. Select **Vector** — this makes movement arrive and depart from keyframes without easing
4. Or select **Linear** for a similar flat-speed effect
5. **Bezier** (the default) gives the slow-in, slow-out feel

**For the walk cycle:** Use Bezier — it looks natural for walking.
**For a combat punch or shadow detonation:** Use Vector — the snap into and out of impact should be sharp.

---

## SECTION 4 — CAMERA ANIMATION

The camera in Blender is just another object. You animate it the same way — with keyframes.

### 4.1 Animating a Tracking Shot (Shot 02 — Brothers Walking)

This shot requires the camera to follow the brothers as they walk past:

1. Add a camera (Shift + A > Camera) if not already in scene
2. Position it in front of the brothers (facing the direction they will walk from)
3. Go to frame 1 — insert a keyframe on the camera:
   - Select the camera (in Object Mode)
   - Press **I** > **Location**
4. Go to the end frame of the shot
5. Move the camera back (away from where the brothers end up) so they've walked past
6. Press **I > Location** again

Blender will move the camera smoothly between the two positions.

### 4.2 Static Camera Shots (Most of the Episode)

Most shots in Episode 1 are static cameras. For these:

1. Position the camera exactly where the shot requires (use SHOT_LIST.md)
2. Object select the camera
3. Press **I > Location & Rotation** at frame 1
4. Do NOT add any more keyframes to this camera — it stays still

### 4.3 Camera Lock to Character (Following a Character)

For shots that need the camera to follow a character automatically:

1. Select the Camera
2. Properties Panel > **Object Constraints Properties** (chain link icon)
3. Click **Add Object Constraint > Track To**
4. In the **Target** dropdown, select the character armature
5. Set **Track Axis** to **-Z**
6. Set **Up** to **Y**

The camera will always face the character, even as they move. The camera itself still needs to be repositioned with keyframes — this just makes it always look at the character.

---

## SECTION 5 — ANIMATING KEY MOMENTS IN EPISODE 1

### 5.1 Scene 1 — The Walk (Shots 02, 11)

- Two characters walking together, side by side
- Tré slightly ahead
- Both characters need a walk cycle running simultaneously
- Each character is a separate armature — animate them independently

**Approach:**
- Build a walk cycle for Tré (Section 2.5)
- Duplicate it for Gabriel and offset the start frame by 3–4 frames so they are not perfectly synchronised (no two people walk in perfect sync)
- Camera tracks them from the front or side per the shot list

---

### 5.2 Scene 1 — The Montage Positions (Shots 06–10)

These are quick, near-static shots. Each one needs:
- Characters placed in position (posed, not walking)
- Single poses held for 2–5 seconds
- A subtle weight shift in the torso (rotate spine slightly) on the held poses so nobody looks frozen

**Subtle idle animation:**
1. On a held pose, insert a keyframe at frame 1
2. Slightly rotate the `spine` bone (1–2 degrees)
3. Insert a keyframe at frame 30
4. Return to original pos at frame 60, insert keyframe
5. This gives a gentle breathing/weight-shift loop that prevents characters looking like statues

---

### 5.3 Scene 2 — Tré Slowing Down, Gabriel Stopping (Shot 12)

Two characters going from walking to stopping. This is a deceleration animation:

1. Walk cycle running up to the stopping moment
2. On the frame where they stop:
   - Set the foot positions firmly (no more stepping)
   - Set the body weight back slightly (lean back 2–3 degrees on the spine)
3. Insert keyframe on the stop frame
4. On the next 5–8 frames, ease all movement to zero (use the Graph Editor to flatten the curves after the stop keyframe)

A sudden full-stop looks mechanical. The body needs a frame or two to settle into stillness.

---

### 5.4 Scene 4 — Gabriel Dropping to His Knee (Shot 23)

1. Start with Gabriel standing
2. On the frame of the drop:
   - Bend the right knee sharply (rotate lower_leg_R forward/down)
   - Lower the hips (move the root/hips bone downward)
   - Lean the torso slightly forward
3. Over 8–10 frames, animate the drop motion
4. On the final frame of the drop, insert a settling keyframe (body slightly bounces from the impact — move hips down 2 more frames, then back up 1)

---

### 5.5 Scene 5 — The Mark Appearing (Shot 29/30)

The mark does not require character animation — it is a **material animation** (the forearm texture fades in):

1. Select the forearm mesh on Tré's model (in Object Mode, click the arm area)
2. Go to the Material that contains the mark texture
3. In the Material, find the **Alpha** or **Strength** value of the mark texture layer
4. At the frame before the mark appears: click the dot next to the Alpha value (this inserts a keyframe for that value) — set value to **0** (invisible)
5. Five frames later: set the Alpha value to **1.0** (fully visible), insert keyframe
6. The mark fades/appears over those 5 frames

If the toon shader does not expose Alpha directly, use an **object visibility keyframe** instead:
1. Select the mark overlay object (if it is a separate plane mesh)
2. Press **I > Visibility** at the hidden frame and the visible frame

---

### 5.6 Scene 5 — The Shadow Smoke Appearing (Shot 32)

The shadow particle system needs to turn on and off:

1. Select the particle system emitter object (on Tré's forearm)
2. In Properties Panel > **Particle Properties** (blue dots icon)
3. Find the **Emission > Start** and **Emission > End** values
4. Set **Start** = the frame the smoke begins
5. Set **End** = the frame the smoke stops
6. Right-click on the Start value > **Insert Keyframe**
7. Right-click on the End value > **Insert Keyframe**

This activates the particle system exactly when you need it and stops it when the scene ends.

---

### 5.7 Scene 6 — Dog Tamer Turning and Walking Away (Shot 36)

The Dog Tamer's movement must be deliberately wrong — slow, mechanical, no natural body rotation before the turn. He does not look where he is going.

**The turn:**
1. On the start frame: Dog Tamer facing the brothers — insert keyframe (all bones)
2. On the turn frame: rotate the ENTIRE armature (not individual bones) 180 degrees on the Z axis. Do this all at once — no gradual head-turn or shoulder-lean first. He just turns.
3. Over 6 frames total (not 2 — slightly slower than natural): animate the body rotating
4. Insert keyframe

**The walk away:**
- Use a walk cycle but with deliberately uneven timing
- One step every 20 frames instead of 12 — slower than a human
- The coat does NOT swing. Keep the coat bones (if separate) locked in position

---

### 5.8 Scene 7 — Tré Walking Back into the Flat (Shots 37–38)

- Simple walk, 10–12 steps
- Tré goes first, camera holds in the doorway
- Gabriel follows
- Use the walk cycle from Scene 1
- The difference: slower. This is grief. Reduce the stride length and the pace.

---

## SECTION 6 — RENDER YOUR ANIMATION

Once all keyframes are set and you're happy with a scene:

1. Make sure Output Settings are correct (Section 1.9 of SOFTWARE_SETUP.md)
2. Set the frame range in the Timeline to cover just this scene
3. Press **Ctrl + F12** to render the entire sequence
4. PNG files save to your output folder one by one
5. Check the folder periodically to see renders appearing — look at them as they generate to catch any errors early

**Test render before full render:**
- Set frame range to just 10 frames
- Render those 10 (Ctrl + F12)
- Check the output PNGs look correct
- Then set the full frame range and render overnight

---

## SECTION 7 — WHAT TO EXPECT (HONEST)

**Episode 1 is 38 shots at ~3 minutes = approximately 4320 frames.**

For a beginner learning Blender while building this:
- Your first shot will take significantly longer than your last — you are learning while doing
- Expect to spend several hours on your first properly animated scene
- It gets faster as the tools become familiar

**The hardest shots in Episode 1:**
1. The walk montage (multiple characters, multiple cuts) — most frames
2. Gabriel dropping to his knee — requires precise bone work
3. The mark appearance — requires material animation
4. The Dog Tamer turn — requires getting the wrong-ness right

**The easiest shots:**
- All the static environment shots (empty corridor, flat exterior)
- The close-ups of the mark and hands — simple, minimal movement

**Render time estimate:**
- Your GPU renders 1 frame in 8-25 seconds
- 4320 frames × 20 seconds average = ~24 hours of render time per episode
- Render overnight in scene chunks — you do not need to babysit it

**Build one scene at a time. Complete it. Move to the next. Do not open 8 .blend files simultaneously.**
