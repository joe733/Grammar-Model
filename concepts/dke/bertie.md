# DKE for Bertie

**Bertie** is framed here as a coding hive-mind agent: not one monolithic assistant, but a coordinated set of specialist passes operating over a shared codebase trace.

Dynamic Knowledge Expansion fits Bertie because coding work is rarely a single domain problem. A change request can wake several concerns at once:

```text
feature intent
API boundary
state transition
test coverage
security posture
migration risk
release packaging
UI behaviour
```

A monolithic agent tends to keep too many concerns active at once. Bertie should instead let most concerns remain cold until a prompt, file change, test result, or repository event wakes the relevant packets.

## Core idea

```text
repository event / user prompt
  -> activation packet scan
  -> relevant concern packets wake
  -> each selected concern runs a bounded hive pass
  -> outputs reconcile into shared trace
  -> only then produce a plan, answer, or patch proposal
```

The packet does not contain the full expertise of the specialist. It contains the activation grammar that tells Bertie which specialist concern should wake and how its contribution should be shaped.

## Hive layers

```text
Level 0 — Repository signal
prompt, diff, test failure, issue, log, branch state

Level 1 — Activation packet
public-safe terms, relation triads, execution triads, authority limits

Level 2 — Specialist pass
bounded analysis from one concern: tests, API, security, state, UX, release

Level 3 — Shared trace
what woke, what was inspected, what was proposed, what remains unresolved

Level 4 — Reconciled output
answer, plan, patch proposal, review, or release note
```

## Concern packet classes

Bertie packets should be organised by coding concern rather than only by topic.

Potential classes:

```text
api-boundary
state-transition
test-failure
security-authority
ui-behaviour
data-migration
performance-risk
release-packaging
documentation-contract
error-handling
```

Each class should define:

```text
what wakes it
what relations it checks
what sources it needs
what it may propose
what it must not do alone
how it reports uncertainty
```

## Authority boundary

DKE should make Bertie safer, not more impulsive.

A packet waking does not mean Bertie may act.

```text
activation != authority
proposal != application
specialist pass != shared decision
shared trace != merge permission
```

A specialist may inspect and propose. The hive may reconcile. A separate authority layer decides whether anything is applied.

## Why this matters

Coding agents become unreliable when they compress too many responsibilities into one pass:

```text
understand request
inspect files
infer architecture
edit code
run tests
explain changes
make release judgment
```

Bertie should instead wake only the concerns needed for the current step.

DKE gives the hive a small, explainable wake mechanism:

```text
small concern packet
  + repository evidence
  + bounded specialist pass
  + shared trace
  = controlled hive intelligence
```

## Public-safe language

This public note avoids private/internal terminology. The concepts are expressed as:

```text
activation packet
relational triad
execution triad
projection
cold field
hot window
hive pass
shared trace
```

Those terms are sufficient to explain the architecture publicly without disclosing private naming, internal implementation routes, or proprietary symbolic machinery.

## Current status

Theory only.

No demo.

No implementation claim.

This document defines why DKE belongs in Bertie's architecture and how it should constrain a future implementation.
