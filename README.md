# authorship-strategy-skill

A [Claude Code skill](https://docs.claude.com/en/docs/claude-code/skills) that loads the four-layer judgment framework for **authorship strategy under AI-mediated diffusion** into an LLM-based coding agent's rule set. Provides the operational form (trigger conditions, judgment checklist, prohibited and encouraged actions) of the normative framework articulated in the [`authorship-strategy`](https://github.com/shimo4228/authorship-strategy) research line.

The skill is **scoped to a narrow trigger**: it applies only to the author's own DOI-targeted idea-rescue research repositories, not to general client work or commercial deliverables. Adopting the skill commits the agent to the framework's core principle that authorship strategy under AI-mediated diffusion inverts on three axes (scarcity → diffusion, exclusivity → derivation, enclosure → openness).

## When to use

Apply the skill when **all** of the following hold:

- The current repository owner is the skill's adopter (the framework is single-author normative; adapting it to client work or contributions to others' projects is out of scope)
- The repository is a DOI-targeted or DOI-registered research artifact (Zenodo or comparable archive registration intended or in place)
- The artifact is an **idea-rescue** in character — specifications, schemas, ADRs, glossaries, or doctrine documents whose value is at the concept level rather than at the implementation level

Skip the skill if any one of those is missing. Specifically, skip for:

- Client work and commercial deliverables (monetization is the goal; the author's identity is not the protected value)
- Contributions to others' projects (the other author's strategy takes precedence)
- Operational tooling and scaffolding meant to dissolve (the artifact's diffusion outside its substrate is not desired)
- Day-to-day coding and debugging (the framework would be over-applied as a judgment instrument)

When in doubt, the framework defers to the author's explicit judgment rather than auto-applying.

## Install

### Claude Code

```bash
git clone https://github.com/shimo4228/authorship-strategy-skill
cp -r authorship-strategy-skill/skills/authorship-strategy ~/.claude/skills/authorship-strategy
```

No runtime dependencies. The skill is documentation-only; it shapes agent judgment by being loaded into the agent's rule set.

### Other harnesses

The skill body is a standard markdown file with a YAML frontmatter header. Adapt the install path to your harness's skill convention.

## How it works

1. **Trigger gate** — the skill checks four conditions (DOI-targeted, idea-rescue character, author's own work, not commercial) before applying. Misfires are explicitly cheaper than false negatives; when in doubt, the skill defers to author confirmation.
2. **Three-axis inversion as the core principle** — value source (scarcity → diffusion), validation mechanism (exclusivity → derivation), network effect (enclosure → openness). The three axes co-vary; mixing axes is internally inconsistent.
3. **Four-layer judgment stack** — Authenticity (Layer 1, the value) → Attribution Diffusion (Layer 2, the strategy) → Idea vs Scaffold (Layer 3, the prediction) → Tactics (Layer 4, the decisions). Each layer is downstream of the layer above; tactical decisions justified at Layer 4 must trace back to Layer 1.
4. **Prohibited and encouraged actions** — the skill blocks proposing monetization strategies, exclusionary competitive positioning, market-driven concept dilution, sensational framing, and over-scoped origin claims. It encourages DOI-citable structures, distinctive terminology coinage, abstract-doctrine-plus-worked-implementation pairs, friction-minimized adoption paths, and permissive licensing.
5. **Judgment checklist** — fifteen yes/no questions the agent runs against every proposal in the framework's trigger scope.
6. **Operating the strategy over time** — a two-tier discipline for running the strategy across sessions: a private implementation ledger (operational status, ranked candidate interventions) versus a public, dated, effect-claim-free intervention timeline, plus a periodic gap-review (deployed tactics against the tactic catalog and open questions) that generates the next proposals.

## Key concept: three-axis inversion is structural, not stylistic

The framework's strongest claim is that the three axes are not independent dimensions an author can freely mix. A strategy combining enclosure with derivation-welcoming license, or scarcity with crawler-friendly access, is *internally inconsistent* and weaker than either fully consistent strategy. The skill enforces this consistency: a Layer 4 tactic that violates the inversion on any axis is flagged regardless of how locally attractive it appears.

## What this skill does NOT do

| Concern | Use this instead |
|---|---|
| Release-time workflow for DOI-registered repos (verify, tag, deposit, propagate DOI) | [release-doi](https://github.com/shimo4228/release-doi) |
| llms.txt / llms-full.txt prose design, navigator wording | [llms-txt-writer](https://github.com/shimo4228/llms-txt-writer) |
| JSON-LD knowledge graph design | [jsonld-knowledge-graph](https://github.com/shimo4228/jsonld-knowledge-graph) |
| Cross-document drift audits | [context-sync](https://github.com/shimo4228/context-sync) |
| Article / blog post writing | [claude-skill-writing-ecosystem](https://github.com/shimo4228/claude-skill-writing-ecosystem) |

## Related research and skills

- **Doctrine repository**: [authorship-strategy](https://github.com/shimo4228/authorship-strategy) — the normative framework, five tactical ADRs, and empirical baseline this skill is the operational form of
- **Peer components** (other component skills of the same framework):
  - [release-doi](https://github.com/shimo4228/release-doi) — release-time workflow operationalizing the identifier-federation triplet (ADRs 0001-0003)
  - [llms-txt-writer](https://github.com/shimo4228/llms-txt-writer) — operationalizes Layer 4 tactic 7's Answer.AI `llms.txt` convention
  - [jsonld-knowledge-graph](https://github.com/shimo4228/jsonld-knowledge-graph) — operationalizes Layer 4 tactic 7's JSON-LD knowledge graph
- **Sibling research lines** (at the research-program level): [Agent Knowledge Cycle (AKC)](https://github.com/shimo4228/agent-knowledge-cycle), [Contemplative Agent](https://github.com/shimo4228/contemplative-agent), [Agent Attribution Practice (AAP)](https://github.com/shimo4228/agent-attribution-practice)

> **Terminology note.** This ecosystem reserves *sibling* for research-line-level peers; at the component-skill level the term *peer component* is used instead.

## License

MIT. See [LICENSE](LICENSE).
