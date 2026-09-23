# Goal and Problem Analysis

This is the front half of Problem-Driven Architecture Analysis. Preserve the dependency order: **project goals → problem spaces → baseline → solution routes → target views → logical responsibilities → capability slots → WHERE / WHAT / WHO / WHEN**.

## 1. Project Goal Discovery — WHY

Begin with the analyzed project, not a preselected market category. Discover goals by triangulating:

- mission, README, design documents, roadmaps, release notes, talks, issues, and ADRs;
- entry points, public interfaces, commands, adapters, state models, and deployment modes;
- tests and failure handling that reveal protected outcomes;
- adopter stories, operational guidance, and repeated user requests;
- history that explains why a subsystem was introduced or changed.

Maintain a goal ledger:

| Goal ID | Project goal | Largest pain | Affected actor | Success criterion | Status | Evidence |
|---|---|---|---|---|---|---|
| G1 |  |  |  |  | observed / stated / inferred / unknown |  |

For each candidate goal answer:

1. Why build or change this system?
2. What business or operational pain is large enough to justify it?
3. What observable outcome would prove that pain was solved?
4. Which public capabilities exist to achieve this goal?
5. Which evidence establishes intent, implementation, and outcome separately?

Split goals when their desired outcomes, pains, or success measures differ; merge wording variants of the same outcome. A goal states an observable improvement for an actor. A mechanism states how a system might achieve it; classify the mechanism as a route or capability unless evidence establishes a distinct outcome. Classify concerns shared by several problems from their evidenced outcomes and responsibilities: they may be goals, quality constraints, or enabling capabilities. Keep that classification open when evidence is insufficient.

Classify success criteria:

- **business outcome:** cost, adoption, revenue, time-to-market, risk, user experience;
- **operational outcome:** latency, throughput, source load, recovery, operator effort;
- **quality constraint:** availability, durability, security, compatibility, resource ceiling;
- **proxy metric:** a measurable signal used when the outcome itself is hard to observe.

Record the target, unit, workload, environment, percentile/window, and source when available. A metric without this context is incomplete. If maintainers state no measurable target, define the measurement needed and mark the threshold unknown.

### Goal coverage test

Create a capability-to-goal matrix. Every major public capability must map to one or more goals. Mark capabilities with no defensible goal as **orphan capabilities**; they may be legacy, enabling infrastructure, or evidence of a missing goal. Do not invent motivation to close the matrix.

Goal discovery is complete when goals are non-duplicative, each has a pain and a success criterion or explicit gap, and every major public capability is mapped or orphaned.

## 2. Cluster goals into problem spaces

A problem space is the causal baseline chain that gives rise to one or more goals' pains. Goals with different metrics may share a problem when their pains occur in that chain and their technical routes can be compared in one architecture coordinate system. A shared topic or customer label alone is insufficient. Start with provisional groups, then confirm or split them after reconstructing the baseline. Keep separate documents when goals require different:

- baselines or sources of pain;
- responsibility models;
- technical route families;
- competitor sets;
- ownership or temporal models that change the solution space.

Maintain the goal-to-problem trace and grouping rationale:

| Goal ID | Baseline pain location / element ID | Problem ID | Success criterion | Why this problem groups the goal | Evidence |
|---|---|---|---|---|---|
| G1 |  | P1 |  | Shared causal chain and comparable routes |  |

Maintain one problem ledger row per problem:

| Problem ID | Product-independent problem statement | Goal IDs | Shared baseline chain | Architecture coordinate / route family | Grouping rationale | Evidence status |
|---|---|---|---|---|---|---|
| P1 |  | G1, G2 |  |  |  | designed / implemented / extension-supported / plausible |

State each problem without naming the current project or its chosen mechanism. Confirm that each mapped pain can be pointed to in the baseline and that the same responsibility slots can compare the routes. A goal may link to several problems only when each link has its own pain location and causal rationale; otherwise move it to the problem where those conditions hold or classify it as a shared quality obligation.

## 3. Reconstruct the baseline architecture

The baseline is the complete system chain before the analyzed solution intervenes. Reconstruct it from trigger to business outcome:

1. demand or initiating event;
2. actors and calling systems;
3. control decisions and policy checks;
4. authoritative state and data sources;
5. transformations, transfers, storage, and execution;
6. consumption and observable outcome;
7. feedback, monitoring, and recovery;
8. organizational ownership and trust boundaries.

Before drawing, establish a per-problem vocabulary of logical elements: stable element ID, visible name, definition, and role. Reuse the same visible name and meaning in baseline, solution-space references, target views, and the logical responsibility model. Add a new element only when a route adds a new responsibility; do not force different problem spaces to share a vocabulary.

Draw control relationships and data relationships with different edge styles or separate views. Put the line-style legend or direction cue inside the figure when it can be expressed there. Treat diagram IDs as source-only identifiers: refer to visible element names in explanatory prose. Verify the direction of each request, command, response, and data transfer separately. Mark where latency, cost, failure probability, inconsistency, manual coordination, or risk accumulates. Quantify the bottleneck when evidence exists.

The baseline contains responsibility names, not product or repository component names. A product can be mentioned only as evidence that a real deployment uses the baseline.

Baseline completion test:

- every input reaches an outcome or explicit dead end;
- control and data paths are distinguishable;
- authoritative state and ownership are visible;
- each stated pain is located at a step, edge, queue, store, or handoff;
- the goal-to-problem trace uses those pain locations and the figure's visible element names;
- control and returned-data arrows point in their actual directions;
- removing the current project from the story does not make the baseline unintelligible.

## 4. Derive the solution space from first principles

Treat the baseline as a constraint system. For every pain point ask which responsibility, dependency, quantity, location, time, or guarantee can change.

Search these intervention families where relevant:

- eliminate or reduce demand;
- reduce the amount of work or data;
- reuse completed work through caching, deduplication, or memoization;
- move work earlier, later, closer, or to another owner;
- parallelize or distribute work;
- increase bottleneck capacity or replicate the bottleneck;
- change representation, protocol, algorithm, or consistency guarantee;
- precompute, pre-position, batch, or schedule demand;
- degrade, shed load, or narrow the promised outcome;
- remove a coordination handoff through automation or a different trust model.

These are search prompts, not a fixed taxonomy. Derive the actual technical routes from the problem's responsibilities and constraints.

Maintain a route ledger. Its intervention point references a baseline element or edge, and its status determines the required target entry:

| Route ID | Baseline element/edge | Technical route | Changed responsibility/guarantee | Benefits | Costs/risks | Known solutions | Status |
|---|---|---|---|---|---|---|---|
| R1 |  |  |  |  |  |  | viable / rejected / unknown |

Research current industry solutions for every material route. Include open-source projects, managed products, standards, and common operational workflows when they occupy the solution space. Use first-party sources for current behavior. Record rejected routes and the constraint that rejects them.

The solution space is **exhaustive by responsibility** when every diagnosed pain point and capability slot has at least one considered intervention, and every route is either represented, rejected with reason, or marked unknown. Do not claim mathematical completeness.

## 5. Close every route with a target architecture entry

Create a target entry with the same Route ID for every route ledger row. For a viable route, show how the baseline changes:

- responsibilities added, removed, moved, split, or merged;
- new control and data paths;
- source of truth and cache ownership;
- trust and failure boundaries;
- new dependencies and operational owners;
- which pain and success criteria the route addresses;
- which pain remains.

Give materially different structures a full target diagram. For a local change, a normalized delta from the baseline is sufficient if it explicitly names added, removed, moved, split, or merged elements and edges. Give the analyzed project's chosen route a full target view. A rejected entry records the rejecting constraint; an unknown entry records the evidence gap. The route ledger row alone is not a target entry.

For each viable entry, identify the baseline element or edge it intervenes at, changed control and data paths, new or shifted responsibility owner, and residual pain. Use stable visible terms and element IDs across the baseline and all target views; label route-specific elements and the route's intervention location in the view.

Check route closure with:

| Route ID | Status | Target representation / rejection / unknown gap | Baseline intervention | Changed control/data paths | Responsibility owner | Residual pain |
|---|---|---|---|---|---|---|
| R1 |  |  |  |  |  |  |

Target views remain product-independent. Product components are mapped only after the logical responsibility model is stable.

## 6. Build and trace the logical responsibility model

Abstract the baseline and every viable target view into the capabilities required to produce the outcome. A **capability slot** is one product-independent responsibility with a defined input, output, dependency, owner, and quality obligation. The model is a union of possible responsibilities, not a claim that every route needs every slot.

Derive layers from dependency direction:

1. name the outcome-producing responsibilities;
2. state what each responsibility consumes and provides;
3. draw dependency edges;
4. separate control dependencies from data dependencies;
5. topologically group responsibilities into logical layers;
6. identify optional slots, route-specific slots, and shared cross-cutting slots.

Use this slot schema:

| Slot ID | Logical layer | Responsibility | Consumes | Provides | Depends on | Control/data role | NFR obligation |
|---|---|---|---|---|---|---|---|
| CS1 |  |  |  |  |  | control / data / both |  |

The first responsibility diagram must contain no product names. Its purpose is to define the architecture coordinate system before implementation choices bias it.

Trace elements in both directions:

| Route ID or baseline | Target/baseline element ID and visible name | Slot ID | Shared / optional / route-specific | Mapping rationale |
|---|---|---|---|---|
| Baseline |  | CS1 |  |  |

Every baseline and viable target element maps to at least one slot. Every slot cites at least one source element; split an element or slot whose mapping hides independent responsibilities. A route-specific slot remains optional for routes that do not use it. This mapping precedes the product-component projection.

## 7. Project solutions into capability slots — WHERE

Create one projection table per problem. Rows are the stable capability slots; columns are the analyzed project and that problem's solutions. Map concrete components into cells:

| Capability slot | Current project | Solution A | Solution B | Operational workflow |
|---|---|---|---|---|
| CS1 — responsibility | component / external / absent |  |  |  |

Use explicit cell values:

- component or module name when the solution owns the slot;
- **external/delegated** when another system supplies it;
- **operator-supplied** when deployment teams must provide it;
- **absent** when the route intentionally removes the slot;
- **unknown** when evidence is insufficient.

WHERE is the resulting set of occupied slots, layers, and handoffs. A solution can span multiple layers. Explain whether its product boundary is narrow, end-to-end, or ecosystem-composed.

## 8. Classify competitors from the route ledger

Competitor labels are local to a problem:

- **Direct competitor:** follows the same technical route and competes through a different implementation, operating model, or optimization focus.
- **Indirect competitor:** follows a different technical route to resolve the same business or operational problem.
- **Complement or dependency:** fills a required slot without independently promising the same problem outcome.

The same product may be direct in one problem, indirect in another, and a complement in a third. State the problem ID and route ID with every label.

Compare direct competitors through the same capability-slot table and implementation axes. Compare indirect competitors through route-level benefits, residual pains, and shifted responsibilities rather than feature totals.

## 9. WHAT — current-project contribution

For each problem, focus on what the analyzed project contributes:

- occupied capability slots and concrete components;
- accepted inputs, operations, outputs, and observable outcomes;
- owned versus delegated responsibilities;
- supported modes and environments;
- explicit exclusions, structural exclusions, operational limits, and unobserved cases;
- extension seams and the boundary between implemented and merely extensible.

Connect each capability to a Goal ID and success criterion. The WHAT boundary is complete when a reader can tell what work the project removes from users, what work remains, and where another solution is required.

## 10. WHO — customer, collaborators, ownership, and operations

Answer WHO from a product-manager and operating-model perspective. Identify sponsor, adopter/decision maker, operator, direct user or calling system, downstream beneficiary, integrator, maintainer, security/network owner, and incident responder as relevant.

Use an operational participation matrix:

| Participant | Value proposition / reason to adopt | Operations they can execute | Data they can see | Module/data owner | Incident responsibility | Required collaboration |
|---|---|---|---|---|---|---|

Distinguish permission from responsibility: a user may see metrics without owning the module; a platform team may operate deployment while upstream maintainers fix code. State the escalation handoff for failures that cross product boundaries.

For promotion and adoption, state:

- target customer's recognizable pain and trigger;
- proof or trial needed to establish value;
- integration partners and internal teams required;
- adoption friction, trust concerns, and switching cost;
- non-fit customers whose baseline or constraints differ.

## 11. WHEN — temporal specification

Analyze time at four levels:

1. **business/adoption timing:** when the pain justifies adopting or replacing the project;
2. **lifecycle timing:** build, publish, deploy, start, request, steady state, failover, recovery, maintenance, retirement;
3. **interaction timing:** ordering, synchronization, retries, timeouts, deadlines, leases, TTLs, refresh, batching, backoff, retention;
4. **service timing:** latency percentiles, throughput windows, RTO/RPO, staleness, propagation delay, maintenance and release cadence.

Use a temporal contract table:

| Event/phase | Trigger | Preconditions | Ordering/deadline | State transition | Timeout/retry/fallback | Observable signal | Evidence |
|---|---|---|---|---|---|---|---|

Separate configured values, hard-coded limits, documented guarantees, measured behavior, and unknown targets. WHEN is complete when the runtime lifecycle and time-based quality obligations are both visible.

## Front-half consistency test

Before moving to the shared 2H, verify:

- project goals explain why each problem document exists;
- each Goal ID maps through a named baseline pain location to its Problem ID(s) and success criterion, with a rationale for each grouping or shared obligation;
- baseline and target views use the same per-problem visible terms and correct edge directions;
- routes intervene at an identified baseline responsibility or dependency;
- every Route ID has a corresponding target entry, rejection reason, or unknown gap;
- target entries show changed control/data paths, owners, and residual pain without silently adding unnamed responsibilities;
- every baseline and viable target element maps to a capability slot, and every slot has a source element;
- WHERE follows from slot occupancy;
- WHAT maps only the current project;
- WHO assigns every operational responsibility and failure handoff;
- WHEN covers lifecycle and quantitative time obligations;
- competitor classes follow route IDs within the same problem.
