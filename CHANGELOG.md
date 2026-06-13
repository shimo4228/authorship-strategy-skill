# Changelog

All notable changes to this project will be documented in this file.

## [Unreleased]

### Added

- Layer 4 tactic: intrinsic identifier layer — SWHID (ISO/IEC 18670) complementing the extrinsic DOI layer; release-time archival in a content-addressed software archive (Software Heritage), with SWHID as the substitute priority-claim mechanism for DOI-impractical genres (authorship-strategy ADR-0013)
- Layer 4 tactic: citation-graph federation — machine-readable citation edges (`.zenodo.json` `references` + Wikidata P2860) whenever external literature is cited, making citations visible to scholarly citation graphs and cited researchers
- Layer 4 tactic: link-index-only contributions to external collections, with a four-condition pre-submission host audit (corporate ownership / absence of an open license / content-vendoring structure / paid-product funnel) and a standing withdrawal rule (authorship-strategy ADR-0012)
- Judgment checklist extended from twelve to fourteen items: machine-readable citation edges and link-index host audit added; the DOI-citable item amended with the SWHID substitute branch
- "Operating the strategy over time" section: a two-tier discipline (private implementation ledger vs public, dated, effect-claim-free intervention timeline) plus a periodic gap-review procedure (deployed tactics against the Layer 4 catalog, open questions, and recent literature → ranked candidate interventions through the judgment checklist) for running the strategy across sessions and generating new proposals. Generic/portable — project-specific wiring stays in the adopter's context file (authorship-strategy ADR-0014)
- Judgment checklist extended to fifteen items: the gap-review-before-proposing check added

### Planned

- Initial public release.

### What it does

A Claude Code skill that loads the four-layer judgment framework for *authorship strategy under AI-mediated diffusion* into an LLM-based coding agent's rule set. Provides the operational form of the [`authorship-strategy`](https://github.com/shimo4228/authorship-strategy) research line: trigger conditions, three-axis inversion, four-layer judgment stack, prohibited and encouraged actions, a fifteen-item judgment checklist, and an "operating the strategy over time" discipline (two-tier ledger + periodic gap-review).

### Components

- `skills/authorship-strategy/SKILL.md` — the skill body. Specifies trigger conditions, the three-axis inversion (scarcity → diffusion / exclusivity → derivation / enclosure → openness), the four-layer judgment stack (Authenticity → Attribution Diffusion → Idea vs Scaffold → Tactics), the catalogues of prohibited and encouraged actions, the fifteen-question judgment checklist (the vocabulary-discipline item follows authorship-strategy ADR-0010; the link-index audit item follows ADR-0012; the SWHID substitute branch follows ADR-0013; the gap-review item follows ADR-0014), and an "operating the strategy over time" discipline (two-tier ledger + periodic gap-review, ADR-0014).

### Scope

The skill is single-author normative and applies only to the author's own DOI-targeted idea-rescue research repositories. It deliberately does not apply to client work, contributions to others' projects, scaffold-only tooling, or decisions the author has explicitly placed outside the framework.

### Requirements

- No runtime dependencies. The skill is documentation-only; it shapes agent judgment by being loaded into the agent's rule set.

### Relationship to companion skills

| Skill | Role | When |
|---|---|---|
| `release-doi` | Release workflow | After this skill determines an artifact is in scope, the release workflow handles the deposit |
| `llms-txt-writer` | AI-facing documentation prose | At documentation-design time |
| `jsonld-knowledge-graph` | JSON-LD knowledge graph | When the artifact has stable concept-level structure |
| `context-sync` | Cross-document drift audits | Maintain phase |
