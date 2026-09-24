# Durable Report Shape

Produce a main report and one linked document for each defensible problem space:

```text
[report-directory]/
|-- analysis.md
`-- problems/
    |-- P1-[short-problem-name].md
    `-- P2-[short-problem-name].md
```

The shapes below are a reader's path, not mandatory headings or tables. Keep Goal, Problem, and Route identifiers stable where they help cross-file tracing. Element and capability-slot IDs are optional in the visible report; the same names and meanings must remain stable. Maintain the detailed goal, problem, route, slot, and claim ledgers during analysis, then disclose only the detail that helps readers understand the argument. Relative links from the main report must resolve.

## Main report: project portfolio and shared 2H

Open with the project and revision studied, research date, evidence scope, and a short synthesis of the problems, evidenced route coverage, primary beneficiaries, and largest unproven claim.

Give readers a compact goal portfolio and problem index. For each goal, show the desired outcome, affected actor, acceptance measure or measurement gap, and the problem document where its baseline cause is explained. A goal linked to several problems needs a separately justified link for each. Map major public capabilities to supported goals or mark them as unexplained; this coverage can be compact or placed in an appendix. The main report need not repeat each problem document's baseline narrative or grouping explanation.

Then explain the shared **How much** and **How**:

- **How much:** for each material non-functional requirement, distinguish intended target, workload and measurement boundary, implemented mechanism, observed result, and unknown. A configuration default or vendor benchmark is not a measured result for the analyzed deployment.
- **How:** explain the architecture's responsibility split, trace representative uses through actual components and code, then deepen the decisions, state, failure handling, and quality evidence that determine outcomes. When several problems reuse implementation, a compact shared-mechanism/scenario-difference table can open this section.

Close with the evidence status, contradictions and resolving checks, and a conclusion at the strength of the available evidence. Link every problem document. The main report owns cross-problem implementation detail; problem documents own their individual scenario and solution comparison.

## Problem document: a causal explanation

### 1. The scene and the original problem

State a recognizable trigger, relevant actors, completion boundary, and why the outcome matters. Draw the product-independent baseline from trigger to outcome. Distinguish control and data paths, authoritative sources, and ownership where they matter. Follow the diagram with a short walk-through of who requests, transfers, stores, and consumes what, and how those actions produce the pain and consequence; locate each important pain at a named element, relation, or handoff.

Use one visible name for each architectural element throughout diagrams, tables, and prose. Explain a newly abstracted element when readers first need it: its responsibility, input/output, and difference from neighboring elements. Established industry terms can retain their usual meanings. An optional glossary is an index, not a prerequisite for reading the first diagram.

### 2. WHY: why these goals belong here

Connect each linked goal to a pain in the baseline, the affected actor, the value of improving it, and an acceptance measure. Explain the causal path first; introduce measurement as a way to test improvement, without mechanically appending the same unknown-target disclaimer to every goal. State the causal reason several goals share this problem in ordinary language. Explain a cross-problem quality obligation separately rather than letting it merge unrelated scenarios. Refer to the main portfolio instead of repeating its full goal ledger. A concise table may orient readers, but use prose or short lists when a cell would otherwise contain several causal steps. Use emphasis and list labels to aid scanning, not as substitutes for readable sentences.

### 3. The solution space and its changes to the baseline

Show the intervention possibilities derived from the pain, with known industry solutions and meaningful rejected or unknown routes. A short overview can orient readers. For each Route ID, place its target entry near its explanation: identify the baseline intervention, added/removed/moved responsibilities, changed control and data paths, new owner, addressed goals, and remaining pain. Material structural changes need a full responsibility view; local changes can use an explicit baseline delta. A rejected route needs its constraint; an unknown route needs its evidence gap. Do not substitute an overview row for this entry. A product can realize several routes: map each evidenced contribution with its mechanism and enabling conditions instead of selecting one representative route for the whole product.

### 4. Compare the solutions

Abstract the baseline and viable targets into product-independent responsibilities and capability slots, then map their elements to those slots in the analysis. In the reader's document, use a scene-level architecture comparison only to the extent that it supplements the route target entries: show where relevant solutions intervene, what their paths and deployment boundaries change, and what remains external. Choose the clearest representation rather than requiring a responsibility diagram or a particular table. Keep full derivation or element-to-slot mapping in an appendix when it interrupts the comparison.

Compare complete candidate configurations for a stated goal and constraints. Establish their directional prerequisites first, then separately explain route coverage and similarity, substitution potential, and optional gain from using them together. The same pair may be substitutable and complementary under those conditions. Use direct/indirect competitor shorthand only after substitution has been established; do not turn route difference or coexistence alone into a competitor label. Let this comparison lead into WHERE and the current project's boundary.

### 5. The analyzed project's choice

Explain **WHAT** it delivers for this problem across its evidenced routes, what work remains with other systems, and the conditions under which it helps. Explain **WHO** benefits, adopts, operates, integrates, maintains relevant modules, sees which data, and handles incidents. Explain **WHEN** it enters the lifecycle and how ordering, deadlines, retries, retention, and recovery affect the outcome. Use diagrams, tables, or prose according to what makes these relationships easiest to follow.

Close with problem-specific evidence gaps and sources at the claims they support. The reader should be able to answer four questions without decoding research ledgers: What causes the problem? What solutions exist and how do they change the baseline? How do those solutions compare? What does this project contribute, for whom, and when?

## Delivery check

The narrative can be short or detailed, but its claims must remain traceable: each linked goal points to a baseline pain and acceptance measure; each route has a target entry; baseline and viable target elements map to slots in both directions; every evidenced route realized by the project appears; relevant complete solution configurations share a comparison coordinate; and the current project's boundaries, participants, temporal behavior, and implementation evidence remain explicit. Add a view, table, or ID only when it makes that explanation easier to use.
