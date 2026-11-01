# The prompt

Copy everything inside the box into Claude Code (or any coding agent that can run code, install npm packages and use ffmpeg). Fill the `[BRACKETS]` first. Put your app screenshots in a folder and give Claude the path.

```text
Make a 15-20 second vertical promo reel (1080x1920, 60 fps) for my brand. It is a clean motion-design
promo: a phone showing my REAL app screens, floating UI cards, kinetic text and a brand-colour flood.
Do not ask me questions. Decide, build, check your own frames, then deliver the mp4.

## MY BRAND
- Brand / app name: [NAME]
- One-line description: [WHAT IT DOES, IN ONE SENTENCE]
- Audience: [WHO IT IS FOR]
- THE PROBLEM my audience has (this opens the video): [THE REAL PAIN, IN THEIR WORDS]
- What my product does about it: [THE CORE MECHANIC IN ONE OR TWO SENTENCES]
- 4-6 real features, each with a screen I will give you: [FEATURE 1], [FEATURE 2], [FEATURE 3], [FEATURE 4], [FEATURE 5]
- Real copy lines from my app or site that you may quote verbatim: [LINE 1], [LINE 2]
- Real numbers visible in my screenshots that you may use on cards: [e.g. 4.4 km, 5:10 /km]  (never invent numbers)
- Tagline: [TAGLINE]
- Brand colours: primary [#HEX], secondary [#HEX], text/ink [#HEX]
- Font: [FONT NAME or "Geist"]  (load it from a local file; no CDN at render time)
- Logo file: [PATH]   Mascot art (optional): [PATH or "none"]
- Screenshots folder: [PATH]  (real, clean app screens: no private chats, no faces, no real usernames)
- Call to action at the end: [e.g. "Follow for more", "Download on the App Store", "Comment WORD"]
- Handle to show on the end card: [@HANDLE]

## STORY (in this order, every scene must be about my product, nothing random)
1. The problem, first. Open on the pain my audience feels, one short kinetic headline plus cards that
   prove it using real numbers or a real line from the app.
2. The turn. A brand-colour flood wipe with one sentence: what changes now.
3. The core mechanic, shown on a real screen with a tap/cursor interaction and a result card.
4. A list of my features: the text list highlights one item at a time while the phone swaps to the
   matching real screen.
5. The hook of the product (rivals, streaks, rewards, savings, whatever is true for me), shown as two
   cards that react to each other.
6. End card: brand-colour flood, logo, tagline, handle, CTA.
Do not add charts, globes, stats or any scene that is not part of this story.

## LOOK
- Light, airy background (soft blurred blobs in my colours), generous whitespace.
- Big bold kinetic type: each line rises out of a mask line and leaves by rising out. One highlighted
  line per headline in my primary colour.
- A phone mockup in 3D (perspective, slow float) with my real screenshots inside, swapped with a short
  cross-blur. A tap ripple where my button is.
- White floating cards with soft shadows that pop in on a spring and gently bob.
- Everything fits the safe area (nothing under the top 250px or bottom 300px that matters).
- No stock illustrations, no generic icons that do not exist in my app, no lens flares, no particles.

## BUILD
- One HTML file. Every style is computed from time inside seek(t): no CSS transitions, no timers, no
  state carried between frames. Springs are closed-form step responses; a value with many targets is
  the sum of one spring per change.
- Render with Playwright (playwright-core + the installed headless Chromium): 4 sub-frames per frame,
  blended with ffmpeg tmix for natural motion blur, output 60 fps, H.264, yuv420p.
- Before the full render, screenshot one frame per scene and fix anything cramped, clipped, overlapping
  or hard to read. Check text never overflows 1080 px.
- Run the 60 fps render across 4 parallel pages to save time.

## SOUND
- NO music. NO synthesised or AI-generated sounds. Use real recorded sound effects from a library
  whose licence allows commercial use without attribution (for example Mixkit's free sound effects),
  and save the licence note in the project.
- Sound design style: a dense layer of small hits on almost every motion event. A soft tick as each
  headline line rises, a pop as each card appears, a clean click on every phone screen swap, a mouse
  click on every tap, a short air sweep on every scene change, a bigger sweep on the flood, a clean
  confirmation tone when the key result lands.
- Place each sound by its measured loudest point (find the peak with numpy), not by its start.
- Mix with numpy, then loudnorm to about -16 LUFS with a limiter so true peak stays below -3 dB.
  Verify the decoded mp4 audio never clips.

## DELIVER
- The final mp4 in my Downloads folder, and tell me which file it is.
- Tell me honestly what you could not verify (for example "I did not listen to the audio").
- Do not publish or upload anything.
```

## Notes for the person pasting this

- Give it **real** screenshots. The whole look depends on them. Crop out status bars if they show
  something private.
- "Never invent numbers" matters: cards should only show figures that are visible in your own screens.
- If your brand has a mascot, say so and give the art; the prompt will put it on screen with idle
  motion (breathing, blinking) instead of leaving it static.
- Want a voiceover? Add: "Also write a 40-word voiceover script and time the scenes to it", then
  generate the audio with your own voice tool.
