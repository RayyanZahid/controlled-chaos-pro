# Prompting

The shortest route from nothing to something-good is prose. Not a schema. Not a checklist of adjectives. A sentence or two that sounds like the thing itself.

This document teaches the craft. Read it once. You won't need the skill to tell you again.

## Match the register

Anthropic's own prompt-engineering guide says it directly: *"try matching your prompt style to your desired output style as closely as possible."* Their specific example — *"instead of: 'Do not use markdown in your response' — try: 'Your response should be composed of smoothly flowing prose paragraphs.'"*

Translation — if you want smooth prose paragraphs, write your brief in smooth prose paragraphs. If you want a clinical product spec, write your brief as a clinical spec. The prompt and the output want to rhyme.

This matters more than it sounds. Reasoning-heavy models — the ones this skill is tuned for — actively penalize contradictions. They burn reasoning tokens reconciling a menu-style prompt against a creative task, and they settle for safe. Safe is generic. Generic is exactly what we're trying to avoid. Spec-heavy briefs for creative work don't fail because they're structured; they fail because they mismatch the target register.

## The Shield of Achilles problem

Homer's most famous ekphrasis — 130 lines on a single shield — does not describe the shield. It narrates Hephaestus making it. The scenes come alive because we watch them forged, not because we get a bronze-diameter-and-weight inventory.

Auden's *Musée des Beaux Arts* goes further. He never looks at Icarus. He looks at the ploughman who hasn't noticed, the ship that sails calmly on. You see the painting because of what Auden stares at around it. Indirection is the mechanism.

The bad brief works like a wall label: *"A modern, clean, minimalist landing page for a coffee brand. Warm color palette, mobile-first."* The good brief works like ekphrasis: *"A coffee shop on the top floor of a converted 1920s mill. The grinders sound like a cathedral. Every cup is someone's morning prayer."*

Same subject. The second version gives the skill cultural anchors, emotional register, specificity, and stance — four things no adjective pile has ever loaded into a model's context.

## Six craft moves

**Name with dignity.** Natalie Goldberg's rule: *"Give things the dignity of their names. It is much better to say 'the geranium in the window' than 'the flower in the window.' Geranium gives us the scene by the window — red petals, green circular leaves, all straining toward sunlight."* Specific nouns pull their networks with them. The model has read every geranium ever written; it has not read every flower.

**Lead with stance, not inventory.** Every good brief opens with the *relation* the output should have to something known — rivalry, homage, kinship, critique, counterargument. Gehry's brief for Bilbao from Thomas Krens was *"make it better than Wright."* Stance is generative. Feature lists constrain.

**Compress, then displace.** Dan O'Bannon pitched *Alien* as *"Jaws in space."* Three words. One known emotional compression plus one displacing context. The recipient's imagination does the synthesis. You can write *"a landing page that reads like a Mary Oliver poem."* You cannot write *"modern, clean, warm, human-centered"* and expect the same activation.

**Write oblique.** Don't describe the page. Describe what's around the page — what the reader is doing when they arrive, what they're afraid of, what they expect and don't get, what the subject sits between. The skill is good at rendering centers when the brief renders edges.

**Verbs over adjectives.** Not *"a sleek, modern, minimalist site"* — *"a site that makes you hesitate before scrolling."* Actions the page performs on the reader beat properties the page possesses. The first is a thing-to-build; the second is a thing-to-feel.

**One concrete sensory anchor per paragraph.** A brief without a single named thing drifts into mist. A brief with a dozen named things drifts into clutter. One anchor per paragraph — a texture, a color, an object, a place, a sound — is the tuning.

## When prose fails

Prose is the right register for creative work on reasoning-heavy models. It is not universally correct.

Use structured prompts when:

- The output is machine-parsable (JSON, SQL, tool calls, code)
- The task is extraction or transformation with a rigid target shape
- The audience of the output is downstream code, not a reader

For everything this skill generates — pages, decks, heroes, editorial surfaces, manifestos — prose is the right register.

## Editorial vs. commercial

A brief's prose-richness controls how vivid the output is. A brief's **voice register** controls whether the output sounds like an essay or a quote.

Most CC-PRO briefs are editorial — you're writing a tribute, a manifesto, a brand page, an atmospheric surface. The voice of the brief is the voice of the output: considered, specific, anchored.

Some briefs are **commercial** — pitch decks, sales pages, quotes, investor one-pagers, event proposals. These surfaces are read by someone who has ten minutes and a checkbook. Literary voice in that seat reads as evasive or amateur. When your brief is for a commercial surface, say so directly:

> *"Pitch deck for a private-venue rental business. Four tiers, clear pricing, client-facing. Commercial register — no narrative framing, no romantic tier descriptions."*

Or just name the output form:

> *"A one-pager quote for a $50K event buyout."*

Either triggers the skill's commercial register. You can still write the brief itself in prose — ekphrasis works for commercial surfaces too (*"the feeling of a well-priced menu handed to you by a host who respects your time"*) — but the output will be fact-first, direct-ask, and typographically closer to a document than an essay.

See `principles/register.md` for the full prohibition/requirement list and before/after examples from real pitch iteration.

## What to read next

- `prompting/exemplars.md` — ten paired briefs. Bad vs. good, two per persona.
- `prompting/anti-patterns.md` — the eight common ways a brief kills itself.
- `axioms.md` — the five content-operations the skill holds against every output.

The skill assumes you have read this. Write like you mean it.
