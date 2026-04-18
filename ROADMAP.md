# Roadmap

Where Controlled Chaos PRO has been, where it's going, and what's parked.

## Shipped in v0.1 (2026-04-17)

The whole thing, end to end:

- **Five authorial personas** — Saville, Scher, Rams, Weingart, Bierut. Each a method, not an aesthetic.
- **Five axioms.** One composition engine (eight phases). Five CSS token files. Four annotated gallery exemplars plus a Saville-mode visual archive page.
- **Five validation pages,** one per persona — Factory Records tribute, a civic manifesto, a Rams-disciplined product page, a post-modern zine, a rebrand-as-adaptive-reuse.
- **A three-layer metaprompting framework** — teaching (`prompting.md` + anti-patterns + exemplars), intake (thin-prompt detector + one matched question), reflection (five on-demand behaviors). Silent by default.

## v0.2 — planned

**Live-test the whole stack.** Generate a page for a new subject, end to end — no pre-baked scaffolding. Confirm the brief-sufficiency check, the persona routing, the discord injection, the quality gate, and the reflection surfaces all cook together in practice.

**More personas.** Sagmeister for expressive handmade emotional work; David Carson for raw typographic rebellion beyond what Weingart covers. Potentially Irma Boom (section-as-architecture), once the operationalization problem is solved — her method is beautiful and abstract in roughly equal measure.

**More gallery exemplars.** Paula Scher's Public Theater as the Scher canon. Saville's *Blue Monday* sleeve as the ultimate form-as-violation discord. Experimental Jetset's Stedelijk identity as language-as-object.

**Skill-level quality-gate helper.** A small script that, given a new output and the last three, actually runs the 0.7 similarity reject on palette / layout / motion / type. Right now the gate is implicit; we want it explicit and cheap to invoke.

**A v0.1 release announcement** — short, in CC-PRO's own voice, pointing at the repo, the gallery page, and the prompting doc. Shared once the stack has cooked through a few live generations.

## Parked (possibly v1.0, possibly never)

**Commercial packaging.** Earlier research mapped a $39 / $299 / $2k tier structure with open-core + Stripe license and an Anthropic featured-skill partnership play. Not shipping. The skill stays free.

**Integrations.** Cursor / Windsurf / other Claude-adjacent clients. The skill format is portable; the work is mostly adaptation.

**A SaaS web app** — prompts in, generated pages out, hosted. The repo is a Claude skill; a SaaS would be a separate product built on top of it. No plan.

## How to steer the roadmap

Open an issue or a pull request on [GitHub](https://github.com/RayyanZahid/controlled-chaos-pro).

Exemplar contributions (a well-annotated case study for one of the five personas) are the highest-leverage thing anyone can add. Persona proposals are welcome but require a fully operationalized method document — stance, when-to-use, step-by-step, anti-patterns, gallery references. The bar isn't "does this designer have good taste." The bar is "does this method decompose into moves an LLM can execute."
