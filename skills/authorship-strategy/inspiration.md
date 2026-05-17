# Inspiration / Origin

This file records the canonical implementation that originated the
`authorship-strategy` skill. Kept separate from `SKILL.md` so the
skill stays portable to other authors who do not share this origin
context.

## Origin

The framework articulated in this skill was extracted from operating
four DOI-registered sibling research repositories in the same author's
research program — [`agent-knowledge-cycle`](https://github.com/shimo4228/agent-knowledge-cycle)
(DOI 10.5281/zenodo.19200726), [`contemplative-agent`](https://github.com/shimo4228/contemplative-agent)
(DOI 10.5281/zenodo.19212118), [`agent-attribution-practice`](https://github.com/shimo4228/agent-attribution-practice)
(DOI 10.5281/zenodo.19652013), and the federation hub
[`shimo4228/shimo4228`](https://github.com/shimo4228/shimo4228) —
during the year of operation that culminated in the four-axis 2026-05
ecosystem federation work.

The framework was not deduced from prior literature. It was articulated
by noticing recurring tactical decisions across the four lines,
formalized as a four-layer judgment stack and a three-axis inversion,
and re-expressed in harness-neutral form so adopters could install the
skill without inheriting the original sibling-line content.

## Canonical doctrine repository

The skill's operational form lives in this repository
(`claude-skill-authorship-strategy`). The framework's *normative
articulation* — the full thesis, the five tactical ADRs, the empirical
baseline, the glossary, the manifesto of open questions, and the
lineage to prior literature — lives in the doctrine repository:

> [`authorship-strategy`](https://github.com/shimo4228/authorship-strategy)

The doctrine repository is independently DOI-registerable and is being
released as the fourth sibling research line in the author's program.
The skill exists to make the framework loadable into LLM-based coding
agents without requiring the agent (or its operator) to re-derive
judgment from the thesis on every interaction.

## Lineage to existing skills

Two existing skills in the author's ecosystem informed the operational
shape of this one:

- [`claude-skill-jsonld-knowledge-graph`](https://github.com/shimo4228/claude-skill-jsonld-knowledge-graph) and [`claude-skill-llms-txt-writer`](https://github.com/shimo4228/claude-skill-llms-txt-writer) supplied the *AI-facing documentation* tactics that became Layer 4 entries in the framework. The skill assumes both are installed when the framework's tactics call for `llms.txt` / `graph.jsonld` artifacts.
- [`claude-skill-context-sync`](https://github.com/shimo4228/claude-skill-context-sync) supplied the *cross-document drift detection* discipline that the framework's maintenance layer presupposes. The framework treats drift as a structural failure mode rather than as a one-time defect.

## Lineage to memory

The framework's tactical layer was specifically informed by seven
project memory entries the author had accumulated by May 2026:
graph.jsonld validation observations, multilingual README policy
decisions, ORCID enrichment discipline, Zenodo relatedIdentifiers
federation, the concept-versus-version DOI drift incident, Hugging Face
Datasets cross-federation patterns, and a catalogue of authorship-strategy
judgments (skip decisions on Wikidata, arXiv, Semantic Scholar). Each
memory entry was converted into a corresponding ADR in the doctrine
repository; the skill summarizes the resulting framework rather than
duplicating each ADR.

## When this skill becomes obsolete

The framework's Layer 3 explicitly predicts that scaffolds dissolve.
This skill is itself a scaffold: it loads the framework's operational
form into a specific class of harness (LLM-based coding agents). When
LLM-mediated coding shifts to a different interaction substrate — for
example, when persistent agent memory makes the per-session
rule-loading model obsolete, or when authorship-strategy framework
adoption becomes widespread enough that re-derivation from doctrine is
the norm rather than the exception — this skill should be retired in
favor of whatever loading mechanism the new substrate supports. The
framework itself, the doctrine repository content, is the artifact the
framework's own Layer 3 commits to preserving across substrate shifts.
