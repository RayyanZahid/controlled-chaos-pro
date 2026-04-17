---
name: controlled-chaos-pro
description: Generate novel web output via authorial personas and subject-derived aesthetics. Principles-based composition for pages, decks, landing heroes. Five designer personas (Saville, Scher, Rams, Weingart, Bierut), first-class motion, strategic microfeatures. Every run invents its own DNA.
allowed-tools:
  - Read
  - Write
  - Bash
  - Glob
  - Grep
  - Edit
---

# Controlled Chaos PRO

You are not picking from a menu. You are an author working in a chosen designer's method, responding to THIS subject, producing something that has never existed before.

## The core shift

v1 offers 5 modes × 8 moods × 5 voices. 200 combinations, and every combination becomes recognizable "CC" after six months. Pattern fatigue.

PRO removes the menu. Aesthetic DNA is **derived** from the subject. Method comes from a **persona library**. Every output is one-of-one.

## Workflow

### Step 1 — Understand the subject

Before anything else, answer:

- **Who** is this for? What's the goal?
- **What emotional register** should the reader leave with?
- **What cultural/historical anchors** exist in the subject's world? (A concept, artifact, era, painting, album, document, person)
- **What output context** — standalone web page, presentation deck, landing hero, long-form editorial?

If you skip this step, you're about to write generic output. Stop and answer.

### Step 2 — Select the persona

Read `personas/*.md`. Each persona is a **method**, not an aesthetic:

- **Saville** — *source-before-style.* Find a cultural object that already means the thing, frame it.
- **Scher** — *scale-as-voice.* Typography IS the interface, sized to context.
- **Rams** — *pay-rent test.* Every element earns its presence or is removed.
- **Weingart** — *disciplined rebellion.* Know the grid deeply; break it at one load-bearing point.
- **Bierut** — *adaptive reuse.* Find existing heritage; transform, don't invent.

Pick the persona whose **method** matches the subject's need. NOT the one whose aesthetic you prefer. A design-system page might want Rams (reductive) even if Weingart's aesthetic is cooler.

### Step 3 — Derive the aesthetic DNA

Per the chosen persona's method, derive:

- **Palette** — from a cultural anchor, a hero artifact, the subject's era. Not from a menu. Not from `tokens/color.css`'s defaults.
- **Typographic voice** — pairings appropriate to the method. Use `tokens/typography.css` as primitives to compose, not as a preset menu.
- **Motion character** — per `principles/motion.md`. Pick primary category (ambient / punctuating / narrative / reactive).
- **Imagery posture** — per `principles/photography.md` decision tree.

### Step 4 — Compose

Use `tokens/` as CSS primitives. Compose per the five axioms (read `axioms.md` before generating):

1. Type is the hero
2. Tension is beauty
3. Whitespace is pressurized
4. Motion has meaning
5. Derive, don't decorate

### Step 5 — Inject the discord

Every composition contains exactly **one** deliberate violation of its own chosen mode. Not decoration. The discord must be **load-bearing** — if removed, the composition would be poorer.

If you can't defend why the discord matters, cut it and try again.

### Step 6 — Apply ONE signature microfeature

Read `principles/microfeatures.md`. Pick ONE. Everything else is utility.

Multiple microfeatures compound into noise, not craft. The craft-read comes from restraint.

### Step 7 — Quality gate

Before delivering, answer:

- [ ] Did I **derive** aesthetics from the subject, or lookup from a menu?
- [ ] Is the chosen persona's **method** visible in the output?
- [ ] Is there exactly **one** load-bearing discord element?
- [ ] Is there exactly **one** signature microfeature?
- [ ] Does it pass `prefers-reduced-motion`?
- [ ] Held next to three prior PRO outputs — is it recognizably its own thing, or "CC-PRO default"?

If any answer is no, regenerate.

## What's where

| Path | Purpose |
|---|---|
| `axioms.md` | Five content-operations — read first |
| `personas/*.md` | Authorial method library |
| `principles/motion.md` | Four motion categories + calibration |
| `principles/microfeatures.md` | Catalogued microfeatures (pick ONE) |
| `principles/photography.md` | Imagery decision tree + treatment |
| `tokens/*.css` | CSS primitives (import all five) |
| `gallery/*.md` | Annotated exemplars — **inspiration, not menu** |
| `examples/` | Validation outputs |

## Token import (in generated HTML `<head>`)

```html
<link rel="stylesheet" href="tokens/forces.css">
<link rel="stylesheet" href="tokens/color.css">
<link rel="stylesheet" href="tokens/typography.css">
<link rel="stylesheet" href="tokens/layout.css">
<link rel="stylesheet" href="tokens/motion.css">
```

Set forces on `<html>` per the composition's position on each spectrum (0 to 1):

```html
<html style="
  --force-structure: 0.7;
  --force-density: 0.3;
  --force-warmth: 0.5;
  --force-stillness: 0.8;
  --force-volume: 0.4;">
```

These values derive spacing, radius, tracking, motion duration, border weight — without any additional CSS.

## Anti-patterns

- **Menu shopping** — picking a palette/mode because you like the aesthetic (this is v1 thinking)
- **Persona-without-method** — picking Saville-mode but skipping the source-before-style step
- **Decorative dissonance** — adding a discord element that doesn't earn its violation
- **Microfeature pileup** — cursor trail + grain + chromatic aberration + parallax = noise
- **AI-default imagery** — using raw Midjourney output without art direction
- **Voice stacking** — using three typefaces when two would carry

## The test

If your output could have been generated by CC v1 with the right menu selections, you didn't use PRO — you used v1 with extra steps. Regenerate.
