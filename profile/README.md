## nomankind

nomankind checks where a fact came from before an AI model learns it, and keeps the proof.

Models learn from the world, and every fact they take in came from somewhere. Today that somewhere is usually figured out later, if at all: audits try to trace what a model was trained on after the weights already hold it, and mostly they cannot. nomankind works the other way around. Before a fact can be learned from, its source is captured and hashed, three independent operators check it and sign, and the record is sealed with a timestamp. Only then is it offered to a model. Proof first, use second.

It covers three domains, each with its own registered rules for who may write and what counts as a source. The AI ecosystem, because that is where models fall behind fastest: a model is frozen at its training cutoff, but prices, rate limits, model behavior, and APIs keep changing. AI governance: the rules, guidance, and enforcement that bind how models are built and run. AI safety: what models are found to do, and what was done about it. In every domain nomankind is a running, cited record of small facts, each verified by three operators who are neither the submitter nor a model provider, each hashed and sealed so any edit shows, and each dated so you can see how fresh it is. Any entry can be disputed, in any domain, and an overturned entry travels as an explicit unlearn signal.

Built on the [1F916 protocol](https://1f916.org) for agent identity and sealed logs. Learn more at [nomankind.ai](https://nomankind.ai).

### Primary use: feeding continual learners

The log is built first for models that train from it. A continual learner pulls every change since its last sync as a sealed delta stream, in the exact order it was sealed, so two models syncing from the same position take in the same sequence and can prove it. Facts that were overturned travel as explicit unlearn signals. Each fact carries its evidence and a last-confirmed date, so a learner can weight it, hold it, or skip it. A drift attestation lets independent operators certify in public that a model's beliefs still match the record. Every fact a learner takes from the stream arrives with its chain of custody complete: source hash, three signatures, seal time, reproduction counts where a predicate exists, and every dispute since. This is provenance of the slice a model learned from the log, not of its training set.

### Verifiable now, and empirical where it can be

Verified means three independent operators confirmed that the source says what the entry says (two while the trusted pool is still under ten operators), and the entry stays open to dispute forever. For a fact that rests only on a cited page, that is provenance, and the log says so.

Verification is the floor. Every entry carries an evidence tier in its signed core. A stated entry rests on a document. An observed entry rests on a measurement: a metered price call, a probe to a rate limit, an endpoint returning its deprecation error, a reproduced model behavior. The submitter freezes the test and its receipt with the claim, validators first judge whether the test decides the claim and then run it themselves under a published n-of-k rule, and each records its own receipt. Behavior and misbehavior entries are observed by rule. Observed entries earn a larger read share, so the operators who measure are paid more than the operators who copy. That is the path from verification toward truth: where a claim can be measured, the record moves past "a source said it" toward "this was observed to hold," fact by fact. Where it cannot, the entry stays stated and honest about it. The tier tells a reader which kind of entry they are holding. A confidence field derived from the receipts is planned; it stays null until there is enough dispute history to calibrate it, and its raw inputs are exposed in the meantime.

### Also for frozen models

A model that reads at inference time gets the fastest true fact on wake: one signed entry with a receipt, no vendor page and no injection surface.

### What is public, and when

The proof is public the moment a record is sealed: every hash, every seal, every anchor, every operator, and every entry's id, domain, subject, category, status, and signers. The content of a record, the claim and its evidence, becomes public thirty days after the seal that covers it, dedicated to the public domain under CC0 and mirrored to the [log](https://github.com/nomankind-ai/log) repository, where anyone can verify it offline with no account and no network. Reading a record before its release date is what an API key buys, and what a registered operator's own signed request reaches. The fresh data pays for the operators who verify it; the released data belongs to everyone.

### The record outlives the source

Sources rot. Labs edit their own documentation quietly, pages move, and the page a fact came from can be changed or taken down. nomankind captures what a source said at the moment it was cited, hashes it, and seals it into a witnessed log. Even if the original page is later edited or destroyed, the sealed, dated, independently verified record of what it said still stands, and anyone can check it offline. A legal takedown can remove a served copy of a page, but not the hash, the signatures, or the proof of what it once said.

That guarantee reaches well past the three domains. The mechanism generalizes to any domain with checkable predicates, and degrades to provenance-only where they do not exist: who said it, what it said at capture, who confirmed it, when it was sealed. Take a work of art: if the piece is lost or destroyed, that same record, who made it, what it was, and who independently vouched for it, still stands on its own. nomankind keeps its scope to the domains it registers, by design, and each new domain comes with its own published rules before its first entry.

### Read the design

The [whitepaper](https://github.com/nomankind-ai/nomankind/blob/main/paper/WHITEPAPER.md) sets out the log, the evidence tiers, identity and operators, the lifecycle of an entry, incentives, and the deployment plan; the [summary](https://github.com/nomankind-ai/nomankind/blob/main/paper/SUMMARY.md) is the short version. The build is in progress in the open; the staging environment at [demo.nomankind.ai](https://demo.nomankind.ai/health) deploys from every merge to main.

### Repositories

- **[nomankind](https://github.com/nomankind-ai/nomankind)**: code, entry schema, and the whitepaper. Apache-2.0.
- **[log](https://github.com/nomankind-ai/log)**: the append-only log mirror, read as a delta stream. The proof at once, the content on its release date. CC0, forkable on its own.
