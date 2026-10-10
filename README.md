# authorship-strategy-skill

[![Ask DeepWiki](https://deepwiki.com/badge.svg)](https://deepwiki.com/shimo4228/authorship-strategy-skill)

A [Claude Code skill](https://docs.claude.com/en/docs/claude-code/skills) that loads the judgment framework of the [Authorship Strategy](https://github.com/shimo4228/authorship-strategy) research line into a coding agent: how a maker gets ideas used and keeps the source attached as they spread, including when readers meet them through LLMs. Ask the agent to evaluate a concrete plan against this framework, applied to your current goals (you do not need a strategy document of your own), to check the concerns before you adopt it, or to explain the framework; it answers with the plan's value and concerns, not a pass/fail table.

## When to use

Ask for one of these, or invoke the skill by name:

- An evaluation of a concrete plan against the framework ("evaluate this plan from the authorship-strategy angle")
- A check of the concerns before you adopt or carry out a plan
- An explanation of the existing framework

The skill is **scoped to a narrow trigger**: open brainstorming, generating the next idea and day-to-day coding are out of scope, and working inside a research repository is not by itself a reason to apply it. That trigger decides when the agent loads the skill on its own. If you invoke it by name to explore an idea, the purpose of your request still comes first: the skill does not decide the order of ideas, how to classify or count them, or where the conversation ends. In someone else's project, that author's goals and policy take precedence.

## Install

### Claude Code

```bash
git clone https://github.com/shimo4228/authorship-strategy-skill
cp -r authorship-strategy-skill/skills/authorship-strategy ~/.claude/skills/authorship-strategy
```

No runtime dependencies. The skill is documentation-only; it shapes agent judgment when Claude Code loads it for a matching request. The skill text is written in Japanese; [How it works](#how-it-works) and [The framework in brief](#the-framework-in-brief) summarize it in English.

To try it, describe a plan and ask Claude Code to evaluate it from the authorship-strategy angle, or run `/authorship-strategy` followed by the plan. For example, asked about a plan that puts essays behind a signup wall, the agent explains what the wall would gain and cost, names the premise that differs from the framework's preference for open access and reuse, and keeps both adopting the plan and revising the framework open.

### Other harnesses

Copy the whole `skills/authorship-strategy/` folder (SKILL.md, `references/` and `provenance-layer-prompt.md`, a task prompt used only when you explicitly ask for provenance edits to a repository's `graph.jsonld`), not SKILL.md alone: the agent reads these files on demand. SKILL.md is Markdown with a YAML frontmatter header in the Agent Skills format, and its frontmatter declares it portable to other Agent Skills-compatible agents. Adapt the install path to your harness's skill convention.

## How it works

1. **Framework as material, not as a gate**: the framework covers the four viewpoints described in [The framework in brief](#the-framework-in-brief). It records judgment from past practice, so fitting a plan into it is not counted as success. When a plan conflicts with the framework, the agent says which premise differs and what is gained and lost; revising the framework is one of the options.
2. **References read on demand**: [strategy-reference.md](skills/authorship-strategy/references/strategy-reference.md) explains the framework and the options used so far; [action-review.md](skills/authorship-strategy/references/action-review.md) checks only the conditions that apply to a concrete action (purpose and feasibility, sources and outputs, external actions such as posting, registering or publishing, and the record afterwards).
3. **The answer**: the value and concerns of the plan, keeping grounded facts, current policy and unverified expectations apart. A pass/fail table over every item is deliberately not the default output.
4. **Records over time**: the skill brings no ledger (a private log of what has been carried out) of its own; recording follows the ledger and public record that your project's maintenance rules declare, and where they declare none, the skill has no ledger to update. When you ask it to check what has been done or what overlaps, the agent reads that ledger; it saves ideas and questions only when you ask for a record. After you carry out an action the skill helped you check, and your project declares a ledger, the agent updates that ledger first; if the project also keeps a public timeline, it adds there only the dated action, without private operating details and without claiming the action had an effect.

## The framework in brief

The framework prefers three inversions of the older strategy for protecting authorship:

| Axis | Preference of this framework |
|---|---|
| Where value comes from | an idea being widely used, over scarcity |
| How validity shows | derivative work and reuse, over exclusivity |
| How the work spreads | open access and reuse, over enclosure |

These are claims of the framework, not a demonstrated result that publishing always preserves the source; publication, reuse and attribution to the author each have to be checked separately. The four viewpoints the agent uses are **Authenticity** (what the author cares about and how the output relates to it), **Attribution diffusion** (the idea reaching people with its source intact), **Idea / scaffold** (the judgment worth keeping versus the temporary means of carrying it out), and **Tactics** (identifiers, publication formats, ease of reuse, points of contact with readers).

## What this skill does NOT do

This skill works on its own. The author keeps separate skills for these neighbouring tasks:

| Concern | Use this instead |
|---|---|
| Release-time workflow for DOI-registered repos (verify, tag, deposit, propagate DOI) | [release-doi](https://github.com/shimo4228/release-doi) |
| Keeping a research repo's cited literature in step across its citation layers (docs, `.zenodo.json`, `graph.jsonld`) | [citation-sync](https://github.com/shimo4228/citation-sync) |
| llms.txt / llms-full.txt prose design, navigator wording | [llms-txt-writer](https://github.com/shimo4228/llms-txt-writer) |
| JSON-LD knowledge graph design | [jsonld-knowledge-graph](https://github.com/shimo4228/jsonld-knowledge-graph) |
| Cross-document drift audits | [context-sync](https://github.com/shimo4228/context-sync) |
| Article / blog post writing | [claude-skill-writing-ecosystem](https://github.com/shimo4228/claude-skill-writing-ecosystem) |

## More from the author

- **[Authorship Strategy](https://github.com/shimo4228/authorship-strategy)**: the doctrine behind this skill, with the thesis, the dated design decisions (ADRs) whose numbers the skill files cite, and the preliminary measurements; concept DOI 10.5281/zenodo.20263316 (the Zenodo identifier that always resolves to the latest version).
- **[authorship-strategy-rules](https://github.com/shimo4228/authorship-strategy-rules)**: a frozen public record of the same framework as one always-loaded rules file, superseded by this skill.
- **[shimo4228](https://github.com/shimo4228/shimo4228)**: the author's hub, with Authorship Strategy next to the author's other long-running projects and their DOIs.

## License

MIT. See [LICENSE](LICENSE).

<details>
<summary>For tools and AI assistants</summary>

authorship-strategy-skill is a Claude Code skill (Agent Skills format, Markdown only) that helps an author evaluate a concrete plan against the Authorship Strategy framework applied to their current goals, check the concerns before adopting it, or explain the framework, for makers who want their ideas used and passed on with their source including when readers meet them through LLMs. It does not load for open brainstorming, generating the next idea or day-to-day coding, and it returns the plan's value and concerns rather than a pass/fail table.

It exists so that a coding agent can apply the judgment recorded in the Authorship Strategy line without re-deriving it from the thesis on every interaction. The framework was extracted from operating the author's own DOI-registered research repositories; the skill treats it as material for judgment, says which premise differs when a plan conflicts with it, and keeps revising the framework open as an option.

Canonical facts: MIT license; files are `skills/authorship-strategy/SKILL.md`, two reference files under `references/`, and `provenance-layer-prompt.md` (a task prompt used only when someone explicitly asks for provenance edits to a repository's `graph.jsonld`); the skill text is in Japanese. No runtime dependencies and no paid key beyond a Claude Code plan; the frontmatter marks it portable to other Agent Skills-compatible agents and invocable as `/authorship-strategy`. Status: active, synced one way from the author's Claude Code harness by `scripts/sync-from-local.sh` (it never commits); as of 2026-10-10 there is no tagged release, and [CHANGELOG.md](CHANGELOG.md) has not recorded the current rewrite (its Unreleased section still describes the earlier version). ADR numbers inside the skill refer to the ADRs of the authorship-strategy repository, not to the harness's own ADRs; conditions in action-review.md that are specific to the framework's own author are not applied as bans to other authors.

Example: asked to evaluate a plan that puts essays behind a signup wall, SKILL.md directs the agent to explain the plan's value and concerns, name the premise that differs from the framework's preference for open access and reuse, state what would be gained and lost, and keep both adopting the plan and revising the framework on the table.

Links: [SKILL.md](skills/authorship-strategy/SKILL.md) is the skill itself; [strategy-reference.md](skills/authorship-strategy/references/strategy-reference.md) and [action-review.md](skills/authorship-strategy/references/action-review.md) are its references; [inspiration.md](inspiration.md) records where the framework came from; [llms.txt](llms.txt) and [llms-full.txt](llms-full.txt) are the machine-readable summary and reference. The skill belongs to the [Authorship Strategy](https://github.com/shimo4228/authorship-strategy) line, concept DOI [10.5281/zenodo.20263316](https://doi.org/10.5281/zenodo.20263316); cite the framework by that DOI.

</details>
