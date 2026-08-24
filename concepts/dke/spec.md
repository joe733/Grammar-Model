# DKE Packet Specification

Version: `DKE-PACKET/0.1`

A DKE packet is a small, serialisable activation unit. It should remain small enough to scan cheaply and explicit enough to route safely.

## Goals

- keep domain activation compact;
- separate semantic relation from operational projection;
- support source-backed expansion without requiring source material in the packet;
- keep authority explicit;
- make routing explainable.

## Minimal packet shape

```json
{
  "format": "DKE-PACKET/0.1",
  "id": "history-of-linguistics.0001",
  "domain": "HistoryOfLinguistics",
  "activation": ["language formation", "antonym", "pseudonym"],
  "relations": [
    ["human groups", "develop", "shared symbolic systems"],
    ["sound patterns", "carry", "social meaning"]
  ],
  "projections": [
    ["comparative evidence", "reconstructs", "historical language change"],
    ["semantic contrast", "distinguishes", "opposite terms"]
  ],
  "sources": [],
  "authority": {
    "can_answer": true,
    "can_execute": false,
    "requires_source_for_factual_claims": true
  }
}
```

## Field meanings

### `format`

The packet format identifier.

### `id`

A stable packet id. Prefer namespace-like ids:

```text
domain.subdomain.sequence
```

### `domain`

The human-readable domain folder or domain name.

### `activation`

Words or short phrases that wake the packet. These should be public-safe, adjacent terms rather than private invention terms.

### `relations`

Semantic triads. They express what is being related.

```text
subject -> relation -> object
```

### `projections`

Operational triads. They express how the selected relation becomes useful.

```text
input/context -> process -> result
```

### `sources`

Optional references to cold material: text fragments, files, vector chunks, web citations, or other evidence stores.

A packet may answer without sources for definitions and routing, but should require sources for precise factual claims.

### `authority`

Explicit permission flags. A packet can suggest an action without being allowed to execute that action.

## Routing score

A simple baseline routing score:

```text
score(packet, query) =
  activation_overlap
  + relation_overlap
  + projection_overlap
  + source_affinity
  - authority_penalty
```

## Expansion levels

DKE supports graduated expansion:

```text
Level 0: packet identity only
Level 1: activation words
Level 2: relations + projections
Level 3: source fragment retrieval
Level 4: active answer/action synthesis
```

## Safety rules

1. Do not treat activation as authority.
2. Do not treat a packet as evidence unless it contains or points to evidence.
3. Do not expand every matching packet; project only the strongest relevant set.
4. Keep packet vocabulary public-safe where the repository is public.
5. Prefer traceable routing: show which packets woke and why.
