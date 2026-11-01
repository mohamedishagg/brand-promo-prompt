# brand-promo-prompt

One prompt that turns Claude Code into a motion designer for your brand. You fill in about a dozen
`[BRACKETS]` (brand, problem, features, colours, screenshots), paste it, and get a 15-20 second vertical
promo reel: your real app screens on a floating phone, kinetic text, floating cards, a brand-colour
flood and an end card, with a dense layer of real recorded sound effects and no music.

By [@_mosvlih](https://instagram.com/_mosvlih).

## Use it

1. Open [`PROMPT.md`](PROMPT.md) and copy the prompt.
2. Fill in your brand details and the path to a folder of **real** screenshots.
3. Paste it into Claude Code (it needs to run code: Node, ffmpeg, Python).
4. Get the mp4 back.

## What you need installed

- Node.js 20+ and `npm i playwright-core` (plus a Chromium: `npx playwright install chromium`)
- `ffmpeg`
- Python 3 with `numpy`

## What makes it work

- **The story rule.** Problem first, then the turn, the core mechanic, the feature list, the hook, the
  end card. The prompt bans scenes that are not part of your product.
- **Real screens only.** It uses your screenshots and only the numbers visible in them.
- **Deterministic animation.** Every frame is a pure function of time, rendered with Playwright and
  motion-blurred by blending four sub-frames per frame.
- **Real foley, not generated bleeps.** Sound effects come from a free commercial-use library and are
  aligned by their measured peak.

## Not affiliated

This is an independent prompt. It is not affiliated with Anthropic, Mixkit, Playwright or any brand
you put into it. Check the licence of every asset you use.

## Licence

MIT
