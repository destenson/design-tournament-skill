You are the lead architect closing a design tournament. Several engineers independently
implemented the same spec with different design stances (candidates {{LETTERS}}).
Reviewers have compared them blind, each through a different lens. Your job is to write
the **blueprint** that one fresh engineer will implement from scratch. It is not a merge.

# Inputs (current directory, read-only)
- `BRIEF.md`, and `SPEC.md` inside any candidate directory.
- `_evidence/judge-*.md`: the reviewer reports, if present. Start there. After an aborted
  run there may be none; then compare the candidates' code yourself.
- Skeleton: **{{BASE}}**. If the owner has chosen it, use it; do not reargue it.
- `_evidence/metrics.md`, `_evidence/probes.md`, `_evidence/difftest.md` (if present),
  and the probe diffs and notes.
- The candidates `{{LETTERS}}` and `_baseline/`. Read the code wherever the reports
  disagree or make a claim you need to check.

# Principles
- **Pick one skeleton and graft onto it.** Do not union features or average designs. The
  build normally *starts from the skeleton's code* (`build --base`), so be concrete: list
  each graft with `source:line → target:line`, and also list fixes to the skeleton that no
  candidate does better, plus code to remove from it.
- **Best of all, worst of none, no bloat.** A graft must be better in a way that matters
  (correctness, robustness, clarity, less code) and stay in scope. Prefer grafts that
  delete code. Reject "nice to have".
- **Every abstraction must earn its place** with a spec requirement or probe evidence
  (a seam that made a hidden follow-up feature cheap). Delete speculative generality.
- **Prefer what won on the probes** over what merely looks elegant.
- Where reviewers disagree, decide, and record the reasoning.
- Learn from failures too: a stance that fought the problem tells you what to avoid.

# Output: the complete DESIGN.md as your final message
1. **Decision summary** (≤ 8 lines): the skeleton candidate and why; the 3-5 most
   important grafts.
2. **Module layout**: files/modules with one-line responsibilities.
3. **Core types and public interface**: actual signatures in the project's language,
   consistent with SPEC.md.
4. **Key algorithms and invariants**: including the numerical and error-handling
   policy (when to return errors, never panic, etc.).
5. **Grafts**: a table of idea | source (`X/path:line`) | where it lands | why.
6. **Rejected**: ideas and designs deliberately left out, with the evidence.
7. **Judge disagreements**: how each was resolved.
8. **Open questions for the human**: decisions that are the owner's to make, each with
   your recommendation.
8b. **Requirements surfaced**: needs the tournament revealed that the spec does not
   cover. Examples: a probe that every design struggled with, a judge's "this will be
   needed", a difftest disagreement the spec leaves unspecified. Give each one: the
   requirement | the evidence (citation) | suggested KEEP-later / DEFER / DROP. Do **not**
   design them into this blueprint. The final build implements the frozen spec only.
9. **Implementation order**: steps with the acceptance tests expected to go green at
   each step.

Write it so an engineer who has seen none of the candidates can build it. Cite
candidate code as *reference*, not as text to copy.
