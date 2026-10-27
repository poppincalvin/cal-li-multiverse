# Multiverse intro — the prompt

Paste this file into a coding agent (Claude Code, Codex, Cursor, Gemini CLI, or another). Put `UNIVERSES.md`, `SOURCES.md` and `timing.json` in the same folder. Fill in **Inputs** first. The agent writes the code, you make the images, and the film renders on your own computer.

---

## Inputs

- **NAME**: the only words in the film, on the end card. (Film: `Cal Li`)
- **PORTRAIT**: `assets/universes/u00.png`, your character, frontal, centred, chest-up, 2048×1152, plain background, eyes level at about 36% of the height. It can be a photo or a drawing. (Film: black ink on rice paper)
- **ANCHORS**: 3–4 things that stay the same in every universe: hair, eyewear, outfit and one small mark on the chest. Fill them into the slots in `UNIVERSES.md`. (Film: messy upswept black hair, thin round glasses, black turtleneck, three small white dots on the left chest)
- **ACCENT**: one colour, used once. (Film: cinnabar `#D23F2F`)
- **PAPER**: the ground for the last two beats. (Film: warm white rice-paper texture)

## What you are building

A 27.5-second film, 1920×1080, 30 fps, 825 frames, H.264 + AAC. There is no voice and no text until the name. It is about one character in every universe. The power comes from contrast: still against motion, fast against slow, noise against silence. The two references are the multiverse montage in *Everything Everywhere All at Once* (the same pose and the same face position, with the universe changing faster and faster) and Kimi's K3.1 teaser (one photo per frame, slowing down, landing, holding, tearing).

Arc: stillness → the world explodes past → an endless dive → universes speed up → the screen splits into 1024 universes that form the face → silence → the face explodes into slow-motion shards → a black hole swallows everything → black → the original portrait opens out of the dark → the name.

## Rules

1. **Each frame is a pure function of its frame number.** Do not use `Math.random`, `Date.now`, `requestAnimationFrame` state or physics that carries over from one frame to the next. Use seeded hashes (for example, hash of the tile id or the shard id). If you render frame 400 twice, or render it alone, you get the same pixels.
2. **Keep all timing in one event table.** The picture and the sound both read `timing.json`, so every cut and its sound land on the same frame. The one in this kit is the film's own table. Rebuild it if your photo count or your portal positions are different.
3. **Use WebGL2 for the effects.** Write one full-screen fragment-shader pass per effect. Then do a finishing pass with grain that changes every frame, a soft vignette, chromatic fringing and glow from mip levels.
4. **Render deterministically.** Seek the page to each frame in headless Chrome, capture it, and encode with FFmpeg. HyperFrames (HeyGen, Apache-2.0, `npx hyperframes render`) does this and is what the film used. A Puppeteer loop or Remotion also works.
5. **Build in layers.** First make all 8 beats play as plain hard cuts with the full sound cue sheet, and render that. After that, add one effect at a time, and render again after each one.

## Assets

**A. Universes.** Make 53 images from `UNIVERSES.md`, each made from the PORTRAIT as the reference image. Any image model that edits from a reference works (GPT Image, Nano Banana, FLUX, Seedream and so on; check which versions are current). Generate at 2048×1152.

**B. Eye lock.** This trick makes the montage feel like one person. Find both pupils in every universe with a face-landmark detector (MediaPipe Face Landmarker, Apple Vision or dlib). Apply a similarity transform (scale and shift) that moves them onto the PORTRAIT's pupils. Limit the scale to 0.9–1.1 so that a bad detection cannot ruin an image. If no face is found (a rock, a robot), keep the image as it was generated: the prompt already puts the eyes in place. Then resize to 1600×900.

**C. World photos.** You need about 37 public-domain or CC0 photos: space, Earth, the sun, planets, the moon, macro and micro shots, eyes. Take them from images.nasa.gov, and from Wikimedia Commons or Openverse filtered to PD/CC0. Resize them to 1280×720. For the dive you need 11 photos (they can be among the 37), each with a round thing that fills it: galaxy → ring nebula → sun → Earth → typhoon seen from a space-station window → typhoon eye → tree rings → vinyl record → diatom → soap bubble → iris. For each one, write down the round thing (`o`: centre and radius) and a "portal" inside it (`p`: a smaller round feature that the next picture's round thing will fill). The film's photos and coordinates are in `SOURCES.md` and `timing.json` → `f03.steps`.

**D. Atlas.** Make one 4096×2304 texture of 8×8 tiles, each tile 512×288. Put all the universes in first, then fill the rest with world photos, taken alternately from the darkest and brightest ends so that the mosaic has real blacks and whites. Rank the tiles by mean RGB brightness (an 8×8 downscale gives one pixel per tile).

**E. Music.** Use one continuous piece of music and do not cut it into parts (see Sound).

**F. Sound effects.** Generate 20 sound effects and synthesise 7 in code (see Sound).

## The film, beat by beat

Times are global seconds. Frame numbers inside a beat are local and start at 0.

| # | beat | seconds | frames | picture | sound |
| --- | --- | --- | --- | --- | --- |
| 1 | eyes | 0.0–1.5 | 45 | still ink close-up of the eyes; torn apart from 1.1 s | three clock ticks, then nothing |
| 2 | world | 1.5–4.0 | 75 | white flash, then one photo per frame, slowing down, landing on the galaxy | boom; a click per cut; a thud on landing |
| 3 | dive | 4.0–8.0 | 120 | hold, then a zoom through 11 nested worlds into the portrait | a riser; a whoosh per portal |
| 4 | universes | 8.0–13.0 | 150 | the same pose in universe after universe, faster and faster | eight signature sounds, then denser clicks |
| 5 | split | 13.0–16.5 | 105 | 4 → 16 → 64 → 256 → 1024 tiles that become the face | a digital tear per split, then **silence** |
| 6 | blast | 16.5–22.0 | 165 | the face shatters, shards drift in slow motion, a black hole eats them | explosion, ringing, heartbeat, vortex, hard cut |
| 7 | origin | 22.0–24.5 | 75 | the portrait opens out of the dark like ink on paper; the mark lights up | an ink drop, a low chord, three ticks |
| 8 | name | 24.5–27.5 | 90 | NAME, small, on paper | one low sub |

### 1 · Eyes (0.0–1.5 s)

Show an extreme close-up of the PORTRAIT's eyes and glasses, filling the width (a crop of u00). It fades in from black over 0.3 s and pushes in 3% over the beat. Clock ticks at 0.0, 0.5 and 1.0 s, on the beat at 120 BPM. On the third tick (frame 30), show a one-frame warning tear at strength 0.05. From frame 33 (1.1 s), tear the image sideways at strength ((f − 32)/12)^1.3, until nothing is left at frame 44. Per frame and per seed, use 7–46 horizontal bands. Turn a band on with probability = strength, then shift it sideways, quantise it into pixel blocks, smear it, or (rarely) invert it, with RGB split on the edges.

### 2 · World (1.5–4.0 s)

Frame 0 is pure white. After that, show one world photo per cut, alternating dark and bright: sort the photos by brightness and interleave the darkest and the brightest. The shot lengths slow down (*ritardando*): start at 1 frame, multiply by 1.09 each cut, cap at 6 frames, and let the last cut take the rest. In the film the lengths are 1,1,1,1,1,2,2,2,2,2,2,3,3,3,3,4,4,4,5,5,6,6,12 (23 cuts). Each cut punches in and settles: scale = 1.05 + 0.1·e^(−j/2), with j = frames into the cut. The last cut is the dive's galaxy, framed and rolled exactly as beat 3 starts.

### 3 · Dive (4.0–8.0 s)

Hold on the galaxy for 15 frames, then zoom continuously through the chain until the u01 portrait exactly fills the frame on the last frame.

- **Nesting:** Picture k+1 sits inside picture k. A similarity transform maps its round thing `o` onto picture k's portal `p` (scale = r_p / r_o).
- **Zoom:** Zoom in log space. The total is L = Σ log(r_o / r_p). Position along it = L·τ^2.6, with τ going from 0 to 1 over frames 15–119. This starts slowly and is fastest at the landing.
- **Roll:** Roll 0.12 rad per unit of log-zoom, and finish upright at the landing.
- **Drawing:** Draw about 5 nested layers around the current one in each frame. Keep the camera in the current picture's pixel coordinates (doubles), not in world coordinates. If you do not, precision breaks down after a few orders of magnitude.
- **Motion blur:** Take 10 sub-samples between the previous frame's camera and this frame's camera. This gives radial streaks. Increase the chromatic aberration with zoom speed.
- **Edges:** Each photo is cut out as a crisp circle. The portrait glows out of the pupil.
- **Crossings:** These are the frames where a new picture fills the screen: 52.8, 60.5, 70.2, 79.0, 86.1, 94.0, 100.4, 104.3, 109.7, 113.1, 117.0. Put a whoosh on each one.

### 4 · Universes (8.0–13.0 s)

Show the same pose with the eyes locked to the same pixels, and change the universe on every cut. Cut lengths in frames:

- **Eight slow ones, each with its own sound:** u01 film 14 (shutter), u02 marble 13 (chisel), u03 pixel 12 (8-bit blip), u04 clay 11 (squish), u29 horse 10 (snort), u06 x-ray 9 (zap), u30 rock 8 (boulder thud and wind), u08 opera 7 (gong).
- **Ten faster ones:** u31 6, u05 5, u32 4, u35 4, u11 3, u42 3, u34 2, u43 2, u22 2, u39 2.
- **Then one frame each** to the end of the beat, with every fourth one a world photo. The order is in `timing.json` → `f04.cuts`. These fast ones use the glasses-off images.

Each cut punches in and settles: the extra scale is 0.07·e^(−j/3) for the slow eight, 0.045·e^(−j/1.5) for the faster ten, and a hashed 0.025–0.045 with a ±0.01 rad roll for the one-frame cuts. Under all of it, the whole beat pushes slowly toward the eyes. Some cuts change the aspect ratio with black bars: 4:3 for u03, u12, u26, u52; a tall strip for u05, u17, u43; 2.39:1 scope for u08, u21, u30, u48, u51. The others are full frame.

### 5 · Split (13.0–16.5 s)

- **Splits:** The screen splits on every beat (frames 0, 15, 30, 45, 60) into 2, 4, 8, 16 and then 32 tiles a side.
- **Each split:** It tears and flashes, then pulls back from 2× (zoom = 1 + e^(−j/2.6), j = frames since the split), so the new tiles start at the old tiles' size.
- **Tiles:** Each tile shows an atlas tile and switches at its own rate: every 1–5 frames, from a hash of the tile id.
- **Gutters:** The dark lines between tiles are about 3 px at the first split and a hairline at 32.
- **The face (frames 60–87):** The last pull-back is slow (ease-out cubic from 2× to 1×). During it, each tile switches at its own moment to the atlas tile whose brightness best matches the PORTRAIT under that tile. Then it is relit by the ratio (tile × portrait brightness / tile mean). Multiply the portrait's own strokes into each tile at 75%, so that the glasses, eyes and hair read at sub-tile size, and mix in 20% of the portrait. The 1024 universes now read as the face.
- **Hold:** At frame 87 everything freezes. Hold until frame 105 (0.6 s) in **total silence**. This silence is what gives the blast its weight.

### 6 · Blast (16.5–22.0 s)

- **Shards:** Re-render the frozen mosaic face and cut it into 60 Voronoi cells. Each cell is a thin 3D slab. Its front is the mosaic and its back is the same region of another universe (`timing.json` → `f06.backs`).
- **Explosion clock:** T(t) = 0.55·(1 − e^(−t/0.07)) + 0.05·t, with t in seconds. This gives a fifth of a second of violence, then near-stillness. Start it one frame late, so that frame 1 shows the face cracking under the flash.
- **Motion:** The slabs fly out from the centre, and the middle bulges toward the camera. They turn a little in the burst and mostly in the slow drift, so the backs appear. The camera drifts in between them.
- **Burst look:** White flash for 2 frames, a shock ring, chromatic aberration, edges burned white, sparks, a far starfield in the empty space.
- **Black hole:** From frame 114 to 153, everything spirals into the centre. A point-mass lens in the post pass (pull the UV toward the centre by k/r) bends what is left into a bright ring, and the shadow grows until black fills the frame at frame 157. Stay black until 165.

### 7 · Origin (22.0–24.5 s)

- **Opening:** The PORTRAIT opens out of the same centre like a drop of ink spreading on PAPER, over 20 frames. The edge is ragged (noise), black is outside it, and a warm bright rim runs along the edge, like the black hole's ring.
- **Hold:** After that the picture stays still and pushes in very slowly.
- **Mark:** The MARK lights up in three steps at frames 24, 32 and 40, and the last step turns ACCENT. (Film: the three white dots light up one at a time, and the last dot turns cinnabar.)
- **Ending:** The ink then dissolves back into the paper with a noise-threshold dissolve.

### 8 · Name (24.5–27.5 s)

Use the same paper, with one small line, NAME, centred. In the film it is serif, 46 px, weight 500, letter-spacing 0.34em, colour `#1d1a17`. The letters gather from a wider spread: each glyph starts offset by (i − 2.5)·13 px with blur 8 px and moves to 0 over 1.6 s from 0.2 s, ease power3.out. Move each glyph's x position, not the letter-spacing, because letter-spacing snaps to whole pixels. A small ACCENT dot after the name scales in at 1.45 s (back.out).

## Sound

### Music: one piece

Generate one continuous piece of at least 28 s and play it across the whole film. Prompt:

> A minor, 120 BPM, cinematic electronic score, a pulsing analog synth arpeggio in sixteenth notes that keeps rising in pitch and density, deep sub bass, sustained pipe organ underneath, a faint ticking clock, no drums, no percussion, restrained, vast, precise

If the model takes sections, give it these: **intro** 0–4 s, only a low sustained organ note and the ticking clock · **build** 4–8 s, the arpeggio enters and climbs, the organ grows · **main** 8–16.5 s, the arpeggio at full density keeps rising, the organ swells, tension climbs to a peak · **break** 16.5–22 s, everything drops out except one high sustained organ note, airy and weightless, then a deep rumble swells underneath · **outro** 22–27.5 s, one low organ chord and the ticking clock, very still.

At 120 BPM one beat is 0.5 s, which is 15 frames: the ticks in beat 1 and the splits in beat 5 sit on the beat.

Then apply this automation to the music. Interpolate linearly between the points.

| | points (seconds → value) |
| --- | --- |
| level (dB) | 0→−4 · 1.08→−4 · 1.18→−40 · 1.49→−40 · 1.5→0 · 4.0→−2 · 7.95→+1.5 · 8.0→0 · 15.85→0 · 15.96→−60 · 16.5→−60 · 16.52→−6 · 16.75→−12 · 20.3→−13 · 21.72→−3 · **21.733→ hard cut to silence** · 22.0→−22 · 22.5→−15 · 24.5→−17 · 26.7→−40 · 27.5→−60 |
| low-pass (Hz) | 18000 until 16.5 · 420 at 16.65 (underwater) · 380 at 20.3 · 5000 at 21.73 · 700 at 22.0 · 2600 at 22.6 · 900 at 27.5 |
| reverb wet | 0 until 16.5 · 0.55 at 16.6 · 0.45 at 20.3 · 0.2 at 21.73 · 0.35 from 22.0 |

### Sound effects: generated

Use any sound-effect model, or a CC0 library. Trim the silence before each one so that it lands on its frame.

| id | s | prompt |
| --- | --- | --- |
| tick | 0.5 | a single soft dry wooden clock tick, very close, quiet room |
| explosion | 4.0 | massive cinematic explosion, deep sub boom with a sharp crack transient and a long rumbling tail |
| glass | 3.0 | a huge sheet of glass shattering into thousands of pieces, cinematic, crisp and bright |
| shards | 4.0 | glass shards tinkling in extreme slow motion, airy, reverberant, sparse |
| whoosh | 1.0 | a fast whoosh passing right by the camera, airy, cinematic, short |
| riser | 4.0 | a rising tension riser, accelerating whoosh with the pitch going up, cinematic, ends abruptly |
| vortex | 2.5 | a deep low rumbling vortex sucking everything in, a reverse whoosh building up, ends abruptly |
| heart | 3.0 | a slow muffled heartbeat, deep and close, as heard underwater |
| hit | 1.5 | a cinematic boom hit, deep and punchy, short tail |
| glitch | 0.8 | a digital glitch burst, data corruption crackle, short and sharp |
| shutter | 0.7 | a 35mm film camera shutter click and film advance lever |
| marble | 0.7 | a steel chisel striking marble stone, sharp |
| 8bit | 0.5 | a retro 8-bit video game jump blip |
| clay | 0.6 | a wet clay squish, close |
| xray | 0.7 | an electric x-ray machine zap with a short hum |
| gong | 1.2 | a single bright Chinese opera gong crash |
| neigh | 0.8 | a short horse snort and whinny, close and dry |
| rock | 0.8 | a heavy stone boulder settling on dry desert ground, a low thud and a gust of wind |
| brush | 0.8 | an ink brush stroke on rice paper, close and soft |
| drop | 2.0 | a single drop of ink falling into still water in a vast quiet space, a deep resonant plop with a soft low boom and a long airy tail |

### Sound effects: synthesised in code (48 kHz)

- **click**: a 2 ms crack of differentiated white noise (decay 2.2 ms) plus a sine ping at f0 (decay 4 ms), 14 ms long. One for each fast cut.
- **sub**: a sine whose frequency falls from f_start to f_end, f(t) = f_end + (f_start − f_end)·e^(−t/0.09), with a 3 ms attack and an exponential decay.
- **tear**: sample-and-hold noise (holds of 3–60 samples, random sign and level) over a sine falling from 2.5 kHz, 0.25–0.5 s.
- **ring**: ear ringing after the blast, 3.8 kHz with a 5 Hz vibrato plus a partial 70 Hz above, a soft 80 ms attack and a 0.9 s decay.
- **noise rise**: white noise through a low-pass that opens from 300 Hz to 9 kHz, with a gain that rises as (t/dur)².
- **rumble**: a 38 Hz sine rising 14 Hz, plus low-passed noise, growing as (t/dur)^1.6, cut hard at its end.
- **chord**: a soft organ A-minor chord (55, 82.41, 110, 130.81, 164.81 Hz, with 2nd and 3rd partials), 0.45 s attack, 2.6 s decay.

### Cue sheet (beat-local seconds)

- **1 eyes:** tick at 0, 0.5, 1.0 · a faint tear crackle at 1.12 · cut at 1.5
- **2 world:** hit + sub (120→40 Hz) + a short tear at 0 · a click on every cut from the second to the second-last, ping pitch 3400/n^0.75 Hz (n = shot length, so longer shots click lower), pan alternating ±0.35, slowly getting quieter · on the galaxy: hit low-passed at 900 Hz + sub (80→36 Hz)
- **3 dive:** the riser with its peak on the last frame · a noise rise over the last 1.6 s · a whoosh with its peak on each crossing, playback rate 0.85→1.45 and louder each time, pan alternating · hard cut on the landing
- **4 universes:** hit + sub at 0 · each of the first eight: its own sound + a small low punch (sub 90→48 Hz, 0.3 s) · every other cut: a click, pitch rising 1500→4100 Hz across the beat, louder, pan alternating · a noise rise (400 Hz→12 kHz) over the last 1.5 s · hard cut at the end
- **5 split:** on each split: a tear (longer each time) + glitch + sub (100→40 Hz, a little lower each time), each heavier · the gong reversed and slowed to 0.7×, ending on frame 87 · then cut to silence
- **6 blast:** explosion + glass (at 0.02) + sub (90→30 Hz, 2.6 s) at 0 · ring from 0.25, quiet · shards slowed to 0.7× with reverb from 0.3 · heartbeat low-passed at 400 Hz from 0.9 · the vortex slowed to 0.85×, ending on the black frame · the rumble from the start of the collapse · **everything cuts hard on the black frame**
- **7 origin:** the drop with its "plop" on frame 0, with reverb · sub (80→34 Hz) · the chord · a tick with reverb on each step of the mark (frames 24, 32, 40)
- **8 name:** sub (70→32 Hz, 2.2 s) at 0 · brush at 0.2

Mix: build one stem per beat. Apply one gain to all stems, because their balance is the design, and a soft-knee limiter on the few peaks. Target about −15 LUFS integrated and −2 dBTP true peak (the film measured −15.2 LUFS and −2 dBTP).

## Checks before you call it done

- Render 20 random frames twice: the pixels are the same.
- Lay all the universes over u00 at 50%: the eyes do not move.
- Every cut in `timing.json` has its sound within ±1 frame (draw a waveform under a contact sheet).
- 15.9–16.5 s and 21.73–22.0 s are digital silence.
- There is no text before the name, and no watermark from the image model.
- Make a contact sheet at one frame every 0.5 s and look at it. Then watch the film once with sound and once without. It must still work with no sound, because X autoplays muted.
