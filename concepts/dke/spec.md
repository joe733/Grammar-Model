# DKE Packet Theory

Version: `DKE-PACKET/0.1-theory`

A DKE packet is a small, serialisable activation unit. It should remain small enough to scan cheaply and explicit enough to route safely.

This document is a **theory specification**, not a demo implementation.

## Goals

- keep domain or concern activation compact;
- separate semantic relation from operational projection;
- support source-backed expansion without requiring source material in the packet;
- keep authority explicit;
- make routing explainable;
- allow multi-agent systems to wake only the specialist concern currently needed.

## Minimal packet shape

A packet can be described abstractly as:

```text
packet
  format
  id
  domain_or_concern
  activation_terms
  relational_triads
  execution_triads
  source_pointers
  authority_limits
  trace_policy
```

The exact serialisation is intentionally left open at this stage.

## Field meanings

### `format`

The packet format identifier.

### `id`

A stable packet id. Prefer namespace-like ids:

```text
domain.concern.sequence
```

### `domain_or_concern`

The human-readable folder, topic, codebase concern, architectural layer, or specialist agent area.

For a coding hive-mind, examples of concern classes might include:

```text
state management
API boundary
security posture
test failure
migration plan
release packaging
UI behaviour
performance risk
```

### `activation_terms`

Words or short phrases that wake the packet. These should be public-safe, adjacent terms rather than private invention terms.

### `relational_triads`

Semantic triads. They express what is being related.

```text
subject -> relation -> object
```

For Bertie-style coding work:

```text
module -> exposes -> public interface
state transition -> affects -> downstream behaviour
test failure -> indicates -> unresolved contract
```

### `execution_triads`

Operational triads. They express how the selected relation becomes useful.

```text
input/context -> process -> result
```

For Bertie-style coding work:

```text
failing test -> isolate cause -> bounded patch proposal
API change -> compare callers -> compatibility note
security concern -> inspect authority path -> risk statement
```

### `source_pointers`

Optional references to cold material: files, tests, logs, vector chunks, issue comments, previous decisions, or external evidence stores.

A packet may support routing and planning without sources, but should require source material for precise factual or codebase-specific claims.

### `authority_limits`

Explicit permission flags. A packet can suggest an action without being allowed to execute that action.

For a coding hive-mind, authority should distinguish:

```text
may observe
may propose
may edit
may test
may merge
may release
```

### `trace_policy`

The packet should describe how its contribution will be made inspectable:

```text
why this packet woke
which source pointers were used
which agent pass contributed
what changed in the shared trace
what remains unresolved
```

## Routing score

A simple baseline routing score:

```text
score(packet, query_or_repo_event) =
  activation_overlap
  + relation_overlap
  + execution_overlap
  + source_affinity
  + recent_trace_affinity
  - authority_penalty
```

## Expansion levels

DKE supports graduated expansion:

```text
Level 0: packet identity only
Level 1: activation terms
Level 2: relations + projections
Level 3: source fragment retrieval
Level 4: specialist hive pass
Level 5: reconciled shared trace
```

## Safety rules

1. Do not treat activation as authority.
2. Do not treat a packet as evidence unless it contains or points to evidence.
3. Do not expand every matching packet; project only the strongest relevant set.
4. Keep packet vocabulary public-safe where the repository is public.
5. Prefer traceable routing: show which packets woke and why.
6. In coding contexts, separate patch proposal from patch application.
7. In hive contexts, separate individual specialist output from reconciled shared state.

## Bertie interpretation

For Bertie, DKE is not a toy packet format. It is a way of organising a coding hive mind so that many specialist concerns can exist cold while only a few become active during a given pass.

The packet is the wake condition and relational scaffold.

The hive pass is the bounded specialist contribution.

The shared trace is the reconciled memory of what the hive actually decided.
