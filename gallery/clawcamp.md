# ClawCamp — Vibe Coding Nights presentation deck

A 48-slide presentation deck presented at Vibe Coding Nights, April 2026. Built with Controlled Chaos v1 tokens, extended with a custom ember-particle system.

**Subject:** Context engineering, AI agents, "the claw is the law."
**Format:** Live-presented deck at room scale.
**Facilitators:** Rayyan Zahid & Michalis Vasileiadis.

## The four-axis analysis

### Palette

- **Derived from subject.** `data-mood="blaze"` — deep amber background, charcoal foreground, ember-red accent, gold discord color.
- **Why it works:** the subject (context engineering, AI agents, "the claw") warranted fire imagery. The palette EARNS its heat rather than decorating with it. Paper-mode slides (cream bg + rust fg) break the heat rhythmically.
- **Staling risk:** `blaze` is a v1 named mood. PRO would derive the palette from the subject directly — sample colors from a hero artifact, not pick from a menu.

### Layout

- **Near-full-bleed typography.** 15rem+ headlines, sparse grids, paper-mode contrast slides interleaved for visual rhythm.
- **Why it works:** the presentation context demands motion stages dominate. ClawCamp treats each slide as a single-statement composition, not a grid of content. This is the right intuition — and the one PRO formalizes with the `context: presentation` profile.
- **Staling risk:** three-column indexed content slides recur across the deck. At 48 slides, the repetition works as rhythm; at 5 separate decks, the same pattern would read as template.

### Motion

- **Punctuating + narrative.** Ember particles generated per-slide with data-attribute config (`data-ember-count`, `data-ember-spread`, `data-ember-targets`, `data-ember-fractures`).
- **Two-phase architecture:** embers drift randomly → on slide-visible, converge to explicit focal targets (~1900ms) → dwell → optionally fracture outward (~1200ms later). Wave/cohesion staggering: each particle's delay is `index × 18ms`, creating visual rhythm per-particle rather than group-simultaneous.
- **Why it works:** the motion ILLUSTRATES the message. Focal-point slides converge the embers; transition slides scatter them. Motion has meaning per Axiom IV.
- **Staling risk:** ember particles are highly recognizable. PRO must NOT fossilize "ember-converge" as an archetype. Invent per-subject particle behavior — ember was the right call for "the claw is the law," not a universal move.

### Type

- **Two-face pairing.** Brutalist mono (JetBrains Mono) for eyebrows and catalog chrome; a serif editorial face for body; a display grotesque for headlines. Three voices in controlled rotation.
- **Fluid scale:** `clamp()`-based sizing calibrated for room-scale presentation (up to 22rem).
- **Why it works:** the type pairing matches the subject — mono for the technical texture, serif for the essayistic tone, grotesque for the civic-scale argumentative beats.
- **Staling risk:** JetBrains Mono appearing across multiple CC-PRO outputs would read as "CC default." Different subjects → different mono choices (or no mono at all).

## What PRO carries forward

1. **Wave/cohesion index-math staggering** — `transition-delay: calc(var(--i) * 18ms)` where `--i` is the particle/item index. Generalizes beyond embers.
2. **Two-phase motion architecture** — appear → dwell → transform. Pattern for punctuating + narrative compositions.
3. **Data-attribute-driven motion config** — expose motion parameters via HTML `data-*` attributes, parsed by JS. Makes motion declarative, per-composition.
4. **Room-scale typography for presentation context** — clamp() values calibrated for 4K projection, not desktop monitor.
5. **Paper-mode contrast slides** — rhythmic palette inversion as a deck-level pacing device.

## What PRO does NOT carry forward

1. **Picking `blaze` from a named mood list.** Derive per subject instead.
2. **Ember particles as a reusable archetype.** Invent new particle behavior per subject. The ember metaphor was subject-appropriate (fire, claws, heat) — not universal.
3. **Hardcoded `slide--pre` intro-slide pattern.** The generator should compose slide rhythm per deck, not apply a fixed template.

## Persona attribution

ClawCamp is **Weingart-adjacent with a Scher-scale hero**:
- Rigorous 12-column slide underpinning (Swiss floor)
- One load-bearing violation per section (the ember convergence moment)
- Civic-scale typography (Scher influence)
- Paper-mode slides as editorial/Saville counterweight

A hybrid composition. Most PRO outputs will be single-persona, but hybrid compositions are valid when the subject demands multiple methods.

## Source

`~/Documents/2026/life/projects/clawcamp/` (currently private repo; see also the slide deck rendered live at Vibe Coding Nights April 2026).

## Validation prompt

If asked to *"generate a presentation for X subject,"* DO NOT reuse ClawCamp's ember system. Ask: what particle behavior (if any) is load-bearing for X? Invent that. Don't port.
