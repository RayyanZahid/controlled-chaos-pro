# Controlled Chaos PRO

> A principles-based design system for generating novel web output — pages, decks, landing heroes.
> Every run invents its own aesthetic DNA. No shared smell. No template look.

## What it is

A Claude skill that composes web output through **authorial personas** (Saville, Scher, Rams, Weingart, Bierut) applied to **subject-derived** aesthetic DNA. The method is principled. The output is one-of-one.

## How it differs from v1

The original Controlled Chaos skill offers 5 aesthetic modes × 8 mood palettes × 5 typographic voices. 200 combinations, and after six months of heavy use every output becomes recognizable as "CC." Pattern fatigue.

PRO removes the menu. Aesthetic DNA is **derived** from the subject. Method comes from a designer's working approach, not a style palette. Every output is one-of-one.

## Install

Clone into your Claude skills directory:

```bash
cd ~/.claude/skills
git clone https://github.com/RayyanZahid/controlled-chaos-pro
```

## Use

In Claude Code:

> Generate a page for [subject] using controlled-chaos-pro.

Or invoke explicitly:

> /controlled-chaos-pro

## Live pages

- **Root:** https://rayyanzahid.github.io/controlled-chaos-pro/
- **Gallery · the archive:** https://rayyanzahid.github.io/controlled-chaos-pro/gallery/
- **Saville · Factory Records tribute:** https://rayyanzahid.github.io/controlled-chaos-pro/examples/saville-test/
- **Scher · DERIVE, DON'T DECORATE manifesto:** https://rayyanzahid.github.io/controlled-chaos-pro/examples/scher-test/
- **Rams · CC-PRO honest product page:** https://rayyanzahid.github.io/controlled-chaos-pro/examples/rams-test/
- **Weingart · Typografische No. 09 zine:** https://rayyanzahid.github.io/controlled-chaos-pro/examples/weingart-test/
- **Bierut · v1 → PRO adaptive reuse:** https://rayyanzahid.github.io/controlled-chaos-pro/examples/bierut-test/

## Structure

- `SKILL.md` — Claude skill entry, workflow, quality gates
- `axioms.md` — Five content-operations (read first)
- `prompting.md` — How to write a brief that generates (read this before your first prompt)
- `prompting/` — Paired exemplars + anti-patterns catalog
- `composition-engine.md` — The 7-phase execution spec (what actually runs when a page is generated)
- `personas/` — Authorial method library (Saville, Scher, Rams, Weingart, Bierut)
- `principles/` — Motion, microfeatures, photography
- `tokens/` — CSS primitives (forces, color, typography, layout, motion)
- `gallery/` — Annotated exemplars + visual archive (inspiration, **not** menu)
- `examples/` — Validation outputs, one per persona

## The five personas (v0.1)

| Persona | Method | Use when |
|---|---|---|
| **Saville** | source-before-style | Subject has cultural/historical anchors |
| **Scher** | scale-as-voice | Typography can carry the page alone |
| **Rams** | pay-rent test | Every element must earn its presence |
| **Weingart** | disciplined rebellion | Post-modern expressive typography |
| **Bierut** | adaptive reuse | Transform existing heritage |

Each persona is a **method**, not an aesthetic. Picking Saville means following Saville's process — not copying the *Power, Corruption & Lies* sleeve.

## Anti-staleness mechanisms

1. **Subject-derived generation** — palette, type, motion character extracted from the subject, not a menu
2. **Forced dissonance** — every composition contains one load-bearing violation of its chosen mode
3. **Quality gate** — before shipping, verify the output feels distinct from recent runs along four axes (palette / layout / motion / type)
4. **Gallery-as-inspiration** — exemplars studied for delta-from, never matched 1:1
5. **Bespoke typography per run** — generic type pairings are the primary "CC smell" risk

## License

MIT.

## Roadmap

See [`ROADMAP.md`](./ROADMAP.md) for what's shipped, what's planned for v0.2, and what's parked.

## Credits

Designed by [Rayyan Zahid](https://www.linkedin.com/in/rayyanzahid). Philosophical debt to Peter Saville, Paula Scher, Dieter Rams, Wolfgang Weingart, Michael Bierut. Built with Claude.
