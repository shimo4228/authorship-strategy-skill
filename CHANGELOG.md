# Changelog

All notable changes to this project will be documented in this file.

## [Unreleased]

### Planned

- Initial public release.

### What it does

A Claude Code skill that loads the four-layer judgment framework for *authorship strategy under AI-mediated diffusion* into an LLM-based coding agent's rule set. Provides the operational form of the [`authorship-strategy`](https://github.com/shimo4228/authorship-strategy) research line: trigger conditions, three-axis inversion, four-layer judgment stack, prohibited and encouraged actions, and a twelve-item judgment checklist.

### Components

- `skills/authorship-strategy/SKILL.md` — the skill body. Specifies trigger conditions, the three-axis inversion (scarcity → diffusion / exclusivity → derivation / enclosure → openness), the four-layer judgment stack (Authenticity → Attribution Diffusion → Idea vs Scaffold → Tactics), the catalogues of prohibited and encouraged actions, and the twelve-question judgment checklist (the twelfth item — vocabulary discipline: coin sparingly, anchor densely — follows authorship-strategy ADR-0010).

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
