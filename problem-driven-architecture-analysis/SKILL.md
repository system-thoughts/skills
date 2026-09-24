---
name: problem-driven-architecture-analysis
description: "Analyze an existing software project through Problem-Driven Architecture Analysis: discover its goals and problem spaces, reconstruct baseline chains, derive solution routes, locate the project's contributions, compare alternatives and combinations, and explain What, Who, When, How much, and How with evidence. Use when a user wants to understand what a repository is trying to achieve, compare architectural solutions, or produce a durable project and ecosystem analysis. Do not use for ordinary code review, bug diagnosis, or feature implementation."
---

# Problem-Driven Architecture Analysis

Start from the project and reason backward to the problems it exists to solve. A goal names an observable outcome; a problem names the causal system chain that prevents it. Discover candidate goals first, reconstruct the baseline, then confirm each goal's pain location and problem grouping. Goals in one problem may have different success measures.

Keep four linked ledgers:

- **goal ledger:** project goals, business pain, acceptance measures or targets, evidence;
- **problem ledger:** problem spaces, baseline pain locations, linked goals, and the reason each grouping shares one architecture coordinate system;
- **capability-slot ledger:** product-independent responsibilities, dependencies, and the project/route coverage of them;
- **claim ledger:** claim status, confidence, source, contradiction, and next check.

## Route the task

- For a full analysis, read [references/goal-and-problem-analysis.md](references/goal-and-problem-analysis.md), [references/implementation-analysis.md](references/implementation-analysis.md), and [references/evidence-method.md](references/evidence-method.md).
- For current products, competitors, adoption, releases, benchmarks, or standards, research current first-party sources and apply the evidence method.
- For a durable deliverable, read [references/report-template.md](references/report-template.md). Produce one main report plus one linked document per problem space.
- For a requested subset, establish the minimum goal and problem frame first, then load only the reference sections needed for that subset.

## 1. Establish scope

Identify the repository, revision, research date, audience, and deliverable. Separate maintainer intent from implemented behavior. Use code, tests, configuration, schemas, entry points, deployment assets, history, issues, roadmaps, official use cases, and adopter evidence.

**Complete when:** revision, dates, evidence scope, excluded material, and deliverable location are explicit.

## 2. Discover project goals — WHY

Follow the goal-discovery method in [references/goal-and-problem-analysis.md](references/goal-and-problem-analysis.md). For every candidate project goal answer:

- Why build or change this system?
- What is the largest business or operational pain?
- What observable outcome would show that the pain has improved?

Trace every major public capability to at least one goal. After drawing the baseline, revisit the candidates: point to the causal pain, revise or split goals that do not fit, and state how improvement could be recognized. Explain the scene, causal pain, and value before introducing acceptance measures; use measures to test the claim, not as fragments appended to every goal sentence. A measurement plan is not evidence of achieved success; record an unstated target or threshold as unknown without repeating the same caveat after every paragraph. Keep unsupported motivation as inferred or unknown; keep a capability with no defensible goal as an orphan rather than inventing a story.

**Complete when:** goals are non-duplicative, each has a baseline-grounded pain and an observable acceptance measure or explicit gap, and every major capability is accounted for.

## 3. Build one problem document per problem space

Link a goal to a problem only when its pain can be located on that problem's baseline and an intervention there could plausibly improve the goal. Group several goals only when they share a causal baseline chain **and** their solution routes can be compared in one architecture coordinate system; a shared topic or customer is insufficient. Explain the specific causal relationship in ordinary prose. A cross-problem quality obligation may apply to several problem documents without merging their problems.

Research artifacts need not become a sequence of tables in the reader's document. Build each problem document around four connected questions:

1. **What is the problem?** Establish the concrete scene, reconstruct the product-independent baseline from trigger to outcome, explain how pain arises there, then ground each linked goal and its acceptance measure in that chain.
2. **What solutions exist?** Derive intervention routes from the baseline, name known solutions, and give every route a target architecture entry that explains its change or its rejection/uncertainty. Map the analyzed project's implemented capabilities to every route they actually realize; routes need not partition products.
3. **How do solutions compare?** Derive product-independent responsibilities and capability slots from the baseline and viable targets, trace elements to slots, and use a scene-level architecture comparison to show how the routes and concrete solutions change the original system. Choose a view that helps readers locate the solutions and understand their differences; the logical model can remain an analysis ledger or appendix when its full display adds no clarity.
4. **What does this project contribute?** Explain WHAT, WHO, and WHEN across its evidenced route coverage, including boundaries, beneficiaries, collaborators, owners, and temporal behavior.

For solution relationships, first complete each candidate with its required dependencies. Then assess route coverage, substitutability under a stated goal and constraints, and the incremental value of using solutions together. Record dependencies directionally; co-deployment alone is not a combination benefit. Substitutability and combination benefit can both hold. Use direct/indirect competitor only as a shorthand after substitution is established, distinguishing similar from different primary intervention mechanisms.

Keep one visible name and one meaning for each architectural element across a problem's diagrams, tables, and prose. Explain a newly abstracted element when the reader first needs it: its responsibility, input/output, and distinction from adjacent elements. Describe actors, actions, and transferred or stored objects in concrete language; format lists and emphasis to help scanning rather than compressing a causal explanation into labeled fragments. Use established industry terms in their usual sense; explain local deviations. Element IDs and a glossary are optional aids to traceability, not mandatory diagram labels or opening sections. Put line-style legends and direction cues inside figures when useful, and check that request/control and returned-data arrows point in their actual directions. A route overview row alone does not satisfy its target entry: a material structural change needs a full view, a local change needs an explicit baseline delta, and a rejected or unknown route needs its reason or evidence gap. Every viable target entry identifies the baseline intervention, changed control/data paths, responsibility owner, and residual pain.

**Complete when:** a reader can follow the baseline pain to each linked goal, understand the available routes and their changes, locate and compare solutions in the original system, and explain the current project's contribution without first decoding ledgers or IDs. Every goal linkage has a defensible pain location; every route has a target entry; baseline and viable target elements trace to capability slots in both directions; all evidenced project routes are represented; and solution relationships distinguish prerequisites, replacement potential, and optional combination gain.

## 4. Analyze the shared 2H

The main report's second half covers the project across all problem spaces.

### How much

Quantify non-functional requirements and realized quality: performance, scale, latency, concurrency, availability, reliability, consistency, durability, resource limits, security, compatibility, operability, and test/production evidence as relevant. Separate stated targets, implemented mechanisms, reproduced measurements, vendor benchmarks, and unknowns.

### How

Follow [references/implementation-analysis.md](references/implementation-analysis.md). Explain the architecture's responsibility split and dependencies first, then trace representative use cases into the concrete decisions, state, and code that produce the outcome. Select structural, sequence, state, domain, or code views for the question they answer; C4 and 4+1 are optional lenses, not a required set of sections. Tie mechanisms to goals, occupied slots, and How much evidence. When multiple problems reuse implementation, open How with a compact shared-mechanism/scenario-difference table showing where their paths diverge.

**Complete when:** every material NFR has a quantity or explicit measurement gap, and How links implementation mechanisms back to those requirements and the problem documents.

## 5. Synthesize at evidence strength

Apply [references/evidence-method.md](references/evidence-method.md). Keep baseline facts, project goals, solution possibilities, product claims, and analysis inferences visibly distinct. Make contradictions and missing measurements actionable.

The main report links every problem document and summarizes the goal portfolio, then presents How much before How. Its conclusion states what problems the project is demonstrably designed to solve, which routes it realizes, where it fits, and what remains unproven; it is not a universal product ranking.

## Completion criteria

The analysis is complete when:

- every major project capability maps to a supported goal or an explicit orphan;
- every goal-to-problem grouping follows a shared causal baseline chain and architecture coordinate system, with its specific causal rationale explained in readable prose;
- each problem has consistent names for architectural elements, a baseline chain, exhaustive-by-responsibility solution space, one target entry per route, and a traceable product-free logical responsibility model in the analysis;
- baseline and viable target elements trace to capability slots in both directions;
- the report's architecture comparison makes each relevant solution's intervention and deployment location clear, supplements the route target entries, and leads to WHERE and solution relationships;
- every evidenced route implemented by the project is mapped, including conditional coverage, without forcing one product into one route;
- solution comparisons state their goal and constraints, complete candidates with dependencies, and assess route similarity, substitution, and combination gain separately;
- WHAT, WHO, and WHEN are answered inside each problem document, including operations, data visibility, module ownership, and incident ownership;
- the main report links all problem documents and contains evidence-backed How much followed by How that explains both architecture choices and the decisive component mechanisms in code;
- every material conclusion is traceable through the ledgers to repository or current external evidence;
- the problem document reads as an explanation of problem, solutions, comparison, and current-project fit, rather than a display of the ledgers used to research it.
