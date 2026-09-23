# Durable Report Template

Create a report set, not one monolithic document:

```text
[report-directory]/
|-- analysis.md
`-- problems/
    |-- P1-[short-problem-name].md
    `-- P2-[short-problem-name].md
```

Use stable Goal, Problem, Route, logical element, Capability Slot, NFR, Claim, and Gap IDs across files. Relative links from `analysis.md` must resolve. The headings below are a report scaffold; choose the views and How subsections that explain the actual project.

## Main report: `analysis.md`

```markdown
# [Project] Problem-Driven Architecture Analysis

Analyzed revision: [commit / tag / branch / current checkout]
External research date: [YYYY-MM-DD or “not performed”]
Audience and scope: [included and excluded questions]

## Executive synthesis

[Problems the project demonstrably targets, chosen technical routes, cross-
problem product position, primary beneficiaries, quantified evidence, central
tradeoff, and most important unknown.]

## 1. Project Goal Discovery — WHY

| Goal ID | Desired outcome / why build | Largest pain | Affected actor | Success criterion | Evidence/confidence |
|---|---|---|---|---|---|

### Capability-to-goal coverage

| Public capability | Goal IDs | Evidence | Orphan / notes |
|---|---|---|---|

## 2. Problem-space index

| Goal ID | Baseline pain location / element | Problem ID and statement | Success criterion | Grouping rationale | Chosen Route ID | Detailed document |
|---|---|---|---|---|---|---|
| G1 |  | P1 — ... |  | Shared causal chain and comparable routes | R1 | [P1 details](problems/P1-name.md) |

[Use one row per Goal–Problem link, including separate pain locations when a
goal spans problems. Explain a split when goals share a topic but require
different baseline chains or architecture coordinates.]

# Part II — 2H

## 3. How much — quantified non-functional realization

| NFR ID | Goal/problem/slot | Attribute | Target/workload | Mechanism | Result and evidence class | Gap |
|---|---|---|---|---|---|---|

[Cover relevant performance, scale, latency, availability, reliability,
consistency, durability, resource, security, compatibility, and operability
requirements.]

## 4. How — architecture and implementation

[When several problems reuse an implementation, begin with a compact table
showing shared mechanism, reused implementation, scenario-specific entry or
policy, and divergence point. Omit the table when reuse is not material.]

### Traceability

| Goal / success criterion | Problem | Capability slots | NFR IDs | Implementing modules | Evidence/gap |
|---|---|---|---|---|---|

### Architecture choices and concrete implementation

[Choose project-specific subsections. Explain responsibility boundaries and
dependencies first. Trace representative uses from entry to outcome, including
branches, state changes, and code references. Deepen the mechanisms that own
the route's decisive behavior or a material NFR: contract, state, decision
rule, failure handling, and evidence. Choose C4, 4+1, use-case, state,
decision, or code views only where each answers a concrete question.]

### NFR realization

| NFR ID | Architecture mechanism | Verification artifact | Result | Residual risk |
|---|---|---|---|---|

## 5. Evidence, contradictions, and next checks

| Claim/Gap ID | Affected IDs | Claim or gap | Status/confidence | Source | Resolving check / owner |
|---|---|---|---|---|---|

## Conclusion

[What problems the project is evidenced to solve, which routes and slots it
occupies, who and when it fits, what quality is quantified, and what remains
unproven. Avoid a universal ranking.]
```

## Per-problem document: `problems/Px-name.md`

```markdown
# [P1] [Problem statement]

Goals: [G1, G2]
Research date/version scope: [...]

### Canonical logical vocabulary

| Element ID | Visible term | Definition / role | Introduced in baseline or Route ID |
|---|---|---|---|

## 1. Problem and success definition — WHY

| Goal ID | Baseline pain element/edge | Affected actor | Success criterion | Why grouped into this problem | Evidence |
|---|---|---|---|---|---|

## 2. Baseline architecture view

[Product-independent full system chain using canonical visible terms. Put the
line-style legend or direction cue inside the figure; verify request and
returned-data arrow directions. Mark pain, quantities, ownership, sources of
truth, and trust boundaries. Refer to visible terms, not diagram source IDs,
in prose.]

## 3. Solution-space view

| Route ID | Baseline element/edge | Technical route | Changed responsibility/guarantee | Benefits | Costs/risks | Known solutions | Status |
|---|---|---|---|---|---|---|---|

[Include rejected and unknown routes so coverage is exhaustive by responsibility.]

## 4. Target architecture views by route

| Route ID | Status | Target representation / rejection / unknown gap | Baseline intervention | Changed control/data paths | Responsibility owner | Residual pain |
|---|---|---|---|---|---|---|

### [R1] [Route]

[One entry for every Route ID. Use a full product-independent diagram for a
material structural change and for the analyzed project's chosen route. For a
local change, name the baseline elements and edges added, removed, moved,
split, or merged. For a rejected route give the rejecting constraint; for an
unknown route give the evidence gap. Label the intervention and any new
route-specific elements using the canonical vocabulary.]

## 5. Logical responsibility model

[First diagram contains responsibility/capability names only—no product names.
Distinguish control from data relationships.]

| Slot ID | Layer | Responsibility | Consumes | Provides | Dependencies | Control/data role | NFR obligation |
|---|---|---|---|---|---|---|---|

### Baseline and target elements to slots

| Baseline or Route ID | Element ID and visible term | Slot ID | Shared / optional / route-specific | Mapping rationale |
|---|---|---|---|---|

[Every baseline and viable target element has a slot; every slot has a source
element. Route-specific slots remain optional outside that route.]

## 6. Capability-slot projection — WHERE

| Capability slot | Current project | Direct competitor A | Indirect competitor B | Complement/dependency |
|---|---|---|---|---|

[Use component name, external/delegated, operator-supplied, absent, or unknown.]

### Competitor relationship

| Solution | Route ID | Direct / indirect / complement | Why | Residual pain / shifted responsibility |
|---|---|---|---|---|

## 7. Current-project contribution — WHAT

| Project capability/component | Slot | Operations / outcome | Preconditions | Boundary | Goal/evidence |
|---|---|---|---|---|---|

## 8. Participants and operating model — WHO

| Participant | Value / adoption reason | Operations | Visible data | Module/data owner | Incident responsibility | Collaboration |
|---|---|---|---|---|---|---|

[Include target customer, proof needed for adoption, adoption friction, and
non-fit customers.]

## 9. Temporal specification — WHEN

| Event/phase | Trigger | Preconditions | Ordering/deadline | State transition | Timeout/retry/fallback | Signal | Evidence |
|---|---|---|---|---|---|---|---|

[Include adoption timing, lifecycle timing, interaction timing, and service
timing.]

## 10. Problem-specific evidence gaps

| Gap | Affected decision | Resolving check | Owner |
|---|---|---|---|
```

The main report's executive synthesis must be reconstructible from goal, problem, route, element-to-slot, NFR, and claim traces. The problem documents own baseline/solution/target/WHERE/WHAT/WHO/WHEN detail; the main report owns How much and How. Cross-problem implementation reuse, when material, is explained at the start of How rather than in a separate architecture-position section.
