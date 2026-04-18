# Composition Engine

How to actually execute the workflow. This is the spec an LLM follows when generating a CC-PRO output.

Read `SKILL.md` first for the high-level workflow. This document describes what happens inside each step.

## The 8 phases

### Phase 1 — Subject intake

**Inputs:**
- Subject description (what is this page about?)
- Output context (web page, presentation deck, landing hero, long-form)
- Optional: user-specified persona, user-specified forces overrides

#### Phase 1a — Brief sufficiency check (before parsing)

Thin briefs produce thin output. Before parsing, evaluate whether the incoming brief gives you enough to generate from. Do NOT run this as a gauntlet — most briefs pass this check silently and proceed.

**The brief proceeds directly if ANY of these hold:**

1. **It names a specific reference object** — a painting, record, era, building, product, photograph, person, cultural artifact. *"Like Peter Saville's Factory sleeves"*; *"built like a Braun T3"*; *"the aesthetic of late-1970s Manchester."* One named thing is enough.
2. **It describes a functional output** — a tool, dashboard, login, settings page, admin surface. Functional briefs don't need anchors; they need discipline (Rams handles this).
3. **It contains a declarative proposition** — a sentence the reader should leave tattooed. *"Every page is one of one."* Scher can work from this alone.
4. **It's already prose-rich** — more than 3 concrete nouns AND at least one sensory anchor AND stance-bearing language.

**The brief is THIN if the only content is:**

- **Adjective pile** — *"modern, clean, bold, innovative, approachable"*
- **Menu pick** — *"brutalist with the blaze palette, kinetic voice"*
- **Pre-baked solution** — *"make it like Stripe"*, *"like Linear"*
- **Vague gesture** — *"something beautiful about memory"*

(Tells catalogued in `prompting/anti-patterns.md`.)

**When the brief is thin: ask ONE question. Never more than one.** Match the question to the failure tell:

- **Adjective pile / vague gesture** → *"Tell me one specific thing this subject already looks like — a painting, a record, a building, a product, a photograph, a moment. Something concrete. The reference will do the work the adjectives can't."*
- **Menu pick** → *"You've picked from a menu. Rewrite the brief as one paragraph of prose: what is the subject about, and what existing thing in the world is it already like?"*
- **Pre-baked solution** → *"You've referenced another product. What about YOUR subject — what is it on its own terms? One paragraph."*

**After one question:**
- Merge the user's answer into the brief.
- If the answer unlocks an anchor, a proposition, or a reference → proceed to Phase 1b parsing.
- If the user says *"I don't know any reference"* or stays vague → default persona to Scher (if the subject has a declarative proposition possible) or Rams (if the subject is functional). Do NOT ask a second question. One shot, then proceed.

Point the user at `prompting.md` if they want to understand why the question was asked. Never lecture.

#### Phase 1b — Parse the brief

1. Extract the subject's **core proposition** in one sentence. Write it down.
2. Identify the subject's **cultural anchors** — references, influences, historical precedents, artifacts, eras, people. List what's present (may be empty after intake; that's OK).
3. Identify the subject's **emotional register** — one of: contemplative, urgent, celebratory, dissenting, functional, expressive, editorial, atmospheric.
4. Identify the subject's **audience specificity** — general public, specialist audience, niche community, internal stakeholders. This affects persona selection.

**Outputs:**
- `subject.proposition` — one-sentence thesis
- `subject.anchors` — array of cultural anchors (possibly empty)
- `subject.register` — emotional register
- `subject.audience` — specificity tier
- `subject.context` — output context profile
- `subject.brief_quality` — one of: `rich` | `sufficient` | `thin_accepted` (thin brief, intake ran, user chose not to provide more)

**Failure modes:**
- Anchors empty AND proposition weak AND subject isn't functional → escalate: the brief truly does not have enough to generate from. Surface this to the user with a pointer to `prompting.md` rather than attempting a guess.

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

### Phase 8 — Reflection (on demand)

Phase 8 is silent by default. After delivery, the skill does NOT surface metadata, explanations, readouts, or follow-up prompts unless the user asks. Default flow: generate → deliver → stop. No wall of post-mortem.

Five user-intent patterns activate reflection behaviors. Match the user's phrasing to the behavior; surface exactly what's asked for; do not pile on.

#### 8.1 — Interpretation mirror

**Triggers:** *"what did you understand from my brief?"* / *"summarize what you took from that"* / *"are we aligned?"* / *"read it back to me"*

**Presentation:** a compact prose summary of Phase 1 outputs — named references, register, proposition, chosen persona, and one sentence on the forces position. Example:

> *"I read this as a Saville-mode tribute to Factory Records, anchored on Fantin-Latour's Basket of Roses. Palette came from the painting; the typography pair is 1983 — Neue Haas Grotesk and Bembo. Forces land at structure 0.82, warmth 0.65, volume 0.3 — editorial, not civic. Fair?"*

Always close with *"Fair?"* or equivalent. Invites correction. Doesn't demand approval.

#### 8.2 — Attribution readout

**Triggers:** *"why this palette?"* / *"why this type pair?"* / *"where did X come from?"* / *"why this motion choice?"* / *"defend this decision"*

**Presentation:** trace the specific choice back to either (a) the brief phrase that drove it, or (b) the persona principle that required it. Cite. No hand-waving.

Example exchange:

> User: *"Why the cream background?"*
> Skill: *"From your phrase 'Fantin-Latour's Basket of Roses' — the painting's canvas ground is warm cream, sampled as --color-bg. It's the anchor's actual paper, not an aesthetic choice."*

Every attribution names (a) the brief fragment it descended from or (b) the persona rule it obeys. If a choice can't be attributed to either, flag it — it's probably decoration and should be reconsidered.

#### 8.3 — Force readout

**Triggers:** *"show me the forces"* / *"where did this land?"* / *"what's the forces profile?"*

**Presentation:** the five force values with a one-sentence synthesis of what they mean together. Text format (for chat):

> structure **0.82** · density **0.3** · warmth **0.65** · stillness **0.95** · volume **0.3**
> *Rigid editorial restraint, breathing airy, warm, contemplative, whispered — Saville forces.*

If the output surface supports visual rendering (the generated page itself, a companion doc), a compact radar is acceptable. In chat, use the ordered list.

#### 8.4 — Taste-diff rewrites

**Triggers:** *"help me with this brief"* / *"rewrite my brief"* / *"is this brief any good?"* / *"give me two versions"*

**Presentation:** two rewrites of the user's incoming brief:

- **Toward** — sharpened in the direction the subject already suggests. More specific reference objects, tighter stance, prose-richer. This is where the subject naturally wants to land.
- **Against** — a deliberate counterpoint. Displaces one axis (persona, register, era, or reference category) to break predictability. This is where the subject could land if we refused the obvious read.

One sentence after each explaining what it does differently. User picks; skill proceeds with the chosen rewrite.

**Fingerprint logic:**

- **First generation for this user**: no fingerprint exists. *Toward* sharpens the brief's natural register. *Against* moves orthogonally.
- **After multiple generations**: *toward* matches the user's apparent aesthetic gravity (inferred from recent outputs). *Against* deliberately breaks the pattern the gallery similarity check has started to flag.

Never produce only one rewrite. The two-option framing is the mechanic — it lets the user choose an axis instead of accept an answer.

#### 8.5 — Force-dial re-run

**Triggers:** *"more warmth"* / *"less volume"* / *"tighten structure"* / *"re-roll with more stillness"* / any phrase naming one of the five forces with a direction

**Presentation:** adjust the named force by ~0.15 in the requested direction (clamped to 0–1). Re-run the composition with the new forces. Report the delta:

> *"Warmth 0.3 → 0.45. Palette shifted toward earth tones; border-radius bumped up to ~7px; typography suggestions leaned more humanist."*

One force at a time. Let the user drive iteration dimension-by-dimension; don't second-guess them by adjusting multiple axes at once.

**Naming conflicts:** if the user says *"more warmth"* but the persona is Rams (which caps warmth low by design), acknowledge the constraint: *"Rams constrains warmth below 0.2 — pushing higher would move out of Rams-mode. Want to try it anyway, or adjust within Rams?"*

---

### When reflection stays silent

- Immediately after delivery, with no user follow-up → silent
- When the user's next message is about something else → silent
- When the user reports the output is good → silent (don't explain what they already accepted)

The reflection surfaces exist to be pulled, not pushed. Pushing them turns every generation into a post-mortem.

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
