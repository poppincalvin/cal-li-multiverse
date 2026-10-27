# Universes

53 image prompts. Each one makes the same portrait in another universe: same pose, same framing, the eyes on the same pixels. Make each image with an image model that edits from a reference image, using your `u00` portrait as the reference. The prompt is the universe line plus one lock block: **Lock: transform** for a line that starts with "Transform", **Lock** for the others.

## Fill the slots first

Replace the slots with your character's anchors. These are the things that stay the same in all 53 images. If your character does not have an anchor, delete each clause that uses it.

| slot | what it is | Cal Li (the film) |
| --- | --- | --- |
| `[HAIR]` | the hair, by shape | short messy upswept black hair |
| `[GLASSES]` | eyewear, or another face anchor | thin round black-rimmed glasses |
| `[OUTFIT]` | what they wear at the neck and chest | black turtleneck |
| `[MARK]` | one small signature mark on the outfit | three small white dots stacked diagonally upward on the left chest (viewer's right) |

Keep `[MARK]` small and in the same place in every universe. It returns at the end of the film: the dots light up one by one.

## Lock

Keep the exact framing of the reference image: same strictly frontal pose, same head position and size, the eyes at exactly the same pixel positions, same shoulder line, same crop at mid-chest. Keep the identity: [HAIR], [GLASSES], [OUTFIT] with [MARK]. Calm neutral expression, looking straight into the lens. No text, no watermark, 16:9.

## Lock: transform

Keep the exact framing of the reference image: same strictly frontal pose facing the camera, the head at the same position and size, its eyes at exactly the same pixel positions as the reference's eyes, same shoulder line, same crop at mid-chest. Whatever the subject has become still wears the same [GLASSES] over its eyes and the same [OUTFIT] with [MARK]. Looking straight into the lens, calm and deadpan, shot with total conviction as if this universe is completely normal. No text, no watermark, 16:9.

## Glasses off (optional, for the fast universes)

In the film, the universes that flash by in the fast part of beat 4 have no glasses. The speed-up hits harder that way. To do this, make each of those images again with this edit prompt, using the finished universe as the reference:

Edit the reference image: take the glasses off completely so the bare eyes show, as if it never wore glasses; no frames, no lenses, no marks where they were. Change nothing else: the same framing, pose, eye position, expression, lighting, background, colours, materials and style. No text, no watermark, 16:9.

## u00 — your base portrait

This is not generated from a prompt. It is your character: a frontal, centred, chest-up portrait, 2048×1152, on a plain background, in your signature style (Cal Li: black ink wash on warm rice paper). It is the reference for every universe, the face that the 1024 tiles build, and the last image before the name. In the film the pupils are at (925, 416) and (1098, 416) on 2048×1152: the eyes are level at 36% of the height, 45% and 54% across.

## The 53

u01–u28 are the same person in another medium. u29–u53 are the *Everything Everywhere All at Once* idea: they are not always a person any more, but the pose, the glasses, the outfit and the mark do not change.

## u01-film35
Re-imagine the reference portrait as a real photograph of the subject as a real person, shot on 35mm Kodak Portra film, soft window light from the left, natural skin texture, visible film grain, slightly faded colours, plain warm grey studio backdrop.

## u02-marble
Re-imagine the reference portrait as a classical white Carrara marble bust carved in stone, polished marble surface with fine grey veins, the glasses carved in marble too, [MARK] as small inlaid stones, dramatic museum spotlight from above, dark charcoal museum background.

## u03-pixel
Re-imagine the reference portrait as 16-bit retro video game pixel art, chunky visible square pixels, limited 32-colour palette, dithering in the shadows, flat deep blue background.

## u04-clay
Re-imagine the reference portrait as a handmade stop-motion claymation puppet, plasticine surfaces with visible fingerprints and tool marks, slightly lumpy hair sculpted in clay, tiny wire glasses, soft studio lighting, a miniature set backdrop of a painted pastel wall.

## u05-ukiyoe
Re-imagine the reference portrait as an Edo-period ukiyo-e woodblock print, flat areas of colour, fine carved outlines, visible wood grain and paper texture, muted indigo and ochre palette, a plain pale background with a soft colour gradient.

## u06-xray
Re-imagine the reference portrait as a medical X-ray radiograph: glowing translucent skull and spine, the glasses frames and [MARK] show as bright metal, faint soft-tissue outline of the hair and [OUTFIT], black background, film-negative blue-grey tones.

## u07-astro
Re-imagine the reference portrait as an astronaut in a white space suit with the helmet visor open, wearing the same [GLASSES] inside the helmet, [MARK] as mission patches on the suit chest, the Earth's blue limb reflected on the helmet rim, black starfield background, hard sunlight.

## u08-opera
Re-imagine the reference portrait as a Peking opera performer photographed on stage: bold painted opera face makeup in red, white and black, an ornate headdress with pompoms and beads above the hair, still wearing the [GLASSES], the [OUTFIT] under an embroidered silk collar, dark stage with a warm spotlight.

## u09-oil
Re-imagine the reference portrait as a 17th-century Dutch oil painting, thick visible brushstrokes, warm chiaroscuro light from the upper left, deep brown background, craquelure varnish texture.

## u10-glass
Re-imagine the reference portrait as a cathedral stained-glass window, bold black lead lines, glowing jewel-coloured glass pieces lit from behind, the [OUTFIT] and [MARK] in glass.

## u11-neon
Re-imagine the reference portrait as a cinematic photograph on a rainy cyberpunk street at night, wet skin with magenta and cyan neon light from both sides, raindrops on the glasses, blurred neon signs without readable letters in the background, shallow depth of field.

## u12-old
Re-imagine the reference portrait as a real photograph of the subject at 80 years old: deep wrinkles, age spots, thinning white hair in the same [HAIR] shape, the same [GLASSES], the same [OUTFIT] with [MARK], soft natural light, plain grey backdrop.

## u13-child
Re-imagine the reference portrait as a real photograph of the subject as a 7-year-old child: round child face, [HAIR], small [GLASSES], a child-size [OUTFIT] with [MARK], school-photo lighting, plain mottled blue school-portrait backdrop.

## u14-felt
Re-imagine the reference portrait as a handmade felt puppet: needle-felted wool face with visible fibres, yarn hair, button-stitched details, glasses made of bent black wire, a knitted [OUTFIT] with [MARK] in felt, soft warm light, a plain fabric backdrop.

## u15-paper
Re-imagine the reference portrait as a layered paper-cut sculpture: the face, hair and [OUTFIT] built from stacked layers of cut coloured card with soft shadows between the layers, visible paper edges, the glasses cut from thin black card, a pale paper background.

## u16-thermal
Re-imagine the reference portrait as a thermal infrared camera image: false-colour heat map from deep purple through red and orange to bright yellow, the face glowing warm, the glasses lenses dark and cold, the hair cooler, a cold dark blue background.

## u17-icon
Re-imagine the reference portrait as a Byzantine gold-leaf icon painting: flat gold leaf background with a tooled halo, egg tempera face with stylised highlights, dark outlines, the [OUTFIT] as a robe with [MARK], aged cracked wooden panel texture.

## u18-wire
Re-imagine the reference portrait as a low-poly 3D model in a modelling program: flat-shaded grey triangle facets with a thin white wireframe over every edge, the glasses as simple black tubes, a dark grey viewport background with a faint grid.

## u19-water
Re-imagine the reference portrait as an underwater photograph: the subject is under clear blue water, hair floating upward, small air bubbles rising from the hair and glasses, rippling caustic light patterns over the face and [OUTFIT], deep blue water behind.

## u20-ice
Re-imagine the reference portrait as a sculpture carved from clear ice: translucent frosted ice with trapped bubbles, sharp chiselled facets, cold blue rim light, the glasses carved in ice, [MARK] as frosted ice beads, a black background with faint mist.

## u21-alien
Re-imagine the reference portrait as a friendly alien version of the subject: smooth pale green skin, large dark almond-shaped eyes behind the same [GLASSES], the same [HAIR] and [OUTFIT] with [MARK], a desert planet sky with two moons behind. Keep the alien's eyes at exactly the same pixel positions as the subject's eyes.

## u22-cat
Re-imagine the reference portrait as a photorealistic black cat sitting upright like a person, wearing the same [GLASSES] and the [OUTFIT] with [MARK], messy upswept black fur on the head, studio portrait lighting, plain grey background. Keep the cat's eyes at exactly the same pixel positions as the subject's eyes in the reference.

## u23-graffiti
Re-imagine the reference portrait as a spray-paint graffiti mural on a weathered concrete wall: bold outlines, bright drips and overspray, stencil-cut shadows, the glasses as thick black spray lines, no letters or words anywhere.

## u24-polaroid
Re-imagine the reference portrait as an old instant photo with a thick white instant-film border, slightly faded and warm colours, soft flash light, held flat against a dark wooden table, the photo itself centred and filling most of the frame. Keep the eyes at the same pixel positions as in the reference.

## u25-terracotta
Re-imagine the reference portrait as an ancient terracotta warrior statue: sculpted fired clay face and hair with weathered surface and traces of old paint, the glasses sculpted in clay, the [OUTFIT] and [MARK] sculpted in clay, a dim excavation pit background.

## u26-crt
Re-imagine the reference portrait as a frame from a 1980s television broadcast seen on a CRT screen: visible scanlines, RGB phosphor dots, colour bleeding, slight barrel distortion, video noise, a studio set with a gradient backdrop.

## u27-sketch
Re-imagine the reference portrait as a quick graphite pencil sketch on a page of a lined school notebook: loose construction lines, hatching for the shadows, smudges, the blue ruled lines and a red margin line showing through.

## u28-toon
Re-imagine the reference portrait as a character from a modern big-eyed 3D animated feature film: soft rounded shapes, large expressive eyes behind the [GLASSES], subsurface-scattered skin, stylised clumped hair, warm cinematic lighting, a soft blurred colourful background.

## u29-horse
Transform the subject into a person with the head of a real chestnut horse, a real studio portrait photograph: a realistic horse head with a short messy black mane sticking straight up, the horse's big dark eyes behind the [GLASSES], a human body in the [OUTFIT], soft grey studio backdrop.

## u30-rock
Transform the subject into a smooth grey desert boulder with two big plastic googly eyes stuck on it behind the [GLASSES], the rock wearing the [OUTFIT], alone on a vast silent canyon floor under a pale empty sky, flat quiet light, real photograph.

## u31-raccoon
Transform the subject into a real raccoon standing upright like a person in a busy steel restaurant kitchen, the raccoon's black eye mask behind the [GLASSES], messy upswept fur on its head, warm kitchen light with steam, real photograph.

## u32-pinata
Transform the subject into a party piñata in the subject's shape, built from layers of fringed crepe tissue paper in hot pink, orange and turquoise, hanging from a rope in a sunny backyard, the glasses taped on, the [OUTFIT] and [MARK] made of tissue fringe.

## u33-sock
Transform the subject into a handmade sock puppet: a grey wool sock head with two shiny black button eyes behind the [GLASSES], a red felt mouth, black yarn hair sticking up, the [OUTFIT] at the bottom, in front of a dark red puppet-theatre curtain.

## u34-cactus
Transform the subject into a round green barrel cactus growing out of the [OUTFIT] collar: ribbed green skin, rows of pale spines, a pink cactus flower on top like a tuft of hair, two small dark eyes behind the [GLASSES], a sunny windowsill behind, real photograph.

## u35-octopus
Transform the subject into a real octopus: its soft red-brown mantle as the head, its horizontal-slit eyes behind the [GLASSES], tentacles curling up out of the [OUTFIT] collar, suckers visible, deep teal aquarium water behind, real underwater photograph.

## u36-pigeon
Transform the subject into a real city pigeon sized like a person: grey feathers, an iridescent green-purple neck, the round orange pigeon eyes behind the [GLASSES], ruffled head feathers sticking up, standing on a grey pavement with a blurred city street behind, real photograph.

## u37-shiba
Transform the subject into a real shiba inu dog sitting upright like a person: fluffy red-and-cream fur, upright ears, the dog's eyes behind the [GLASSES], soft window light, plain warm grey backdrop, real photograph.

## u38-frog
Transform the subject into a real green tree frog the size of a person: wet glossy lime-green skin, huge red bulging eyes behind the [GLASSES], a wide flat mouth, rainforest leaves and water droplets behind, macro photograph.

## u39-robot
Transform the subject into a polished chrome humanoid robot: a smooth mirror-chrome head with fine panel seams, two glowing white eye lenses behind the [GLASSES], chrome hair fins sticking up, a clean white laboratory behind, studio product photograph.

## u40-snowman
Transform the subject into a snowman made of packed snow: lumps of black coal as eyes behind the [GLASSES], a carrot nose, dry twigs sticking up as hair, wearing the [OUTFIT], a snowy field at blue dusk with snow falling.

## u41-teddy
Transform the subject into a worn old teddy bear: matted brown mohair fur, a stitched nose, two glass bead eyes behind the [GLASSES], a patched ear, a tuft of fur sticking up, sitting on a child's bed in warm lamp light, real photograph.

## u42-goldfish
Transform the subject into a person with the head of a bright orange goldfish, a corporate headshot photograph: wet glossy scales, the round fish eyes behind the [GLASSES], a small open fish mouth, a grey office background with soft even lighting.

## u43-moai
Transform the subject into a giant Easter Island moai head carved from dark volcanic stone: long face, heavy brow, the [GLASSES] carved in stone, moss and weathering, the [OUTFIT] carved in stone, a grassy hill under dramatic clouds.

## u44-patina
Transform the subject into a colossal copper monument statue covered in pale green verdigris patina, like a famous harbour statue, the glasses in copper, streaks of oxidation, a bright blue sky with a few clouds behind.

## u45-ghost
Transform the subject into a classic bedsheet ghost: a white sheet draped over the subject with two cut-out eye holes behind the [GLASSES], the [OUTFIT] collar showing at the bottom, standing in a dark suburban hallway lit by a flashlight, real photograph.

## u46-cardboard
Transform the subject into a homemade cardboard-box robot costume: brown boxes taped together, two bottle caps as eyes behind the [GLASSES], marker-drawn buttons, bent drinking straws as antennae sticking up, a messy living room, real photograph.

## u47-potato
Transform the subject into a big russet potato with two small eyes behind the [GLASSES], pale sprouts sticking up as hair, sitting inside the [OUTFIT] on a kitchen counter, soft daylight, real photograph.

## u48-knight
Transform the subject into a medieval knight in battered steel plate armour with the helmet visor raised, only the [GLASSES] visible in the dark of the helmet, a plume sticking up, a misty battlefield at dawn, cinematic film still.

## u49-yeti
Transform the subject into a shaggy white yeti: long matted white fur, a dark leathery face with eyes behind the [GLASSES], ice in the fur, standing on a windy snowy mountain ridge, real photograph.

## u50-mummy
Transform the subject into an ancient Egyptian mummy wrapped in yellowed linen bandages, two dark eyes behind the [GLASSES], loose bandage ends sticking up like hair, a torch-lit tomb with hieroglyph-carved walls (no readable letters), cinematic film still.

## u51-kungfu
Re-imagine the subject as the star of a 1970s Hong Kong martial-arts film, a frame from the film: saturated faded colour film, scratches and dust, a sweaty heroic face, a temple courtyard with red pillars behind.

## u52-anime
Transform the subject into a character in a 1990s hand-painted cel animation, a frame from the film: thick ink outlines, flat cel shading, a painted background of a city at sunset with power lines, slight film grain.

## u53-otherlife
Transform the subject into who they are in another life with a different gender, a real photograph: the same [HAIR], the same [GLASSES] and [OUTFIT] with [MARK], soft window light, plain warm grey backdrop.

