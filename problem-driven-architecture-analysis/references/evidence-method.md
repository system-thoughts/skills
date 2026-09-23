# Evidence Method

Use this method for repository behavior, project intent, current products, solution-space research, and durable reports.

## Claim status

| Status | Meaning | Typical wording |
|---|---|---|
| **Observed** | Directly demonstrated by code, tests, configuration, schemas, artifacts, repository history, or reproduced behavior | “The implementation exposes…” |
| **Stated** | Asserted by maintainers, vendors, adopters, or standards authors but not independently demonstrated in this analysis | “The maintainers state…” |
| **Inferred** | Reasoned from multiple observations; alternative explanations remain possible | “This suggests…” |
| **Unknown** | Evidence is absent, inaccessible, stale, contradictory, or lacks measurement context | “The available evidence does not establish…” |

Confidence expresses evidence strength:

- **High:** reproduced behavior or multiple direct sources agree;
- **Medium:** one strong source or several consistent indirect sources;
- **Low:** weak, stale, ambiguous, or materially incomplete evidence.

Attach each claim to Goal ID, Problem ID, Route ID, Capability Slot ID, or NFR ID as appropriate. Use `cross-problem` only when evidence establishes the claim across all retained problems.

## Evidence layers

Keep these layers distinct:

1. **Baseline fact:** current actors, systems, flows, quantities, and pain before intervention.
2. **Project intent:** why maintainers say the project exists or changed.
3. **Implemented behavior:** what the analyzed revision demonstrably does.
4. **Solution possibility:** a first-principles route that may or may not have a product implementation.
5. **Product/vendor claim:** what an existing solution says it supports.
6. **Measured outcome:** benchmark, production case, experiment, or reproduced result with environment.
7. **Analysis inference:** architecture classification, tradeoff, or likely consequence derived from evidence.

Do not use implemented behavior alone to prove business motivation, or a vendor claim alone to prove measured success.

## Source fitness

Choose sources according to the claim:

1. Repository artifacts and reproduced behavior establish implementation.
2. History, ADRs, maintainer documents, issues, roadmaps, and talks establish intent and change rationale.
3. Official materials from each compared solution establish current behavior and positioning.
4. Standards and specifications establish protocols and guarantees.
5. Independent primary evidence, published benchmarks, and adopter reports establish outcomes.
6. Secondary sources assist discovery; identify them as secondary.

Prefer exact revisions, files, symbols, commands, configuration keys, releases, dates, workloads, and measurement environments. Verify recency for current external facts.

## Contradictions

Preserve conflicting evidence:

- documentation intent versus current code behavior;
- tests versus implementation;
- project goal versus orphan capability;
- configured limit versus published benchmark;
- maintainer value claim versus adopter outcome;
- one version, route, or deployment mode versus another.

Attach each side to its revision or date and state the check that would resolve the conflict.

## Negative and completeness claims

Classify boundaries as:

- **explicit exclusion:** specification or maintainers rule it out;
- **structural exclusion:** responsibility model or interfaces require material redesign;
- **operational limit:** possible but constrained by scale, latency, cost, security, topology, or workflow;
- **unobserved:** no path found; retain as unknown.

Treat “all possible routes” as **exhaustive by responsibility**: every diagnosed pain point and capability slot has a considered intervention, rejected route, or explicit unknown. Do not claim mathematical completeness.

## Quantitative claims

For every target, limit, benchmark, or outcome record:

- metric and units;
- workload/input and scale;
- percentile or aggregation window;
- hardware, network, topology, and configuration where relevant;
- software version and date;
- evidence class: configured, stated target, vendor benchmark, adopter case, or reproduced;
- comparison baseline.

A number missing material context is unknown for cross-solution comparison.

## Ledgers

### Claim ledger

| Claim ID | Goal/problem/route/slot/NFR | Claim | Evidence layer | Status | Confidence | Source | Conflict / next check |
|---|---|---|---|---|---|---|---|

### Contradiction and gap ledger

| Gap ID | Affected IDs | Missing or conflicting fact | Why it matters | Check that resolves it | Owner |
|---|---|---|---|---|---|

Working ledgers may remain in notes for a conversational answer. Durable reports include a compact evidence appendix and place unknowns beside the decisions they affect.
