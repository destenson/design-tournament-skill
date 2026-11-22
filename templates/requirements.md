# Requirements ledger

Every requirement that comes up during the tournament gets exactly one decision.
That covers ideas from the brief, the spec agent, auditors, the user, judges, probes
and the synthesis.

| Decision | Meaning | Required column |
|---|---|---|
| `KEEP` | In this run's SPEC.md. | `Ref`: the behavior ID, e.g. `B12` |
| `DEFER` | Deliberately left for a later tournament. | `Ref`: a tracker issue (link or key) |
| `DROP` | Rejected. | `Why` |
| `?` | Not decided yet. `tourney freeze` refuses while any remain. | — |

Sources: `brief`, `user`, `spec`, `audit:<lens>`, `fold`, `judge:<lens>`, `probe:<name>`,
`synthesis`, `previous:<run>`.

Candidates never see this file. SPEC.md may list non-goals, but must never say that
something is planned for later, because candidates would design toward it.

| ID | Requirement | Source | Decision | Why | Ref |
|---|---|---|---|---|---|
