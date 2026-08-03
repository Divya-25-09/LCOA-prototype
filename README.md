# LCOA — dragonfly scroll guide (prototype)

Live: **https://prototype.lcoaurelian.in**

A prototype of a 3D dragonfly that flies through the page as a guide,
introducing each section as you scroll. This is a **feature prototype**, not a
draft of the new site — the copy, imagery and layout are deliberately
placeholder. What is being reviewed is the flight mechanic and the per-section
mood shifts.

This is published on a subdomain so it stays entirely separate from the live
site at lcoaurelian.in.

## What to look at

- The dragonfly's flight path across the seven sections, and whether the timing
  feels right at different scroll speeds
- The mood/lighting shift per section (energetic / reflective / functional)
- Team cards lighting as the dragonfly passes them, rather than on a generic
  scroll stagger
- The circling flourish near the highlighted event card

Colours are placeholders driven by CSS variables, ready to swap for real brand
colours. The type system is the live site's: Birds of Paradise, Jost, Cormorant
Garamond, Pinyon Script.

## Known gaps

- Content, copy and imagery are all placeholder
- Wing-flap amplitude and resting pose may still need tuning
- The 3D model is 3.5 MB, mostly two PNG textures. It needs compressing
  (WebP/KTX2 + Draco) before anything like this ships.

## Running it locally

ES modules will not load over `file://`, so it needs a static server:

```bash
python -m http.server 5180
```

Then open http://localhost:5180

## Console handles

The page exposes `window.__dfly` for tuning without a reload:

| Call | Effect |
|---|---|
| `__dfly.setSize(1.2)` | Resize the dragonfly (world units, nose to tail) |
| `__dfly.flipNose()` | Reverse travel direction if it flies tail-first |
| `__dfly.roll(180)` | One-off roll, to inspect another face |
| `__dfly.t` | Current scroll progress, 0–1 |

Loading with `?placeholder=1` forces the box-and-planes stand-in instead of the
real model.

## Stack

Vanilla JS, GSAP + ScrollTrigger, Lenis, Three.js. No framework, no build step —
it drops into the existing site as-is.

## Credits

"[skull island dragonfly](https://skfb.ly/pHntB)" by dinoguy263allo is licensed
under [Creative Commons Attribution](http://creativecommons.org/licenses/by/4.0/).
Attribution is a condition of the licence, so the credit must stay in the footer
wherever this is used.
