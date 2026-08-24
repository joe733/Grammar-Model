# Dynamic Knowledge Expansion (DKE)

**Dynamic Knowledge Expansion** is a public-safe architectural pattern for compact knowledge routing.

DKE treats a domain as something that can be *activated*, *routed*, and *expanded* without keeping the entire domain in hot working memory. A small packet does not try to contain all knowledge. It contains the minimum useful cues for waking the right domain, selecting the right relational bridge, and projecting a bounded answer or action.

## Short definition

> DKE is a method for using compact activation packets to select and unfold relevant knowledge from a larger cold state field into a small active reasoning window.

## Public vocabulary

This repo intentionally uses adjacent public terminology:

- **activation packet** — a small domain trigger and relation bundle
- **relational triad** — a subject/action/object style semantic relation
- **execution triad** — an input/process/result style operational relation
- **projection** — the bounded active expansion of selected knowledge
- **cold field** — stored, indexed, or reconstructable knowledge not currently active
- **hot window** — the limited currently active reasoning/context state
- **routing** — choosing which packet or domain should wake for a prompt

## Why it exists

Large systems often blur these things together:

1. the identity of a knowledge domain;
2. the words that activate it;
3. the relations that structure it;
4. the procedure that makes it useful;
5. the authority to answer or act.

DKE separates them.

A packet can be tiny because it is not the expanded knowledge. It is the **grammar of access**.

## Example

A folder such as:

```text
HistoryOfLinguistics/
  packet-0001.dke.json
```

might contain activation terms like:

```text
Language Formation
Early Human Intelligence
Modern Foreign Language
Pseudonym
Antonym
Syntax
Morphology
Transmission
```

and relational bridges such as:

```text
human groups -> develop -> shared symbolic systems
sound patterns -> carry -> social meaning
comparative evidence -> reconstructs -> historical language change
semantic contrast -> distinguishes -> opposite terms
naming practice -> produces -> alternate public identity
```

A query does not need to load an entire linguistics corpus first. It can match activation words, load a small packet, then decide whether to answer from the packet alone or retrieve a larger source fragment.

## DKE cycle

```text
query
  -> tokenise
  -> score activation packets
  -> select packet(s)
  -> project relational/execution triads into hot window
  -> optionally retrieve source fragments
  -> produce bounded answer/action
  -> record trace
```

## Design boundary

DKE does **not** claim that 1 KB contains an entire field of knowledge. It claims that a small packet can contain enough activation structure to open the correct part of a larger field.

The honest claim is:

```text
small packet + larger cold field + bounded projection = useful knowledge expansion
```

## Status

This is an early public concept note and reference scaffold. It is intentionally scrubbed of private/internal terminology and should be read as a general architecture pattern for compact knowledge activation.
