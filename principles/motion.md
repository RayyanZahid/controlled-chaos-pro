# Motion

Every animation answers: *what problem does this solve?*

If the answer is "because it looks cool," cut it.

## Four categories

### 1. Ambient

**Always-on, below the threshold of notice.**

Rules:
- Passes the **invisibility test** — if you cover it, does the page feel dead? If yes, it's doing work. If the page feels identical, remove it.
- Subject-derived. A breathing gradient whose hues come from the hero image, not a library default.
- Never loud. Never fast. Never a spectacle.

Examples: slow particle drift, gradient breathing, subtle grain movement, parallax at 0.1× scroll rate.

**When to use:** exhibition sites, brand experiences, atmospheric hero sections. Rarely on utility pages. Rams never uses ambient. Saville uses ambient.

### 2. Punctuating

**Triggered, dramatic, rare. 1-3 per page maximum.**

Rules:
- Must be **load-bearing** — if removed, the message is weaker
- Reserved for moments of meaning, not decoration
- Earned by context — the section's argument demands the reveal

Examples: scroll-crossing reveals, CTA interactions, section-entry flourishes, character-matching text morph, physics-driven hero moments (rope, fluid, distortion).

**When to use:** at the key narrative beats. Never as ambient decoration. Weingart and Scher use punctuating.

### 3. Narrative

**Sequence-bound, advances meaning.**

Rules:
- Must **advance the story**, not just reveal layout
- The reader controls pacing (scroll-scrubbed, not hijacked)
- Only appropriate when the scroll IS the story

Examples: sticky-grid scrollytelling, cinematic scroll narratives, chaptered reveals with numeric indices, old-to-new transformations.

**When to use:** case studies, product explainers, origin stories, Bierut-mode rebrand pages. Not on landing pages.

### 4. Reactive

**Pointer/scroll-linked, responsive.**

Rules:
- **Latency budget: <16ms** (one frame). If noticeable lag, it's wrong.
- Must respond to user input within one frame or it reads as broken.
- Feedback, not spectacle.

Examples: cursor magnetism, parallax tied to scroll position, tilt-on-hover, scroll-linked property changes (font weight, color, crop).

**When to use:** throughout, as feedback for interaction. Rams uses reactive exclusively. Every persona uses some.

## Disney's 12 principles — filtered for web

**Translate directly (8):**
- **Anticipation** — hover states prepare for click
- **Staging** — one thing changes focus at a time; don't reveal six elements simultaneously
- **Slow-in / slow-out** — never linear easing; `cubic-bezier` always. Linear motion feels mechanical.
- **Arcs** — swipes follow curves; cursor magnetism uses arcs, not straight lines
- **Secondary action** — button rotates slightly when clicked. Supports primary, never competes.
- **Follow-through** — elements settle past endpoint with subtle bounce. Use sparingly — drawers yes, page content no.
- **Timing** — micro 100-200ms; transitions 300-500ms; large 500-600ms
- **Appeal** — the catch-all. Does it have personality appropriate to the subject?

**Translate partially (3):**
- **Squash & stretch** — works on buttons and loaders. **Never on type** — crushing text reads as broken.
- **Exaggeration** — one signature move per page maximum. Beyond one, it's decoration.
- **Straight-ahead vs. pose-to-pose** — maps to scroll-linked vs. keyframed. Different use cases.

**Skip (1):**
- **Solid drawing** — 3D volumetric form. Context-dependent, not universal.

## Calibration heuristics

### The 1/3 rule

If a user reports **noticing** the motion, reduce its intensity by a third. Iterate until the page feels alive without being noticed.

The best motion is invisible — the page feels *right* but the user can't articulate why.

### One signature per page

One dramatic move. Everything else is utility.

### Ease curves

- **Entrances** — ease-out (content arrives decisively)
- **Exits** — ease-in (content leaves willingly)
- **Transitions between equal states** — ease-in-out
- **Default** — `cubic-bezier(0.22, 1, 0.36, 1)` — a snappy ease-out

### `prefers-reduced-motion`

Non-negotiable floor. Every animation has a reduced-motion fallback. This is the invisible badge award juries check for.

## The crafted-vs-decorated test

Carbon Design System's test: *"If motion is frequently noticed by average users, consider removing or minimizing it."*

- **Invisible motion** = craft
- **Noticed motion** = decoration

Applied to generation: if you would defend a piece of motion by saying "but it looks cool," cut it. Defend it by saying "the user needs this signal" or cut it.

## Implementation

- `tokens/motion.css` — primitives (durations, eases, keyframe library)
- Subject-derived motion character is set per-composition, not via class lookup
- See gallery exemplars for how the four categories compose in practice:
  - ClawCamp ember-stage (punctuating + narrative)
  - Maxima Therapy rope physics (punctuating)
  - Active Theory radial menu (reactive)
  - Saville tribute page (ambient only)

## Motion per persona

| Persona | Primary category | Character |
|---|---|---|
| Saville | Ambient | Slow, contemplative, print-turning |
| Scher | Punctuating | One dramatic reveal of the phrase |
| Rams | Reactive | Feedback only; no ambient, no punctuating |
| Weingart | Punctuating + Reactive | Type-morphs, chromatic aberration, grid violations |
| Bierut | Narrative | Old transforms into new over scroll |
