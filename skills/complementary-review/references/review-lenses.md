# Review Lenses

Concrete warning signs for each side's typical failure modes. They are prompts for judgment, not a checklist to complete. The examples are generalized from real collaboration and illustrate the pattern; they are not rules.

## Signs to look for in Codex's work

**The experiment cannot answer its question.**
- The total measured cost at the chosen site is smaller than the improvement threshold it must pass, so even eliminating it entirely cannot succeed.
- The ranking or cost model was already contradicted by an earlier measurement, for example two parts of similar size that take very different time.
- A protection rule guarantees rejection of the very class of candidates being tested.
- A second attempt repeats the same mechanism with the same expected effect as a failed first attempt.

**Discovering interface errors the expensive way.**
- A full baseline is rerun several times to find path, permission, or import-convention errors that a ten-line project would expose in seconds.
- A long pipeline fails at the end on a capacity limit that could have been counted before it started.
- Mock tests stand in for one cheap test against the real tool.

**Limits without a purpose.**
- A file-size, memory, or count cap is lower than normal output and kills healthy runs.
- One busy or transient signal discards a whole attempt and forces re-preparation.
- Adoption-level requirements (full certification, API contracts, identity proofs) are applied to exploratory candidates.
- Each small fix triggers a new frozen package, a new review, or a new approval.

**Stuck on a non-core line.**
- Several rounds of preparation fixes, none of which reaches the research question.
- Iterating on one narrow variant after its ceiling is already visible.
- Analysis stops at "not comparable" or "cannot attribute" instead of proposing the comparison that would decide.

**Detail without judgment.**
- Six significant figures from four samples.
- Internal identifiers that require a lookup table to read.
- Caveats longer than the conclusion, with no statement of which experiment would resolve them.

What to offer instead: the decisive analysis, the cheaper ordering, the concrete replacement for a limit, or the decision to stop a line.

## Signs to look for in Claude's work

**Facts from partial reading.**
- A claim about how a lock, interface, or protocol behaves, based on reading only one of its callers.
- Treating a historical artifact's identity as established from its name or layout.
- A number taken from a summary rather than its source.

**Confidence beyond the evidence.**
- A ceiling or decomposition derived from measurements taken under different conditions, without saying how that limits it.
- A recommendation that assumes an interface, option, or data source that does not exist.

**Underspecified or costly plans.**
- A direction with no feasible first step in the actual codebase.
- Missed existing capabilities, so the plan proposes rebuilding them.
- Too many parallel directions for the coordination capacity available.

**Its own gates.**
- "Build the evaluation infrastructure first," acceptance levels, score cards, frozen thresholds, or lineage ledgers that turn into prerequisites for exploration.

What to offer instead: the corrected fact with its source, the existing capability to reuse, and the nearest feasible version of the proposal, keeping its direction.
