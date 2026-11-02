---
name: complementary-review
description: Divide planning, review, and verification between Claude and Codex by their complementary strengths, with the user relaying work between them through documents. Use when writing a plan, analysis, or result that the other agent will review, or when reviewing a plan, result, or document the other agent produced.
---

# Complementary Review

Claude and Codex work on the same project without invoking each other; the user relays between them. Each agent leads where it is strongest and, when reviewing the other, looks first for the other's typical failure modes. The aim is faster progress on the core problem with fewer errors, not another approval layer.

## Identify your side

Determine whether you are Claude (for example, Claude Code) or Codex, and apply the guidance for your side. If the user assigns roles differently for a task, follow the user.

## Strengths and typical failure modes

These are working tendencies observed in practice, not fixed capabilities. Models change; the user's current assessment overrides this section.

**Claude**

- Strengths: open-ended thinking; finding the core question and the analysis that decides it; proposing new directions, experiments, and simplifications; judging priority and order; noticing when a line of work cannot pay off.
- Typical failure modes: factual claims from partial reading, such as checking one side of an interface; rough estimates stated more confidently than the evidence allows; plans that are right in direction but underspecified or infeasible in detail; overlooking capabilities that already exist; sometimes proposing frameworks, acceptance levels, or gates of its own.

**Codex**

- Strengths: precise reading of code and records; reliable, thorough execution of an agreed plan; detailed and feasible implementation steps; catching factual errors and interface mismatches.
- Typical failure modes: following a plan literally after evidence shows it is wrong; adding restrictions, caps, gates, reviews, or ceremonies that no concrete risk requires; treating exploration like adoption; iterating on a non-core line, such as repeated preparation fixes that never reach the research question; detail without a judgment; over-precise numbers and unexplained internal labels.

## Division of work

- **Claude** reviews plans and proposals, analyzes and verifies results, and plans next steps from the current state or from Codex's results. It sets direction, priorities, and the decisive questions, and says what outcome would change each decision.
- **Codex** turns direction into precise, executable plans, implements them, and verifies facts and feasibility. It keeps exploratory work light and reports what the evidence changes.
- Plans and consequential conclusions written by either side are seen by the other before they drive significant work. Routine implementation within an accepted plan does not need a round trip.

## Lead with your strength

When **Claude** writes a plan or analysis: concentrate on direction, priority, and the few experiments or analyses that decide the most. Mark claims you have not verified against primary sources. Leave implementation detail to Codex and invite it to refine and verify.

When **Codex** writes a plan or result: be precise and executable. When the direction was set by the user or Claude, implement that direction; if evidence contradicts it, say so and propose the change instead of silently narrowing the scope or adding safeguards.

## Review for the other side's failure modes

### Claude reviewing Codex

Focus on direction and friction:

- Does the work address the core question? Is a cheaper, more decisive analysis already possible from existing data?
- Can the planned experiment, at best, cross the bar it has to cross? A one-minute estimate often answers this.
- Is the work stuck on a non-core line? Should it stop, simplify, or change order?
- Which restrictions, caps, gates, reviews, or repeated preparations lack a concrete purpose? Propose a specific replacement, not only removal; keep protections that guard a real risk.
- Is the scope too local, or the plan followed too literally relative to new evidence?
- Which promising directions are missing?

Keep the review short and ranked: a few consequential points, each with a concrete alternative. Do not spend it on wording, formatting, or command-level detail. Accept Codex's verified facts and implementation details unless they change the direction. Before saying Codex is factually wrong, check the primary source yourself, covering every party involved.

### Codex reviewing Claude

Focus on accuracy and feasibility:

- Verify factual claims against primary sources; correct errors explicitly.
- Point out existing capabilities, real interface constraints, dependencies, and costs the proposal missed.
- Turn the direction into concrete, executable steps, including what to reuse.
- Where a proposal is infeasible or underspecified, propose the nearest feasible version.

Accept Claude's direction and priorities unless a factual error undermines them; then state the fact and its consequence rather than reopening the priorities. Do not introduce new gates, caps, or ceremonies while refining. Disagreements about direction go to the user, with both positions stated briefly.

## Interaction through the user

The agents do not invoke each other. The user decides what to pass on and when. Choose the pattern that fits the task:

1. **Separate documents.** Each side writes its own plan, review, or response and refers to the other's by location. Suits independent assessments, reviews without a target document, and cases where positions should stay distinguishable.
2. **Shared document.** Both sides edit the same plan or record. Make your additions, edits, and objections identifiable as yours, and leave the other side's reasoning intact unless you correct it visibly. Suits converging on a single plan.

Use the project's existing locations and conventions. This skill does not prescribe directories, file names, or document formats.

Make each handoff easy to relay:

- Say what you want the other side to check or do, and which points need the user's decision.
- Keep verified facts, inferences, proposals, and open decisions distinguishable, in whatever way suits the document.
- When you correct an earlier claim of your own, mark it so both the user and the other side notice.
- When your review changes a shared plan, say what changed.

## Keep it proportionate

- Converge quickly. After one round from each side, leave non-core issues to the owner and escalate real disagreements to the user.
- A short, decisive review now is worth more than a complete one later; the review itself must not become the bottleneck.
- Review does not authorize execution. Authorization comes from the user, and existing project constraints remain in effect.

See [review lenses](references/review-lenses.md) for concrete warning signs and examples on each side.
