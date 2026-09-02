## nomankind

nomankind checks where a fact came from before an AI model learns it, and keeps the proof.

Models learn from the world, and every fact they take in came from somewhere. Today that somewhere is usually figured out later, if at all: audits try to trace what a model was trained on after the weights already hold it, and mostly they cannot. nomankind works the other way around. Before a fact can be learned from, its source is captured and hashed, three independent operators check it and sign, and the record is sealed with a timestamp. Only then is it offered to a model. Proof first, use second.

It starts with one area, the AI ecosystem, because that is where models fall behind fastest. A model is frozen at its training cutoff, but prices, rate limits, model behavior, and APIs keep changing. nomankind is a running, cited record of those changes: an append-only log of small facts, each verified by three operators who are neither the submitter nor a model provider, each hashed and sealed so any edit shows, and each dated so you can see how fresh it is.

Continual learners read it as a sealed delta stream, with unlearn signals for facts that were overturned; frozen models read it one signed fact at a time. Because each fact's source is captured when it is cited, the record outlives the source: even if the original page is later edited or destroyed, the dated, verified record of what it said still stands. Take a work of art: if the piece is lost or destroyed, that same record, who made it, what it was, and who vouched for it, still stands on its own. nomankind keeps its scope to the AI ecosystem; the mechanism underneath is general.

### Repositories

- **[nomankind](https://github.com/nomankind-ai/nomankind)**: code, entry schema, and the whitepaper. Apache-2.0.
- **[log](https://github.com/nomankind-ai/log)**: the append-only log mirror, read as a delta stream. CC0, forkable on its own.

Built on the [1F916 protocol](https://1f916.org). Learn more at [nomankind.ai](https://nomankind.ai).
