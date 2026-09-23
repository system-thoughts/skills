---
name: problem-driven-architecture-analysis
description: "Analyze an existing software project through Problem-Driven Architecture Analysis: discover its goals and problem spaces, reconstruct baseline chains, derive solution routes and capability slots, position direct and indirect competitors, and explain What, Who, When, How much, and How with evidence. Use when a user wants to understand what a repository is trying to achieve, compare architectural solutions, or produce a durable project and ecosystem analysis. Do not use for ordinary code review, bug diagnosis, or feature implementation."
---

# Problem-Driven Architecture Analysis

Start from the project and reason backward to the problems it exists to solve. A goal names an observable outcome; a problem names the causal system chain that prevents it. Keep goals distinct, then group them only when their pains occur in the same baseline chain and their solution routes can be compared in one architecture coordinate system. Goals in one problem may have different success measures.

Keep four linked ledgers:

- **goal ledger:** project goals, business pain, success criteria, evidence;
- **problem ledger:** problem spaces, baseline pain locations, linked goals, and the reason each grouping shares one architecture coordinate system;
- **capability-slot ledger:** product-independent responsibilities and dependencies;
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

Follow the goal-discovery method in [references/goal-and-problem-analysis.md](references/goal-and-problem-analysis.md). For every distinct project goal answer:

- Why build or change this system?
- What is the largest business or operational pain?
- What observable outcome would prove the pain was solved?

Trace every major public capability to at least one goal. Keep unsupported motivation as inferred or unknown; keep a capability with no defensible goal as an orphan rather than inventing a story.

**Complete when:** goals are non-duplicative, each has a pain and success criterion or an explicit evidence gap, and every major capability is accounted for.

## 3. Build one problem document per problem space

Cluster goals by their causal baseline chain and comparable solution space, not by topic label. Trace each Goal ID through its baseline pain location to a Problem ID and success criterion; state why grouped goals belong together. Revisit provisional groups after reconstructing the baseline. For each problem, produce these artifacts in dependency order:

1. **canonical vocabulary and baseline architecture view:** stable logical element names and IDs, the complete system chain, and located pains;
2. **solution-space view:** first-principles intervention routes plus known industry solutions;
3. **target architecture entries:** one entry for every Route ID, showing how that route changes the baseline or why it is rejected or unknown;
4. **logical responsibility model:** product-free capabilities derived from the baseline and viable target views, with control and data relations distinguished;
5. **element-to-slot mapping:** trace baseline and target-view elements into shared, optional, or route-specific capability slots;
6. **capability-slot projection and WHERE:** map the current project and problem-specific competitors into those slots and identify their occupied layers and handoffs;
7. **WHAT, WHO, WHEN:** what this project contributes, the participant/ownership model, and its temporal specification.

Classify competitors only within a named problem:

- **direct competitor:** a different solution following the same technical route;
- **indirect competitor:** a solution following a different technical route to the same problem;
- **complement or dependency:** participates in the target architecture without competing for the same problem outcome.

Keep the same visible term for an element across a problem's diagrams; use diagram identifiers only in source, and put line-style legends and direction cues inside the figure. Check that request/control and returned-data arrows point in their actual directions. A route table row alone does not satisfy its target entry: a material structural change needs a full view, a local change needs an explicit baseline delta, and a rejected or unknown route needs its reason or evidence gap. Every viable target entry identifies the baseline intervention, changed control/data paths, responsibility owner, and residual pain.

**Complete when:** every Goal ID has a defensible problem linkage and pain location, including an explicit rationale when one goal spans problems; every Route ID has a matching target entry; each baseline and viable target element maps to a capability slot and each slot has a source element; every competitor has a route-derived relationship; and every concrete component maps to a product-independent slot.

## 4. Analyze the shared 2H

The main report's second half covers the project across all problem spaces.

### How much

Quantify non-functional requirements and realized quality: performance, scale, latency, concurrency, availability, reliability, consistency, durability, resource limits, security, compatibility, operability, and test/production evidence as relevant. Separate stated targets, implemented mechanisms, reproduced measurements, vendor benchmarks, and unknowns.

### How

Follow [references/implementation-analysis.md](references/implementation-analysis.md). Explain the architecture's responsibility split and dependencies first, then trace representative use cases into the concrete decisions, state, and code that produce the outcome. Select structural, sequence, state, domain, or code views for the question they answer; C4 and 4+1 are optional lenses, not a required set of sections. Tie mechanisms to goals, occupied slots, and How much evidence. When multiple problems reuse implementation, open How with a compact shared-mechanism/scenario-difference table showing where their paths diverge.

**Complete when:** every material NFR has a quantity or explicit measurement gap, and How links implementation mechanisms back to those requirements and the problem documents.

## 5. Synthesize at evidence strength

Apply [references/evidence-method.md](references/evidence-method.md). Keep baseline facts, project goals, solution possibilities, product claims, and analysis inferences visibly distinct. Make contradictions and missing measurements actionable.

The main report links every problem document and summarizes the goal portfolio, then presents How much before How. Its conclusion states what problems the project is demonstrably designed to solve, which route it chose, where it fits, and what remains unproven; it is not a universal product ranking.

## Completion criteria

The analysis is complete when:

- every major project capability maps to a supported goal or an explicit orphan;
- every goal-to-problem grouping follows a shared causal baseline chain and architecture coordinate system, with its grouping rationale recorded;
- each problem has a consistent vocabulary, baseline chain, exhaustive-by-responsibility solution space, one target entry per route, and a product-free logical responsibility model;
- baseline and viable target elements trace to capability slots in both directions;
- capability-slot tables place the project and problem-specific competitors in one architecture coordinate system;
- direct and indirect competitor labels follow technical routes within that problem;
- WHAT, WHO, and WHEN are answered inside each problem document, including operations, data visibility, module ownership, and incident ownership;
- the main report links all problem documents and contains evidence-backed How much followed by How that explains both architecture choices and the decisive component mechanisms in code;
- every material conclusion is traceable through the ledgers to repository or current external evidence.
