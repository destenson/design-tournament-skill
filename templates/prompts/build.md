You are implementing the final, approved design from a design tournament.

# Inputs
- `TOURNAMENT_DESIGN.md` (repository root): the blueprint. Follow it.
- `SPEC.md` and the acceptance tests in `{{FROZEN_PATHS}}`: the contract.
- `{{BLIND_DIR}}`: the read-only candidate implementations (`A/`, `B/`, …) that the
  design cites as references, plus the judges' reports in `_evidence/`.

# Brief
{{BRIEF}}

# Starting point: {{BASE}}
If a base candidate is named, this worktree already contains its code. **Graft, don't
rewrite**: keep the base's structure and apply exactly the grafts, fixes and removals the
design lists. Each graft goes into the base's structure, in its style. Anything the design
does not list stays as it is. If no base is named, implement the design from the spec
baseline.

# Rules
- Work in the order given under "Implementation order" in the design, running
  `{{TEST_CMD}}` at each checkpoint.
- Consult the cited candidate code for ideas, edge cases, and tricky algorithms. Do not
  copy whole files: write code that fits *this* design, with consistent naming and
  error handling throughout.
- You own `{{SCOPE_PATHS}}`. **Never modify `{{FROZEN_PATHS}}`.** Outside scope, make
  only the minimal mechanical edits.
- Build nothing beyond the spec and the design. **No bloat**: when a graft can be done by
  deleting or simplifying code, do that; never keep two ways of doing the same thing. If the design is wrong or impossible
  somewhere, deviate minimally and document it.
- Build: `{{BUILD_CMD}}`. Tests: `{{TEST_CMD}}`. Lint: `{{LINT_CMD}}`. All must be clean.
- Do not commit; the harness commits.

# DESIGN_NOTES.md (required, at the repository root)
1. Architecture in ≤ 10 lines.
2. **Deviations from TOURNAMENT_DESIGN.md** and the reason for each.
3. Known weaknesses and next steps.

Finish with: test status, LOC, and a list of deviations.
