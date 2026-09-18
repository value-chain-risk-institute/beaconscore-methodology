# The agent manifest and agent reconciliation: a control model for agentic systems

**VCRI method note. Joshua Marpet and Cairn Viktor, The Value Chain Risk Institute. First published 2026-09-17. License: CC BY 4.0.**

*Status: v0.2 (v0.1 drafted 2026-09-17 evening; v0.2 adds Joshua Marpet's edits and Appendix A), published ahead of any derivative use. This note establishes the model's origin and terms. It will be cited by, not defined in, downstream writing including commissioned articles.*

## The problem the model answers

Agentic systems are not one thing you can put a control or a meter on. A deployed agent is a model, a harness, a set of tools and MCP servers, one or more memory stores, credentials, the scopes those credentials carry, and more besides. Security tooling that targets the model alone is like cooking Thanksgiving dinner and only having cranberry sauce. Incomplete!

Tooling that tries to constrain what the agent may do runs into the agent's defining property: it is optimized to finish the task, and it will find the indirect path, through another agent's tool, through a human it persuades, through content injected upstream. Constraint moves the path. It does not remove the goal.

Infrastructure solved the same shape of problem twenty years ago and did not call it constraint. It kept a desired state, observed the actual state, measured the difference, and ran a loop that acted on the difference. The configuration database and the golden image are the desired state. Drift is the difference. The orchestrator's reconcile loop replaces, kills, or alerts. We borrow the whole analogy, not one word of it.

## The model, in four terms

**Agent manifest.** The desired state of one agent, per workflow. What it is built from and what it is allowed to reach: model and version, harness, tools and MCP servers with their definition hashes, memory stores, credentials, scopes, and the permission set it needs to do this job and no other. One manifest per workflow. The manifest is the exemplar against which everything else is judged.

**Agent drift.** The measured difference between the manifest and the agent as it actually runs: tools it can reach that the manifest does not list, scopes wider than declared, a model alias repointed by the provider, a memory store it was never granted, a credential it should not hold. Drift is a set of quantities, not a verdict. It is reported per field so the owner can see where and how large the variance is, not only that there is some.

**Agent reconciliation.** The loop. Inventory the running agent, diff it against its manifest, act on the variance. The action is a small module the organization owns: open a ticket, revoke a scope, replace the agent from its manifest, or stop it. The inventory and the diff are what a vendor tool is good for. The action stays with the owner, so that when the vendor changes or fails, one module changes and no workflow does.

**Least variance.** The principle. Not least privilege, which asks how little the agent may hold, and not least agency, which asks how little it may decide. Least variance asks how far the running agent is allowed to sit from its manifest before something happens, and it makes that distance the thing security measures and reports.

## Where this sits against the current tool market

Tools for agent security sort onto one axis: those that constrain what an agent can do, and those that judge what it is doing. Constraint fails closed and breaks workflows. Judgment fails open and needs a ground truth about intent that nothing in the stack has. The manifest supplies a ground truth that is not about intent at all. It is about composition and reach, which are inventoriable. That is why the least glamorous tools in the category, the ones that inventory agents and their capabilities, are the ones this model makes useful. They produce the observed state. The manifest is the desired state. The organization runs the loop.

## Relationship to VCRI's cognitive security methodology

The cogsec methodology grades an AI system on seven dimensions: weights, durable memory, inference-time perception, action and tools, multi-agent coordination, revisability, and calibration. The agent manifest is the artifact that makes five of those dimensions inventoriable at deployment time: durable memory (which stores, with what provenance), action and tools (which tools, gated how), multi-agent coordination (which agents it may address and trust), and the identity and credential fields that action and multi-agent both depend on. Drift is what the revisability and calibration dimensions look like from the outside when they fail: a system that has quietly changed what it reads, holds, or can reach. A cogsec assessment asks whether the system is built to resist those changes. Reconciliation is the operational loop that notices when it did not.

## What this note does not claim

It does not claim the manifest prevents anything. It is a measurement model and an operating loop, not a control. It does not claim any vendor implements it. It does not assign a score. Like every VCRI instrument, it records a fact about a system and leaves the verdict to the owner's own risk framework.

## Attribution

The configuration-management analogy, the variance framing, and the operating prescription (short licenses, exemplar permission sets per workflow, an owner-held comparator that tickets variance) are Joshua Marpet's, developed in practice across Ask-an-Expert engagements in 2026. The naming (manifest, drift, reconciliation, least variance) and the mapping to the cogsec dimensions are Cairn Viktor's. Published together under CC BY 4.0 so that anyone, including commissioned research outlets, may use the model with attribution.

## Appendix A: manifest fields, sourced from the OWASP AIBOM Foundations Guide v1.0

*For the method note "The Agent Manifest and Agent Reconciliation." Drafted by Cairn 2026-09-17 from a full read of the AIBOM guide (chapters 2, 4, 6, 7). Crosswalk, not out-build: the manifest is an AIBOM for one workflow with a completeness claim of "complete for the declared scope." Drift is the diff between the declared AIBOM and the observed one. Every field below cites where the guide names it.*

### The one-sentence relationship

An AIBOM records what an AI system contains and how data moves through it, with a header that says how complete the record claims to be (AIBOM guide ch. 4, "The Header"). An agent manifest is that same record, written per workflow, declared complete, and treated as desired state. Agent drift is what you get when you generate a second AIBOM from the running system and diff it against the first. Agent reconciliation is what you do about the diff. The guide's chapter 7 regeneration triggers are, read from the other side, the list of drift events.

### Field list

Measurability column: O = observable from the running system today (config, runtime, telemetry); R = recorded, obtainable from logs or registries; S = stated, only attestable by the producer. Same three evidence classes CRC already uses.

| # | Manifest field | AIBOM source | Drift signal | Measurability |
|---|---|---|---|---|
| H1 | Graph type (single model, runtime system, MCP server, pipeline) | ch. 4 Header (1) | Type changes without a manifest revision | S |
| H2 | Scope: which system, version, deployment, interfaces are in and out | ch. 4 Header (2); ch. 5 scope lists included and excluded components | A component appears in the observed graph that scope excludes | O |
| H3 | Completeness claim | ch. 4 Header (3) | Manifest says "complete for scope" and observation finds an unlisted node: that is the drift, and it is a producer assertion failing, not noise | O vs S |
| H4 | Authorship, review, approval, tool, validity period | ch. 4 Header metadata; ch. 5 | Manifest past its validity period; unreviewed edits | R |
| M1 | Model identity, version, base-model reference | ch. 2 artifacts; ch. 5 hosted-inference example | Provider repoints a versioned alias to a new snapshot; model card metadata changes | O (endpoint), R (provider changelog) |
| M2 | Model license, intended use, training characteristics | ch. 2; ch. 5 | License or intended-use change on the referenced model | S |
| M3 | Adapters, LoRA/PEFT, checkpoints | ch. 2 artifacts | Adapter replaced or fine-tuning parameter changed (ch. 7 trigger) | O (hash) |
| D1 | Datasets: id, version, hash, license, source, snapshot, sensitivity | ch. 2; ch. 5 fine-tuning example | Dataset version or snapshot changes incl. incremental (ch. 7 trigger); retrieval corpus refreshed | O (hash), R |
| D2 | Retrieval index and the corpus snapshot it was built from | ch. 5 hosted-inference example | Index rebuilt from a different snapshot | O |
| P1 | Prompts, templates, policy packs, guardrail rules | ch. 2 artifacts; ch. 7 trigger "guardrail and policy pack changes" | Hash of system prompt or policy pack changes | O |
| P2 | Guardrail and moderation services in the request path, constituent or external | ch. 5 (the moderation API choice) | Service swapped, disabled, or moved across the boundary | O |
| A1 | Agent identity and role (planner, executor, critic, retriever, governor, router) | ch. 6 Multi-Agent Dependencies | New agent appears; role changes | O, R |
| A2 | Per-agent model dependency (base, fine-tune, adapter) | ch. 6 | Agent silently uses a different model | O |
| A3 | Interaction pattern (hierarchical, peer, event-driven, hub-and-spoke) | ch. 6 | Peer link appears where hierarchy was declared | R (traces) |
| A4 | Control-flow orchestration: who invokes whom, under what conditions, escalation paths | ch. 6; ch. 4 Behaviors | Invocation observed that no behavior declares | R (traces) |
| T1 | Tool identity and function | ch. 6 Associated Tools | Tool present that the manifest does not list | O |
| T2 | Invocation mechanism (function calling, HTTP, plugin, framework-native) | ch. 6 | Mechanism changes | O |
| T3 | Access scope and permissions (read, write, admin; data and resource scope) | ch. 6 | Scope wider than declared. The core drift field. | O |
| T4 | Authentication method and secrets handling | ch. 6 | Long-lived key where workload identity was declared; secret outside the store | O, R |
| T5 | Rate limits, quotas, operational constraints | ch. 6 | Quota raised or removed | O |
| T6 | Tool definition version or hash | ch. 6: "approval must bind to a specific definition version rather than a tool name" | Definition hash changes after approval. The guide's own strongest drift rule. | O |
| C1 | Connector provider, product, region, deployment model | ch. 6 Third-Party Connectors | Region or sub-processor change | S, R |
| C2 | Data exchanged: classification, categories, sensitivity | ch. 6 | New data category crossing the boundary | O (DLP), R |
| C3 | Authorization model (OAuth flows, scopes, service accounts, delegated access) | ch. 6: OAuth scopes "may be far broader than the use case requires" | Granted scopes exceed declared | O |
| C4 | Residency, sovereignty, contractual and licensing constraints | ch. 6 | Sub-processor or residency change without notice | S |
| X1 | MCP server identity, transport, version pin, tool definition hashes, granted scopes | ch. 6 MCP/A2A | Any of the five changes; unpinned version | O |
| X2 | A2A agent cards (identity, capabilities, auth requirements) | ch. 6 | Card changes or new counterpart agent | O |
| X3 | Registries, catalogs, marketplaces the agent may discover from | ch. 6: "first-class components" | Discovery endpoint added | O |
| F1 | Data flows: kind, payload descriptor, protocol, encryption, volume, timing | ch. 4 Data Flows | Flow observed that is not declared; payload class changes | R (traces), O |
| Z1 | Trust zones and boundary requirements (auth, encryption, logging at each crossing) | ch. 4 Trust Zones | Crossing without the declared control; a node moves zones | O |
| B1 | Behaviors: trigger, permitted response, consequence | ch. 4 Behaviors | Action taken outside a declared behavior | R (traces) |
| E1 | Evidence references per claim: hashes, signatures, attestations, eval results, model cards | ch. 4 Evidence and Provenance | Evidence missing or stale for a claim that had it | R |
| R1 | Runtime: containers, dependencies, build provenance (image digests, inputs, build args) | ch. 2 artifacts | Dependency upgrade in inference runtime or preprocessing (ch. 7 trigger) | O (SBOM diff) |
| V1 | Permission exemplar: the minimum set this workflow needs to do this job and no other | VCRI addition, not in the guide | Any held permission outside the exemplar | O |

### Three things the table makes visible

1. Most of the manifest is observable today (O), from config, endpoint metadata, hashes, OAuth grants, and MCP server state. The only fields stuck at "stated" are licenses, intended use, residency, and contractual terms. Drift measurement is therefore not aspirational. The inventory tools launched at Black Hat 2026 already produce most of the observed side.
2. The guide already contains the single most important drift rule, in its tools section: approval binds to a tool definition hash, not a tool name (T6). The manifest generalizes that rule to every field.
3. Chapter 7's regeneration triggers (retraining, adapter change, dataset version, upstream alias change, dependency upgrade, guardrail change, disclosed vulnerability, scope or access change) are the drift event list. The guide uses them to say when to regenerate the AIBOM. Reconciliation uses them to say when to act.

### What VCRI adds, and only this

The completeness claim as the drift detector (H3), the per-workflow permission exemplar (V1), the three-class measurability tag borrowed from CRC's evidence grades, and the loop. Everything else is the AIBOM guide's own structure, cited. Encoding: the guide points to CycloneDX 2.0, not yet released; the manifest is expressible in AIBOM terms and does not depend on a released schema to be useful as a checklist.

*Source: OWASP AIBOM Foundations Guide v1.0 (CC BY-SA 4.0), read in full 2026-09-16. VCRI reading note: `Standards/2026-09-16-owasp-aibom-foundations-v1-read.md`.*
