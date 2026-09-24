# How much and How Analysis

The main report's second half evaluates the project across all problem spaces. Analyze **How much before How** so implementation views answer known quality requirements instead of becoming an unbounded component tour.

## 1. How much — quantified non-functional realization

Build an NFR ledger from project goals, capability-slot obligations, configuration, tests, deployment assets, benchmarks, incidents, and production evidence.

| NFR ID | Problem/slot | Quality attribute | Target and workload | Implemented mechanism | Measured result | Environment/version | Status/gap |
|---|---|---|---|---|---|---|---|
| N1 | P1 / CS2 | latency / scale / ... |  |  |  |  | stated / observed / reproduced / unknown |

Consider only relevant attributes:

- performance: latency percentiles, throughput, startup time, completion time;
- scalability: users, nodes, tenants, objects, fan-out, partitions, request rate;
- resource limits: CPU, memory, disk, network, file/object size, connection and queue bounds;
- availability and reliability: SLO, retries, failover, recovery time, error budget;
- consistency and durability: source of truth, replication, retention, staleness, RPO;
- security and isolation: trust model, authentication, authorization, encryption, tenancy, audit;
- compatibility: protocols, platforms, versions, migration and upgrade guarantees;
- operability: observability coverage, configuration, rollout, backup, maintenance and incident burden;
- quality evidence: tests, static checks, release process, security audit, production cases.

For every number capture units, workload, percentile/window, environment, version, source, and whether it is a target or result. Keep these evidence classes distinct:

- **configured bound:** a default or allowed value, not demonstrated capacity;
- **documented target/guarantee:** maintainer commitment, not a reproduced result;
- **vendor benchmark or case study:** valid only for its published environment;
- **repository observation:** implementation mechanism or test, not production performance;
- **reproduced measurement:** result produced during this analysis;
- **unknown:** quantity or target not established.

Code size and file counts describe implementation footprint; they do not substitute for product NFRs.

### How much exit test

How much is complete when every acceptance measure and slot-level quality obligation has a number, categorical requirement, or explicit measurement gap; every cited result includes context; and no configured default is presented as achieved capacity.

## 2. How — from architecture choices to implementation

Explain how the selected route becomes a working system. Begin with the project's responsibility split and dependencies, then follow representative uses into the decisions, state, and code that produce outcomes. Choose sections and views to fit the project; the questions below are an explanation contract, not a fixed report outline.

When several problem spaces reuse implementation, open How with a compact table of shared mechanisms, reused modules, scenario-specific adapters or policies, and the point where the paths diverge. Omit this table for a single problem or when reuse is not material. Keep route and competitor comparison in the problem documents; this table explains implementation reuse.

### What architectural choices realize the route?

Show the system boundary, principal runtime or module responsibilities, dependencies, interfaces, and the reasons for the chosen split. Identify where control, data, and state cross boundaries; include deployment, trust, and failure domains when they explain a goal or quality result. Map the choices to the occupied capability slots and the selected Route IDs. Establish canonical domain terms and invariants when they are needed to read the implementation; use code and repository documentation to resolve contradictions.

### How does a representative use produce the result?

Select paths that exercise a material goal, a distinctive route decision, or a significant quality risk. Cover every material problem with a trace or an explicit reference to a genuinely shared trace. Follow each path from caller and entry contract to observable outcome, naming:

- the concrete interfaces or functions crossed, in execution order;
- inputs, outputs, and state reads or writes with their owners;
- decisions and alternate branches that change the result;
- success, retry, fallback, failure, and observable signals;
- the affected Goal, Route, Slot, and NFR IDs.

Use a sequence, state, data-flow, or decision view when it reduces the work needed to follow the path. Put edge meanings and direction cues in the figure; refer to visible node names rather than diagram source IDs in prose. Cite the repository location of the implementation, not only a component name.

### Which mechanisms decide the result?

Deepen the modules that own the route's core behavior, a critical state or invariant, a decisive branch, or a material NFR. For each selected mechanism explain its interface contract; input and output; relevant data structures or state; decision rule or algorithm; failure and recovery behavior; and the code and tests that establish the account. Explain why its design changes the outcome and which cost or limit remains. A list of modules and responsibilities does not satisfy this depth requirement.

Use interface and module vocabulary where it clarifies a design choice: a seam is a place behavior can vary without changing its caller; an adapter implements that seam; module depth is complexity hidden behind the interface. Analyze a seam only when it affects a goal, extension boundary, testability, or quality obligation.

### What quality effect is established?

Connect each decisive mechanism to a capability slot and a How much requirement or gap:

> mechanism → slot → expected quality effect → evidence or measurement gap → residual cost

For distributed or persistent state that matters to this chain, identify its owner and source of truth, writers and readers, consistency and retention, and behavior under restart or failure. Distinguish configured limits from measured behavior. Compare a direct competitor's implementation only when it clarifies a route-level tradeoff on the same axes.

### Choose views by the question

- A structural or C4 view can explain system boundaries and dependency handoffs.
- A use-case or sequence view can explain ordering and collaboration.
- A state machine can explain transitions, retries, and recovery.
- A domain model can explain terms, ownership, and invariants.
- A decision table, algorithm sketch, or code view can explain a core rule.

4+1 may be used as a completeness lens across logical, runtime, development, deployment, and scenario concerns. Neither C4 nor 4+1 requires a corresponding section or a fixed number of diagrams. Use the smallest set of representations that makes the actual architecture and core implementation understandable; keep each view at a consistent abstraction level.

## 3. Traceability matrices

Produce two cross-checks:

| Goal / acceptance measure | Problem | Capability slots | NFR IDs | Implementing modules | Evidence/gap |
|---|---|---|---|---|---|

| NFR ID | Architecture mechanism | Verification artifact | Result | Residual risk |
|---|---|---|---|---|

Use these as cross-checks; present them when they help readers follow the explanation. They prevent architecture descriptions from floating free of project purpose and NFR claims from floating free of implementation.

## Exit test

The 2H analysis is complete when:

- each material acceptance measure and capability-slot obligation appears in the NFR ledger;
- targets, limits, and results have context and evidence class;
- the reader can follow the chosen route from architecture boundaries through a representative use to the concrete code that decides its outcome;
- each material problem has a trace or a justified shared trace, and each core mechanism explains its contract, state, decision rule, failure behavior, and evidence;
- relevant state, control, data, failure, trust, deployment, and extension responsibilities are explicit;
- implementation mechanisms explain NFR results or gaps;
- each included view answers a specific question and maps back to project goals and capability slots.
