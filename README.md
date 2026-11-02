<h1 align="center">Complementary Review</h1>

<p align="center">
  <strong>Claude sets direction, Codex makes it precise, and each reviews the other for its typical failure modes.</strong>
</p>

<p align="center">
  <a href="skills/complementary-review/SKILL.md">
    <img alt="Claude Code Skill" src="https://img.shields.io/badge/Claude%20Code-Skill-d97706?style=flat-square">
  </a>
  <a href="skills/complementary-review/SKILL.md">
    <img alt="Codex Skill" src="https://img.shields.io/badge/Codex-Skill-2563eb?style=flat-square">
  </a>
  <img alt="Focus" src="https://img.shields.io/badge/focus-cross--agent%20review-0f8f88?style=flat-square">
</p>

<p align="center">
  <a href="#why">Why</a> &middot;
  <a href="#use">Use</a> &middot;
  <a href="#install">Install</a> &middot;
  <a href="README.zh-CN.md">中文</a> &middot;
  <a href="skills/complementary-review/SKILL.md">Skill Reference</a> &middot;
  <a href="LICENSE">MIT License</a>
</p>

`complementary-review` divides planning, review, and verification between Claude and Codex according to their strengths. The same skill installs on both agents; each reads the guidance for its own side. The agents never call each other: the user relays work between them through documents.

## Why

The two agents fail in different ways.

- **Claude** is strong at open-ended thinking, finding the core question, proposing directions, and judging priority. It can make factual errors from partial reading, state rough estimates too confidently, and leave plans underspecified.
- **Codex** is precise, thorough, and reliable in execution. It tends to follow plans literally, add restrictions and process no concrete risk requires, and keep iterating on a non-core line.

Each side therefore leads where it is strong, reviews the other for the other's typical failure modes, and accepts the other's judgment where the other is strong. Claude reviews direction and friction; Codex verifies facts and feasibility and refines direction into executable steps.

## What it changes

- Claude's reviews of Codex plans concentrate on the core question, experiments that cannot pay off, unnecessary limits, stuck lines of work, and missing directions, instead of wording or command-level detail.
- Codex's reviews of Claude plans concentrate on factual accuracy, existing capabilities, real interfaces, and feasible steps, without reopening agreed direction or adding new gates.
- Plans and consequential conclusions from either side are seen by the other before they drive significant work; routine implementation does not need a round trip.
- Handoffs say what the other side should check and which points need the user's decision.

The skill does not prescribe directories, file names, or document formats. It adds no scheduler, no approval gate, and no mandatory report, and it does not authorize execution.

## Interaction patterns

| Pattern | When it fits |
| --- | --- |
| Separate documents | Independent assessments, reviews without a target document, or positions that should stay distinguishable |
| Shared document | Converging on one plan; each side marks its own edits and objections and leaves the other's reasoning intact |

## Use

In Claude Code:

```text
/complementary-review Review Codex's plan at <path>. Focus on direction,
experiments that cannot pay off, and unnecessary limits. Mark what needs my decision.
```

In Codex:

```text
Use $complementary-review to refine Claude's plan at <path> into executable steps.
Verify its factual claims against the source and keep its direction.
```

Both agents can also select the skill automatically when a task involves writing or reviewing work exchanged with the other agent.

## Install

Clone the repository inside each agent's home and link the skill with a relative path. The installed skill then travels with the home: a backup of `~/.claude` or `~/.codex` stays self-contained and restores without depending on an external checkout. Inspect an existing destination before replacing it.

```bash
repo=https://github.com/xukp20/complementary-review.git

# Claude Code (user level)
mkdir -p "$HOME/.claude/tool-sources" "$HOME/.claude/skills"
git clone "$repo" "$HOME/.claude/tool-sources/complementary-review"
ln -s ../tool-sources/complementary-review/skills/complementary-review \
  "$HOME/.claude/skills/complementary-review"

# Codex
codex_home="${CODEX_HOME:-$HOME/.codex}"
mkdir -p "$codex_home/tool-sources" "$codex_home/skills"
git clone "$repo" "$codex_home/tool-sources/complementary-review"
ln -s ../tool-sources/complementary-review/skills/complementary-review \
  "$codex_home/skills/complementary-review"
```

Update an installation with `git -C <home>/tool-sources/complementary-review pull --ff-only`. For project scope in Claude Code, place the skill under the project's `.claude/skills` instead.

Start a new session, or reload the client, if skill discovery has not refreshed. Installation changes no global instructions, models, agent profiles, or permissions. `agents/openai.yaml` holds Codex interface metadata; Claude Code ignores it.

## Structure

- [SKILL.md](skills/complementary-review/SKILL.md): roles, review focus for each side, and interaction principles.
- [Review lenses](skills/complementary-review/references/review-lenses.md): concrete warning signs and examples for each side's failure modes.

## Validation

Both agents read the same `SKILL.md`, whose frontmatter uses only `name` and `description`. For Codex, run the validator bundled with `skill-creator`:

```bash
python /path/to/skill-creator/scripts/quick_validate.py skills/complementary-review
```

Syntax checks do not establish behavioral quality. Try the skill on a real plan review in each direction and check whether the review stays on the other side's failure modes and leaves its strengths alone.
