# Photography / Imagery

The decision function — and the treatment rules.

## Decision tree

Ask in order:

### 1. Is the subject LANGUAGE-NATIVE?

Editorial, manifesto, product copy, text-centric content.

→ Use **nothing**. The words are the artifact.

*Experimental Jetset rule:* **"turn language into objects."**

### 2. Is the subject SPECIFIC?

A real person, place, product, event.

→ Use **photography**. Only photography signals specificity.

*Creative Bloq rule:* **"Photography is much more effective at depicting a specific subject."**

### 3. Is the subject STRUCTURAL?

A system, flow, relationship, architecture.

→ Use **diagrams**. Often the underrated correct answer. Most pages that use photography for structural subjects should have used a diagram.

### 4. Is the subject ABSTRACT or ATMOSPHERIC?

Concepts, moods, metaphors.

→ Use **illustration** (if budget permits) or **AI imagery** (if heavily art-directed). Never as hero.

### 5. Default

Type alone. When in doubt, strip the imagery.

Most pages over-use imagery.

## Treatment principles

From the masters:

- **Saville** — source-before-style. Find the object that already **means** the thing. Don't prompt Midjourney for it.
- **Bierut** — crop aggressively. The fragment is often stronger than the whole. Saks's 64-square deconstruction works because the parts are denser than the sum.
- **Scher** — image-as-type-inverse. Where type dominates, negative space is the hero. Where image dominates, type becomes dense and small as counterweight.
- **Boom** (and Bierut) — every section has its own photographic logic. Not a grid of same-size thumbnails.
- **Weidemann** — bleed only when the image is the argument; frame when the image is evidence.

## Ratio & crop

**Lock to a narrow set: 4:5, 16:9, 1:1.**

Mixed ratios make pages feel like Pinterest. Consistent ratios compose like film frames.

This is the single most underrated principle on the list. Every award-level portfolio locks ratios.

## Color tie-in

- **Desaturation is the tie-in mechanism** for disparate photos → brings them into one palette
- **But:** desaturation is how mediocre sites fake coherence. If photos are strong, let them keep their color.

## When NOT to bleed

- Editorial contexts — frame it, caption it, let it be evidence
- When the page is about the IDEA and the image is a reference — frame it small and labeled

## When to bleed

- The image IS the argument (hero reveals, atmospheric sections)
- The image IS the content (gallery pages, case studies)

## Commercial register addendum

When `register: commercial` is set, the editorial photography rules still apply — but one additional rule overrides them. On a pitch surface, every photo must **evidence a specific claim in the copy on the same page.** Atmosphere is no longer a legitimate job for an image. Atmosphere costs the reader's attention budget without paying it back, because a commercial reader came to decide, not to feel.

### The cover-the-headline test

1. Find the load-bearing claim adjacent to the image — the headline, the stat, the capacity number, the tier offer.
2. Cover the claim. Look at the image alone.
3. Ask: does the image, by itself, prove the claim?
4. If NO: the image is decoration. Swap it for one that does prove the claim, or remove the slot entirely.

This is a sharpening of the final editorial test ("If you cannot explain WHY this specific image is on this page, remove it"). Editorial accepts *"because it sets the tone"* as a legitimate WHY. Commercial does not — the WHY must be *a claim from the adjacent copy.*

### Worked example — the venue-photo vs marketing-art distinction

The SF Flagship × Worldlabs pitch deck surfaced the pay-rent case. Two legitimate photo types were being used interchangeably when they are not interchangeable:

- **Marketing art** (title key art, brand posters, product renders) — proves *what will be in the room.* Correct for tier-selection slots, title-card slots, menu thumbnails.
- **Claim-evidence photography** (event-in-progress, populated rooms, infrastructure close-ups) — proves *the claim on this page is true.* Correct for hero slots, "why us" sections, capacity claims, AV/infrastructure claims.

Concrete swap, from the real iteration: the Horizon section hero had `venue_main_floor_sandbox.jpg` — an empty floor at 1000×665. The adjacent copy claimed *"VR sessions and partner demo stations together in one evening."* The image proved *"a floor exists"* and nothing more. Swap to `event_keynote_full_audience.jpg` — a populated keynote shot at scale — and the image now proves the copy's actual claim. Same slot, same section, same register; the image went from decoration to evidence.

### Missing image is not fixable with more copy

A claim WITHOUT a supporting image is weaker than the same claim WITH a supporting image. If the photo doesn't exist and can't be sourced, the honest commercial move is to **remove the claim** or to caveat it (*"photography on request"*). Padding a missing image with descriptive prose — *"championship leather with engraved plates, embroidered jerseys, medal lanyards"* — reads on a pitch surface as evasive. The reader notices the absence. A text-only tier description invites the question *"why no photo?"* and the answer *"we don't have one"* is worse than the omission would have been.

### Six semantic categories to audit against

Most commercial decks drift toward covering 3–4 of these well and leaving the rest empty. Before shipping, scan for coverage:

1. **Establishing shot** — proves the place exists at scale (exterior, wide interior)
2. **Configuration-in-progress** — proves events of the pitched type happen here
3. **People-doing-the-activity** — proves the audience in the photo looks like the buyer's team
4. **Architecture-as-context** — proves floor scale, zone count, multi-level claims
5. **Payoff / trophy moment** — proves the bracket, the award, the handshake, the belt
6. **Infrastructure proof** — LED walls, truss, vertical screens, branded surfaces

Categories 5 and 6 are the ones commercial decks most often claim in copy and fail to photograph. If the copy references branded infrastructure or championship moments, the deck needs a photo; otherwise cut the claim.

### Author checklist before shipping

- [ ] Every P0 photo slot has a claim-evidence image, not marketing art in an evidence slot
- [ ] No slot is using atmospheric photography where the copy makes a transactional claim
- [ ] No claim in the copy is stranded without a supporting image (remove the claim or shoot the photo)
- [ ] Across the deck, all six semantic categories that the copy references are represented at least once
- [ ] Cover-the-headline test passes on every photo slot

### Why editorial has no equivalent rule

Editorial copy isn't making transactional claims — the atmospheric photo of a staircase under orange light is doing real work as a tone-setter for an essay. Editorial readers opted in to feel something, and decoration is load-bearing. Commercial readers have ten minutes and a budget; the staircase is the same photo, but it's now decoration costing attention without paying it back. The image didn't change. The reader did.

## AI imagery — strict rules

The default Midjourney look is cinematic-tilt-shift-golden-hour-volumetric-light. It reads cheap because it is the dataset-average aesthetic.

To avoid the generic-AI-look:

1. **Prompt from photography vocabulary.** Film stock, lens, lighting setup. Not adjective piles ("cinematic, vibrant, 8k").
2. **Break symmetry** and add imperfection intentionally. The default AI output is too polished.
3. **Never as hero** without heavy art direction. Use AI imagery for texture, background, atmosphere — contexts where the default aesthetic doesn't load-bear.
4. **Never for specific subjects** — real people, products, places. The uncanny cost exceeds the budget savings.
5. **Heavy post-processing.** Crop, regrade, add grain, reduce polish. Never ship a raw Midjourney output.

## Per-persona posture

| Persona | Imagery posture |
|---|---|
| **Saville** | Photography required. Sourced, not generated. Full-bleed hero or fragment-cropped editorial. Never AI. |
| **Scher** | Typography dominant. Imagery is counterweight — small, dense, evidential. Never hero. |
| **Rams** | Photography if used at all: industrial, white-ground, product-honest. No atmosphere. |
| **Weingart** | Typography dominant. Imagery heavily cropped, layered, half-toned. Material, not hero. |
| **Bierut** | Heritage imagery transformed — archive photos reworked, historical marks fragmented. |

## The final test

If you cannot explain **why** this specific image is on this page — not "to make it look better" but *what it does* — remove it.

Most web imagery is decoration. The principled exception earns its place.
