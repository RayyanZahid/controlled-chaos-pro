# Composition Engine

How to actually execute the workflow. This is the spec an LLM follows when generating a CC-PRO output.

Read `SKILL.md` first for the high-level workflow. This document describes what happens inside each step.

## The 7 phases

### Phase 1 — Subject intake

**Inputs:**
- Subject description (what is this page about?)
- Output context (web page, presentation deck, landing hero, long-form)
- Optional: user-specified persona, user-specified forces overrides

**Actions:**
1. Extract the subject's **core proposition** in one sentence. Write it down.
2. Identify the subject's **cultural anchors** — references, influences, historical precedents, artifacts, eras, people. List at least three.
3. Identify the subject's **emotional register** — one of: contemplative, urgent, celebratory, dissenting, functional, expressive, editorial, atmospheric.
4. Identify the subject's **audience specificity** — general public, specialist audience, niche community, internal stakeholders. This affects persona selection.

**Outputs:**
- `subject.proposition` — one-sentence thesis
- `subject.anchors` — array of cultural anchors
- `subject.register` — emotional register
- `subject.audience` — specificity tier
- `subject.context` — output context profile

**Failure modes:**
- No anchors found → escalate: the subject is too abstract or too new for anchor-based work. Either (a) ask user for references, or (b) default to Scher (language-native) or Rams (function-first) persona.

### Phase 2 — Persona selection

**Algorithm:**

```
if subject.register in [editorial, contemplative, atmospheric] and subject.anchors.length >= 1:
    candidate = Saville
elif subject.register in [urgent, celebratory, dissenting] and proposition_is_declarative:
    candidate = Scher
elif subject.register == functional and audience == specialist:
    candidate = Rams
elif subject.register == expressive and audience.allows_design_literacy:
    candidate = Weingart
elif subject has existing_heritage_assets:
    candidate = Bierut
else:
    candidate = Saville  # default — attempt anchor-find
```

**User override:** if the user explicitly specifies a persona, use it. If the user's choice conflicts with the algorithm, proceed with user's choice but note the tension in comments.

**Outputs:**
- `persona` — the selected method

### Phase 3 — Aesthetic DNA derivation

Per the selected persona's method (read `personas/[persona].md`), derive:

#### Palette derivation

**Saville:** sample 3-5 colors directly from the primary anchor (e.g., image, artifact, era-reference). Extract HSL. Restrict to bg + fg + 1-2 accents + 1 discord. Set `--color-*` variables inline on `<html>` or `:root`.

**Scher:** two non-colors + one loud accent. The accent is subject-derived (what single color IS this manifesto?). Never two accents.

**Rams:** near-monochromatic. bg, fg, one neutral accent for interactive states. Never more.

**Weingart:** CMYK printer's inks with ONE deliberately off-register color. Use `mix-blend-mode: multiply` for the aberration effect. Yellow third-ink as the discord.

**Bierut:** palette sampled directly from existing heritage. If heritage is unavailable or weak, fall back to Saville.

#### Typography derivation

**Saville:** typefaces contemporary to the anchor's era. Pair a display face with a period-appropriate body. Three faces maximum.

**Scher:** one condensed grotesque for civic-scale hero + one readable workhorse for counterweight. Maximum two faces.

**Rams:** ONE typeface. Three sizes total. Do not exceed.

**Weingart:** one workhorse grotesque as the rigorous base + one display cut only in the violation zone. Two faces.

**Bierut:** one heritage face (period-appropriate to subject's era) + one contemporary neutral (Inter, Helvetica Neue, Söhne). Exactly two faces.

#### Motion derivation

Refer to `principles/motion.md` and the persona's motion posture:

| Persona | Primary category | Character |
|---|---|---|
| Saville | Ambient | Slow fade-ins, print-turning |
| Scher | Punctuating | One dramatic hero reveal + reactive kerning |
| Rams | Reactive only | Hover feedback, no reveals |
| Weingart | Punctuating + Reactive | Chromatic aberration, type layering |
| Bierut | Narrative | Scroll-revealed transformation |

#### Force derivation

Set `--force-*` CSS variables on `<html>` inline. Typical ranges per persona:

| Persona | structure | density | warmth | stillness | volume |
|---|---|---|---|---|---|
| Saville | 0.7–0.9 | 0.2–0.4 | 0.5–0.8 | 0.85–0.95 | 0.2–0.4 |
| Scher | 0.85–0.95 | 0.6–0.85 | 0.05–0.2 | 0.3–0.5 | 0.9–1.0 |
| Rams | 0.9–1.0 | 0.4–0.6 | 0.0–0.15 | 0.9–1.0 | 0.05–0.2 |
| Weingart | 0.8–0.9 | 0.6–0.8 | 0.1–0.3 | 0.35–0.55 | 0.65–0.85 |
| Bierut | 0.75–0.9 | 0.4–0.6 | 0.3–0.5 | 0.55–0.75 | 0.4–0.6 |

Adjust within the persona's range based on subject register.

### Phase 4 — Composition

Build the page structure:

1. **Import tokens** — all 5 CSS files from `tokens/`
2. **Set forces** — inline on `<html>` per Phase 3 derivation
3. **Set palette** — inline on `<html>` as `--color-*` vars per Phase 3
4. **Set fonts** — inline on `<html>` as `--font-*` vars per Phase 3
5. **Compose sections** per persona-appropriate rhythm:
   - Saville: hero → anchor → quote → catalog → end
   - Scher: civic-1 → counterweight → civic-2 → counterweight → civic-3 → end
   - Rams: info-hierarchy (no hero) → sections → details → footer
   - Weingart: masthead (Swiss) → hero → articles (grid) → violation → colophon
   - Bierut: heritage swatch → wordmark transformation → transformation sections → closing

6. **Apply axioms** — every section passes:
   - Type is the hero
   - Tension is beauty (offset grids, near-symmetric)
   - Whitespace is pressurized
   - Motion has meaning
   - Derive, don't decorate

### Phase 5 — Inject the discord (Axiom II corollary)

Every composition contains **one** deliberate violation of its own chosen mode. Not decoration. Load-bearing.

Common discord moves:
- **Saville composition** → one Weingart-rotated/layered section
- **Scher composition** → one Rams-mode utility inset
- **Rams composition** → one italic editorial sentence breaking the mechanical tone
- **Weingart composition** → one Rams-mode disciplined caption explaining the violation
- **Bierut composition** → one disciplined Rams-mode heritage swatch

The discord must be **load-bearing**. If removing it would not weaken the composition, it's decoration. Remove it. Try again.

### Phase 6 — Apply ONE signature microfeature

Read `principles/microfeatures.md`. Pick ONE matched to persona:

| Persona | Microfeature |
|---|---|
| Saville | Editorial caption typography + grain overlay |
| Scher | Kerning-on-emphasis OR variable-font weight-on-scroll |
| Rams | NONE (discipline IS the microfeature) |
| Weingart | Chromatic aberration OR color-invert slam |
| Bierut | Letter-scramble morph + numeric index chrome |

Do NOT apply multiple microfeatures. The craft-read comes from restraint.

### Phase 7 — Quality gate

Before delivering, run the checklist:

```
[ ] Aesthetic DNA derived from subject (not menu-picked)
[ ] Persona's method VISIBLE in output
[ ] Exactly ONE load-bearing discord element
[ ] Exactly ONE signature microfeature
[ ] prefers-reduced-motion respected
[ ] Responsive down to 480px
[ ] All 5 axioms pass
[ ] Output distinct from last 3 CC-PRO outputs on palette/layout/motion/type axes
```

**Similarity reject:** if any of the last 3 outputs matches this output >0.7 on any axis, regenerate.

The axes:
- **Palette:** color-count similarity, hue-family similarity, contrast-structure similarity
- **Layout:** section-count, grid-system, hero-treatment similarity
- **Motion:** category mix, signature-move similarity, timing similarity
- **Type:** face-count, pairing-era similarity, scale-rhythm similarity

## Error states

### No cultural anchor found

The subject is too abstract, too new, or too technical for Saville. Options:
- Ask user for reference materials
- Default to Scher (language-native) if the subject has a strong declarative proposition
- Default to Rams (function-first) if the subject is a tool or product

Never fabricate an anchor. If you invent one, the Saville method fails.

### Subject demands imagery but no imagery available

Per `principles/photography.md`:
- If subject is specific → use photography (sourced, not AI-generated)
- If subject is abstract → use illustration OR go typography-only
- If subject is atmospheric → consider AI imagery ONLY if heavily art-directed; otherwise typography-only

### Forced dissonance doesn't land

If the discord element feels decorative, it's wrong. Diagnose:
- Is it load-bearing (removes → composition weakens)?
- Is it legible as intentional (reader recognizes it as a choice, not a mistake)?
- Does it echo a persona other than the primary?

Iterate until the discord is defensible. If you can't defend it, cut it and reconsider whether the composition needs a discord at all — but Axiom II says yes.

## Running this engine inside Claude Code

When invoked as a skill:

1. Read `SKILL.md` for the workflow overview
2. Read `axioms.md` — the non-negotiable floor
3. Determine persona per Phase 2
4. Read `personas/[persona].md` — the method
5. Read `principles/motion.md`, `principles/microfeatures.md`, `principles/photography.md`
6. Read this document (`composition-engine.md`) for phase details
7. Scan `gallery/` for **inspiration only** — do NOT copy any exemplar
8. Generate the output per Phases 3-6
9. Quality-gate per Phase 7
10. Deliver

If any file is missing or you're unsure, STOP and ask. Generating without the method gives you v1 — which is what PRO exists to replace.
