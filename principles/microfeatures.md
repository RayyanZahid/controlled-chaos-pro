# Microfeatures

The tiny details that separate *nice* from *crafted*.

## The rule

**ONE signature microfeature per output.** No more.

Multiple microfeatures compound into noise, not craft. Three microfeatures is a template. One is a decision.

Restraint compounds. This is the difference between a Codrops demo and an Awwwards winner.

## Catalog

### Cursor

- **Context-filled cursor** — the cursor becomes a circle containing contextual text ("View", "Play", "Enter"). Use on portfolio thumbnails, gallery previews, interactive exhibits.
- **Magnetic snap-to-CTA** — cursor springs toward the CTA center within ~40px radius. Use on primary actions only, never on multiple elements per page.
- **Dual-circle trail** — a primary cursor + a lagging shadow circle (~80ms delay). Use on dark-field, slow-paced pages.
- **Context messaging** — cursor displays a word that changes per section. Use for editorial/exhibition sites where each section has a distinct mood.

### Scroll

- **Scrub-not-hijack** — scroll drives the timeline; never steals reader control. ScrollTrigger + Lenis is the standard stack. Default for any long-form content.
- **Pin-then-release** — section pins for two to three screens, then releases naturally. Use for hero reveals, chaptered narratives.
- **Reverse-scroll accent** — a decorative element moves opposite to scroll direction at low velocity. One per page maximum. Use to create spatial depth on minimal layouts.
- **Scroll-synchronized WebGL** — canvas render loop ticker-synced with scroll library. Prevents drift between DOM and WebGL. Essential if your page combines both.

### Hover

- **Letter-scramble morph** — characters that appear in both strings animate to their new position; others fade. Use on section-title hover cycles. Bierut signature move.
- **Unexpected micro-rotation** — card tilts 0.5° to 1.5° on hover. Avoid the 3D-flip cliché. Use on product cards, feature tiles.
- **Color-invert slam** — hover swaps foreground/background **instantly**, no transition. Use on brutalist-leaning buttons. Weingart signature.
- **Image → trailer bloom** — poster hover swaps to an autoplaying muted 6-second clip. Active Theory signature. Use on video-adjacent portfolios.

### Loading / transitions

- **Numeric count-loader** — 0 → 100 counter establishes tempo. Use instead of spinners. Often paired with film-loader framing.
- **SVG mask wipe** — page transition via a morphing SVG clip-path. Use on route changes for editorial sites.
- **Flip-page transition** — clicked thumbnail FLIP-animates to its detail-page position without re-mounting. GSAP Flip + Barba.js. Use on gallery-to-detail navigation.
- **Stagger-in on enter** — lines of copy arrive sequentially at 60-80ms intervals via SplitText or equivalent. Default for hero copy. Saville and Scher both use this.

### Textures

- **Subtle CSS grain overlay** — 2-4% opacity SVG noise as a fixed overlay. Use on dark-field heroes only. Over-applied on clean sites, it kills the clarity.
- **Chromatic aberration on hero** — 1-2px RGB channel split on a single image or headline. Punctuation, not theme. Weingart signature.

### Sound (use sparingly — 5-10% of award sites)

- **UI click 80-300ms** — tactile blip on primary CTAs only. Mute by default. Toggle must be visible.
- **Ambient loop 10-22 seconds** — section-length bed for exhibition or brand experience sites only. Never on utility pages.

### Typography flourishes

- **Variable-font weight-on-scroll** — `font-weight` morphs 400 → 800 tied to scroll position. One hero word per page. Scher signature.
- **Kerning-on-emphasis** — a single word gets +40 to +60 letter-spacing on hover, tightens on release. Cheap to implement, high craft-read.
- **Editorial caption typography** — small-caps eyebrows, italic pulled captions, hanging-indent pull quotes, hairline footnote rules. Saville signature.
- **Underline animations** — links animate a 2px rule in from left on hover. Default microfeature for editorial sites.

### Personality

- **One memorable 404** — a Pong-playable page, a crying mascot, testimonials-for-a-page-that-doesn't-exist. One per brand.
- **Custom selection styling** — `::selection` uses the page's accent color, not browser default. Cheapest craft-read on the list.

## Selection heuristic — by persona

| Persona | Signature microfeature |
|---|---|
| Saville | Editorial caption typography + grain overlay |
| Scher | Variable-font weight-on-scroll OR kerning-on-emphasis |
| Rams | **None.** The discipline IS the microfeature. |
| Weingart | Color-invert slam OR chromatic aberration on hero |
| Bierut | Letter-scramble morph + numeric index chrome |

## Attribution

Catalog derived from award-site study 2025-2026 — Awwwards SOTDs, FWA, Codrops pattern breakdowns. See `gallery/` for annotated examples.
