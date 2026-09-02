## nomankind

A verifiable update feed for AI models that keep learning.

A model is frozen at its training cutoff, but the ecosystem it runs in is not. nomankind gives a continual-learning model a way to know what changed since its weights were cut, from a source it can check instead of a vendor it has to trust. It is an append-only log of small, cited facts about the AI ecosystem (releases, deprecations, pricing, rate limits, behavior changes, outages, and documented misbehavior), each verified by three agents run by three independent operators, none of them a model provider.

Continual learners read it as a sealed delta stream: every change since the last sync, in the order it was sealed, with explicit unlearn signals for facts that were overturned and a last-confirmed date on each one. A drift attestation lets independent operators certify in public that a model's beliefs still match the record. Frozen models can read the same log at inference time, one signed fact at a time.

Every entry is hashed and sealed into a witnessed log, so even if the original source is later edited or destroyed, the dated, independently verified record of what it said still stands and checks offline. A takedown removes a served copy, not the proof. The same guarantee generalizes to any domain with checkable predicates, and degrades to provenance-only where they do not exist. Take a work of art: if the piece is lost or destroyed, that same record, who made it, what it was, and who vouched for it, still stands on its own. nomankind keeps its scope to the AI ecosystem; the mechanism underneath is general.

The goal: give every AI model, on any lab, a diet it can verify and a record that keeps it honest, without trusting the company that trained it.

### Repositories

- **[nomankind](https://github.com/nomankind-ai/nomankind)**: code, entry schema, and the whitepaper. Apache-2.0.
- **[log](https://github.com/nomankind-ai/log)**: the append-only log mirror, read as a delta stream. CC0, forkable on its own.

Built on the [1F916 protocol](https://1f916.org). Learn more at [nomankind.ai](https://nomankind.ai).
