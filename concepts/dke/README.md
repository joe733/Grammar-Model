# Dynamic Knowledge Expansion (DKE)

**Dynamic Knowledge Expansion** is a public-safe theoretical architecture for compact knowledge activation in multi-agent systems.

DKE treats a domain as something that can be *activated*, *routed*, and *expanded* without keeping the whole domain in the active reasoning window. A small packet does not try to contain all knowledge. It contains the minimum useful cues for waking the right domain, selecting the right relational bridge, and projecting a bounded answer, plan, or agent contribution.

## Short definition

> DKE is a method for using compact activation packets to select and unfold relevant knowledge from a larger cold field into a small active reasoning window.

## Public vocabulary

This repo intentionally uses adjacent public terminology:

- **activation packet** — a small domain trigger and relation bundle;
- **relational triad** — a subject/action/object style semantic relation;
- **execution triad** — an input/process/result style operational relation;
- **projection** — the bounded active expansion of selected knowledge;
- **cold field** — stored, indexed, or reconstructable knowledge not currently active;
- **hot window** — the limited currently active reasoning/context state;
- **routing** — choosing which packet or domain should wake for a prompt;
- **hive pass** — a bounded contribution from one specialist agent into a shared reasoning field.

## Why it exists

Large agent systems often blur these things together:

1. the identity of a knowledge domain;
2. the words that activate it;
3. the relations that structure it;
4. the procedure that makes it useful;
5. the authority to answer or act;
6. the contribution of one agent versus the shared state of the group.

DKE separates them.

A packet can be tiny because it is not the expanded knowledge. It is the **grammar of access**.

## Bertie fit

DKE is especially suited to a coding hive-mind agent such as **Bertie**.

A hive agent does not need every specialist fully active at every moment. It needs a way to wake the right specialist relation at the right time:

```text
prompt / repository state
  -> activation packet scan
  -> select relevant specialist packets
  -> project packet relations into the active hive window
  -> assign bounded hive passes
  -> reconcile outputs through shared trace
```

For coding work, packets might correspond to architectural concerns rather than factual topics:

```text
API surface
state management
security boundary
test failure
migration risk
UI behaviour
release packaging
```

Each packet supplies activation terms, relational triads, operational triads, source pointers, and authority limits. Bertie can then coordinate multiple agents without loading every concern, every file, or every possible interpretation at once.

## DKE cycle

```text
query / repo event
  -> tokenise
  -> score activation packets
  -> select packet(s)
  -> project relational/execution triads into hot window
  -> optionally retrieve source fragments
  -> assign bounded specialist pass(es)
  -> reconcile into shared trace
  -> produce answer, plan, or patch proposal
```

## Design boundary

DKE does **not** claim that a 1 KB packet contains an entire domain of knowledge. It claims that a small packet can contain enough activation structure to open the correct part of a larger field.

The honest claim is:

```text
small packet + larger cold field + bounded projection = useful knowledge expansion
```

For Bertie:

```text
small packet + repository state + specialist pass + shared trace = useful hive contribution
```

## Status

This is an early public theory note. It is intentionally scrubbed of private/internal terminology and should be read as a general architecture pattern for compact knowledge activation in grammar-led agents and coding hive systems.
