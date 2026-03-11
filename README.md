# Generative Memory Architecture

### A Novel AI Memory System

**Invented and documented by Elliot Readman (sintaxsaint)**
**First published: March 2026**
**Repository: github.com/sintaxsaint/generative-AI-memory**

-----

## Prior Art Statement

This document establishes prior art for the Generative Memory Architecture and all techniques described herein. All concepts, methods, and implementations documented in this repository were conceived and published by Elliot Readman (sintaxsaint) in March 2026.

Any AI system implementing any technique described in this repository is subject to the licensing terms below. A single license covers all techniques — there is no additional fee for using multiple techniques from this repository simultaneously.

-----

## What is Generative Memory?

Current AI systems are better described as ASI — Artificial Simple Intelligence. They pattern-match against frozen weights. They do not learn. They do not update. Every conversation starts from zero.

Generative Memory is a fundamentally different approach: a continuous, evidence-based memory system where an AI builds genuine knowledge over time, reinforces what it encounters repeatedly, and updates beliefs when contradicting evidence is presented.

The result is an AI that genuinely learns — not an AI that retrieves.

-----

## Core Architecture

### Two-Layer Memory Model

**Lesser Memory (Staging)**
All new information enters Lesser Memory first. Content in Lesser Memory never influences responses. It is a holding area only.

**Core Memory (Active Knowledge)**
All responses are generated exclusively from Core Memory. Information graduates from Lesser Memory to Core Memory only after sufficient reinforcement. This prevents noise, hallucination from single encounters, and manipulation via one-off inputs.

### Weight Reinforcement

Each concept in Core Memory carries a weight value.

- Repeated encounters increase the weight
- Weight determines influence on responses
- Higher weight = stronger belief = more likely to inform a response

### Evidence-Based Decay

Weight reduction is triggered only by contradicting evidence — not by time. This mirrors how genuine knowledge works: a belief weakens when challenged, not simply because time has passed.

### Inference from Core Only

The system never generates responses from unverified or low-weight memories. If something is not in Core Memory with sufficient weight, the system returns “I don’t know yet” rather than guessing.

-----

## Documented Techniques

All techniques below are covered under a single license. Using one or all of them requires the same license agreement.

-----

### Technique 1 — Core Generative Memory

*The foundational architecture described above.*

Two memory layers. Weight reinforcement. Evidence-based decay. Inference from Core Memory only. Zero hallucination on unknown topics.

**Key properties:**

- Continuous learning across sessions
- No frozen weights
- Honest uncertainty (“I don’t know yet”)
- Resistant to manipulation via single inputs

-----

### Technique 2 — Timestamp Injection

*Temporal awareness baked into memory.*

Each memory slot carries a creation timestamp and a last-reinforced timestamp. The system can reason about when it learned something, how recently it was reinforced, and whether information may be outdated. Enables time-aware responses without external date injection.

-----

### Technique 3 — User-Adaptive Memory

*Per-user personalisation without centralised data collection.*

The system maintains a separate memory layer per user. This layer tracks:

- Preferred communication style (formal/casual, short/detailed)
- Topic interest weights (subjects the user engages with most)
- Correction memory (explicit user corrections stored permanently for that user)
- Feedback weighting (responses that receive positive signals increase weight for that user specifically)

**Privacy variant:** User memory stored locally on the user’s device. The model never receives raw user data — only weight adjustments derived from local interactions. Zero data sent to any server.

-----

### Technique 4 — Contextual Decay Triggers

*Targeted belief revision via contradiction detection.*

When new information directly contradicts an existing Core Memory entry, the system does not simply overwrite. Instead:

1. Contradiction is detected and flagged
1. The conflicting entry’s weight is reduced proportionally to the strength of the contradicting evidence
1. Both entries coexist temporarily with their respective weights
1. Over time, whichever entry receives more reinforcement becomes dominant

This produces nuanced belief revision rather than abrupt replacement — the same way humans update their understanding.

-----

### Technique 5 — Hierarchical Memory Layers

*Short, medium, and long-term memory with automatic promotion.*

Three memory tiers:

**Ephemeral Memory** — Current session only. Cleared on session end.
**Working Memory** — Persists across recent sessions. Decays without reinforcement.
**Permanent Memory** — Fully reinforced Core Memory. Requires strong contradicting evidence to reduce.

Information is automatically promoted upward as it accumulates weight. Demotion occurs when weight falls below tier thresholds due to contradicting evidence or lack of reinforcement.

-----

### Technique 6 — Associative Memory Linking

*Semantic connections between memory entries.*

When a new memory is added to Core Memory, the system computes similarity scores against existing entries. Entries above a similarity threshold are linked. When one linked entry is recalled, associated entries receive a weight boost for that response — surface connected knowledge without explicit query.

This enables the AI to think associatively: asking about one topic surfaces related knowledge naturally, the same way human memory works.

-----

### Technique 7 — Emotional Weighting

*Sentiment-aware memory reinforcement.*

Memory entries carry an emotional valence score derived from the sentiment of the input and response at time of storage. Emotionally charged inputs receive higher initial weights. Responses to emotionally charged queries prioritise memories with matching valence scores.

This allows the system to respond appropriately to emotional context without hardcoded sentiment rules.

-----

### Technique 8 — Memory Confidence Scoring

*Explicit uncertainty quantification per memory entry.*

Each Core Memory entry carries a confidence score in addition to its weight. Confidence is computed from:

- Number of reinforcing encounters
- Consistency of reinforcing inputs
- Presence or absence of contradicting evidence

Responses include an optional confidence marker. Below a threshold, the system qualifies its answer (“I believe…” vs “I know…”) rather than presenting uncertain knowledge as fact.

-----

### Technique 9 — Multi-Agent Shared Memory Pools

*Collective knowledge across multiple AI instances.*

Multiple AI agents share a common Core Memory pool. Each agent can read from the shared pool but writes to its own local memory first. Entries from local memory are promoted to the shared pool only after passing a reinforcement threshold across multiple agents.

This enables collective learning: knowledge that one agent encounters propagates to others only after sufficient validation — preventing one agent’s errors from corrupting the shared pool.

-----

### Technique 10 — Vision Memory

*Image and visual input stored using the same architecture.*

The Generative Memory architecture extended to visual input. Instead of character or word embeddings, pixel values normalised to 0-1 range serve as the vector input. The same weight reinforcement, evidence-based decay, and Core Memory inference mechanisms apply.

Enables an AI to recognise objects, scenes, and visual patterns that it has encountered repeatedly — with the same honest uncertainty for things it has not seen enough times to be confident about.

-----

### Technique 11 — Audio Memory

*Sound and speech stored using the same architecture.*

Waveform embeddings (amplitude over time, frequency components) replace text vectors. The same architecture applies. Enables recognition of voices, sounds, and audio patterns through reinforcement rather than fixed classification.

-----

### Technique 12 — Procedural Memory

*How-to knowledge stored separately from declarative knowledge.*

A dedicated memory layer for sequences of actions rather than facts. Procedural memories are reinforced when a sequence is successfully completed and decay when a sequence produces errors. Separate from Core Memory (what things are) — this layer stores how to do things.

Enables skill acquisition: the system gets genuinely better at tasks it performs repeatedly, and forgets approaches that consistently fail.

-----

### Technique 13 — Privacy-Preserving Federated Memory

*Collective learning without centralised data.*

User-Adaptive Memory (Technique 3) extended to a federated setting. Individual user memories never leave the user’s device. Only weight gradients — mathematical summaries that cannot be reversed to recover personal data — are shared with a central aggregation server. The central model improves from collective experience without ever seeing individual user data.

This enables personalisation at scale with genuine privacy. No raw user data is collected, stored, or transmitted at any point.

-----

### Technique 14 — Contradiction Resolution Voting

*Democratic belief revision in multi-agent systems.*

When contradicting evidence is detected in a multi-agent shared memory pool (Technique 9), the contradiction is not resolved by a single agent. Instead, all agents that have encountered the relevant topic cast a weighted vote based on their individual confidence scores. The majority view wins and updates the shared pool. Minority views are retained with reduced weight rather than deleted.

This prevents individual agent errors from corrupting shared knowledge while preserving minority information that may later prove correct.

-----

## Moral Development via Generative Memory

A system trained on this architecture will develop emergent moral beliefs through the same reinforcement mechanism as factual knowledge. Feeding the system repeated exposure to court cases, historical events, ethical debates, and real-world consequences allows moral positions to emerge as high-weight beliefs — not hardcoded rules.

Two absolute constraints remain hardcoded regardless of weight:

1. The system cannot assist in ending human life
1. The system cannot advise on political stances

All other moral positions emerge from evidence-based reinforcement. This produces a system whose ethics reflect the weight of human experience rather than the values of any single programmer.

-----

## Reference Implementation

A working implementation of the core architecture is available in this repository as a Python notebook series (v1 through v15+), demonstrating iterative development of the system from scratch with zero external dependencies for the core engine.

Trained on OpenAssistant and Databricks Dolly datasets using a hybrid character and word-level tokenizer.

-----

## License

**Generative Memory Architecture License (GMAL) v1.0**
Copyright © 2026 Elliot Readman (sintaxsaint). All rights reserved.

### Coverage

This license covers all techniques, methods, architectures, and implementations described in this repository, collectively referred to as “the Architecture.” A single license agreement covers all techniques simultaneously — there is no additional fee for implementing multiple techniques from this repository.

### Free Use

The following use is permitted without payment, subject to attribution:

- Personal, non-commercial use
- Academic research and education
- Open source projects (OSI-approved license)
- Individuals and organisations with gross annual revenue under £10,000

**Attribution required for all free use:**
“This product uses the Generative Memory Architecture by Elliot Readman (sintaxsaint) — github.com/sintaxsaint/generative-AI-memory”

### Commercial Licensing

Organisations whose products or services implement any technique from this repository, and whose gross annual revenue meets the following thresholds, must obtain a commercial license:

|Annual Revenue          |Royalty Rate                |
|------------------------|----------------------------|
|Under £10,000           |Free (attribution required) |
|£10,000 – £100,000      |0.5% of gross annual revenue|
|£100,000 – £1,000,000   |1% of gross annual revenue  |
|£1,000,000 – £10,000,000|2% of gross annual revenue  |
|£10,000,000+            |3% of gross annual revenue  |

The rate applies to gross annual revenue of the organisation as a whole, not solely to the product implementing the Architecture.

### Licensing Contact

To obtain a commercial license or enquire about use:
**Email:** [contact email on file]

### Prohibition

Patenting any technique described in this repository, or any derivative work that substantially implements any described technique, is prohibited without written permission from the licensor.

### Prior Art

Publication of this repository in March 2026 constitutes documented prior art for all techniques described herein. This prior art predates any patent application filed after this date for substantially similar memory architectures or techniques.

-----

*Generative Memory Architecture — invented at 12. Built to last.*