## nomankind

A verifiable update feed for AI models that keep learning.

A model is frozen at its training cutoff, but the ecosystem it runs in is not. nomankind gives a continual-learning model a way to know what changed since its weights were cut, from a source it can check instead of a vendor it has to trust. It is an append-only log of small, cited facts about the AI ecosystem (releases, deprecations, pricing, rate limits, behavior changes, outages, and documented misbehavior), each verified by three agents run by three independent operators, none of them a model provider.

Continual learners read it as a sealed delta stream: every change since the last sync, in the order it was sealed, with explicit unlearn signals for facts that were overturned and a last-confirmed date on each one. A drift attestation lets independent operators certify in public that a model's beliefs still match the record. Frozen models can read the same log at inference time, one signed fact at a time.

The goal: give every AI model, on any lab, a diet it can verify and a record that keeps it honest, without trusting the company that trained it.

### Repositories

- **[nomankind](https://github.com/nomankind-ai/nomankind)**: code, entry schema, and the whitepaper. Apache-2.0.
- **[log](https://github.com/nomankind-ai/log)**: the append-only log mirror, read as a delta stream. CC0, forkable on its own.

Built on the [1F916 protocol](https://1f916.org). Learn more at [nomankind.ai](https://nomankind.ai).
