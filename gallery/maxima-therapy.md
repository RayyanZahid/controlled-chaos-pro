# Maxima Therapy — Louis Paquet

A therapist website treated as a cinematic scroll experience. Built in React + GSAP with Matter.js physics. Documented on Codrops.

**URL:** https://maxima-therapy.com (as of 2026-04)
**Build:** [Codrops case study](https://tympanus.net/codrops/2026/04/06/building-the-maxima-therapy-website-react-gsap-and-dabbling-with-ai/)
**Year:** 2026

## The four-axis analysis

### Palette
- Warm desaturated — cream, muted terracotta, deep warm grey. One soft accent.
- Palette is low-contrast in absolute terms but high in harmony. The whole page feels like one color family, not five competing ones.
- **Why it works:** therapy subjects want calm. The palette does therapeutic work.
- **Staling risk:** "warm minimal therapist aesthetic" is its own cliché. What makes Maxima distinct isn't the palette — it's the motion.

### Layout
- **Sticky-grid scrollytelling.** One fixed visual stage holds while scroll scrubs a multi-phase timeline.
- Each section pins for 2-3 screens, releases, next section pins. Reader controls pacing; site controls composition.
- Editorial caption rhythm — small italic pulls between major reveals.
- **Why it works:** the subject (therapy) is fundamentally about pacing. The layout mirrors the subject.
- **Staling risk:** sticky-grid is now ubiquitous. PRO should use it when the subject demands pacing, not by default.

### Motion
- **Signature move: Matter.js physics rope.** A 50-point rope hangs from the hero, draggable, with real physics simulation. Ripple propagates along the rope.
- Scroll-scrubbed narrative throughout. No hijack.
- Motion category: **punctuating + narrative.** The rope is punctuating (one dramatic load-bearing moment). The scroll reveals are narrative (sequence-bound).
- **Why it works:** ONE signature motion move (the rope) + rigorous restraint elsewhere. This is the rule from principles/motion.md — one signature, everything else utility.
- **Staling risk:** the rope is Maxima's; do not port. PRO should ask: what's our subject's load-bearing physics moment? Invent it.

### Type
- Editorial serif (custom-adjacent) for body + a precise sans for labels. Two faces.
- Large lede typography — not civic Scher-scale, but considered editorial weight.
- **Why it works:** the faces carry therapeutic authority. Serif says "considered." Sans says "modern."
- **Staling risk:** "therapy site uses serif" is a trope. Distinctness comes from the type's interaction with motion, not the type alone.

## What PRO carries forward

1. **ONE signature motion move.** Maxima's rope. PRO adopts this as the microfeatures rule: one per page, everything else utility.
2. **Scroll-scrubbed narrative.** Reader controls pacing, not the site. Reject scroll-hijack categorically.
3. **Sticky-grid for subjects that ARE about pacing.** Therapy, meditation, case studies, chaptered narratives.
4. **Low-contrast harmonic palettes** as a legitimate Saville-derivation when the anchor is mood-based rather than object-based.

## What PRO does NOT carry forward

1. **The therapeutic aesthetic specifically.** Do not produce "therapist-style" pages for non-therapy subjects.
2. **Matter.js rope as an archetype.** It's subject-specific (suspension / tension / release — therapy metaphors). Don't ship it as a reusable primitive.
3. **"Dabbling with AI" as described.** The Codrops case study documents AI-assisted texture work that ultimately was discarded or heavily art-directed. Any AI imagery in PRO must follow the same discipline — see `principles/photography.md`.

## Persona attribution

Maxima is **Saville-adjacent with a punctuating signature**:
- Subject-derived palette (therapeutic mood as the anchor)
- Editorial restraint
- One dramatic load-bearing motion moment (the rope)
- Scroll-scrubbed narrative as the layout method

Not pure Saville because the anchor is a mood, not an object. Not pure Scher because typography isn't civic-scale. Hybrid.

## Validation prompt

If asked to *"generate a page for a therapist / coach / counselor,"* DO NOT produce "warm serif minimal scroll therapy template." Ask: what is this specific therapist's anchor? Their methodology, their archive, their books, their influences? Derive from there.
