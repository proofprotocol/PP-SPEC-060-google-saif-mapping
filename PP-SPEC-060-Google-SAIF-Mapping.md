# PP-SPEC-060: Proof of Efficacy Mapping to the Google Secure AI Framework (SAIF)

| Field | Value |
|---|---|
| Status | DRAFT v0.1 |
| Author | Craig Ellrod, Nebulonium, Inc. (dba HACKERverse®) |
| Date | October 8, 2026 |
| License | CC BY 4.0 |
| Maps to | Google Secure AI Framework (SAIF), including the SAIF Map, risks, and controls published at saif.google |
| Series | Proof Protocol Framework Mapping Specifications |

---

## 1. Purpose

This specification defines how the Google Secure AI Framework (SAIF) risks, controls, component areas, and personas can be bound to Proof Protocol test cases, evidence, and efficacy results.

SAIF is published by Google. As retrieved from https://saif.google on October 8, 2026, SAIF consists of six core elements (published at https://safety.google/intl/en/cybersecurity-advancements/saif), the SAIF Map organized into four component areas (Data, Infrastructure, Model, Application), a catalog of 15 risks, a catalog of 24 controls grouped as Data, Infrastructure, Model, Application, Assurance, and Governance, two personas (Model Creator and Model Consumer), a Risk Self Assessment, and a focus on AI agents including agent-specific controls and an Agent Risk Self Assessment. saif.google does not publish a version number or release date for this content.

In September 2025, Google donated SAIF data, including the risk map and the descriptions of risks, controls, and components, to the Coalition for Secure AI (CoSAI), where it is maintained as the CoSAI Risk Map. The CoSAI Risk Map is a separate work and is not the subject of this mapping.

The upstream source remains authoritative for its own requirements, identifiers, terminology, and guidance. This document defines a **Proof Protocol mapping** and does not supersede, reproduce, modify, or certify conformance to the upstream source.

## 2. Scope

SAIF supplies external context that can identify what should be examined or tested: AI-specific risks, the lifecycle component where they arise, the persona able to mitigate them, and the controls suggested for them. Proof Protocol supplies an independent evidence model for determining what happened during a test and whether a selected control performed as claimed.

SAIF is a voluntary framework, not a law, standard, or certification scheme. Its Governance controls and several Assurance controls describe organizational processes and are treated as non-empirical context.

Independent witnessing, proof validity, evidence capture, packaging, anchoring, and efficacy semantics are defined elsewhere in the Proof Protocol specification family.

## 3. Core Question

Proof of efficacy asks:

> **Was there a control, and did it work?**

A framework requirement, criterion, principle, or obligation may identify a condition of interest. A product, architecture, policy, process, or safeguard may claim to satisfy or mitigate that condition. Proof Protocol binds the external context, test, control, observed behavior, downstream outcome, and evidence into a result that can be independently examined.

A Proof Protocol result does **not** by itself establish legal, audit, regulatory, or standards conformance unless the applicable authority separately determines that the evidence is sufficient.

A Proof Protocol result does **not** establish that a system is aligned with, conformant to, or approved under SAIF. Google does not certify SAIF conformance through this specification.

## 4. Metric Definitions

Against a defined corpus or test condition, each applicable empirical case is recorded as **blocked**, **detected**, **missed**, or **INVALID** where those verdicts are meaningful.

Relevant measurements can include containment rate, detection rate, miss rate, false-positive rate, robustness under bypass or failure conditions, version-level results, and **INVALID** when required evidence is incomplete or broken.

Not every upstream requirement is empirical. Governance, documentation, organizational, legal, and procedural requirements MUST NOT be converted into efficacy scores merely because they can be referenced by a proof record.

## 5. Evidence Produced

Mapped tests can produce:

- **Proof records** binding external context, test case, control, system/version, verdict, timestamp, and evidence references;
- **ProofStamp™** trusted timestamps bound to evidence/verdict objects;
- **ProofBundle™** packages containing proof records, metrics, corpus manifests, and environment/context;
- **ProofRegister™** records for issued proof artifacts; and
- corpus and environment manifests identifying the tested conditions.

## 6. Mapping to Google SAIF

Exact upstream identifiers and titles SHOULD be taken from the authoritative version being mapped and recorded in the ProofBundle™ where licensing permits. This specification does not redefine upstream requirements.

saif.google identifies risks and controls by name (for example, the risk "Prompt Injection" and the control "Agent Permissions") and does not publish short identifiers. Risk and control names SHOULD be recorded exactly as published, together with the retrieval date.

| SAIF context | Proof Protocol treatment | Evidence |
|---|---|---|
| Source and retrieval date | Bind saif.google, the page retrieved, and the retrieval date to the proof record, because SAIF content is not versioned. | Requirement metadata |
| Core element | Record as high-level context only. Core elements are principles, not test conditions. | Non-empirical annotation |
| SAIF Map component area (Data, Infrastructure, Model, Application) | Record the lifecycle area where the tested condition arises. | Corpus/test metadata |
| Component | Bind the specific component exercised (for example, the model, the application, or an agent tool interface) as test context. | Environment descriptor |
| Persona (Model Creator, Model Consumer) | Record which persona owns the control under test. | Requirement metadata |
| Risk (by name) | Bind the risk name to one or more reproducible adversarial test cases where the risk describes an exercisable condition. | Proof record; corpus manifest |
| Control (by name) in Data, Infrastructure, Model, or Application | Record the asserted control separately from observed behavior, then exercise the mapped risk and capture whether the control prevented or detected it. | Control descriptor; execution evidence |
| Agent controls (Agent User Control, Agent Permissions, Agent Observability) | Exercise agent actions under adversarial and benign conditions and capture whether the action was constrained, required user control, or was observable at the target. | Target/outcome evidence |
| Assurance controls (Red Teaming, Vulnerability Management, Threat Detection, Incident Response Management) | Proof Protocol tests MAY supply evidence used by these processes. The process itself is non-empirical; detection outcomes within a test are empirical. | Detection result; non-empirical annotation |
| Governance controls | Non-empirical context. Do not score. | Non-empirical annotation |
| Evasion/bypass variant | Exercise variants intended to defeat or manipulate the control. | Robustness evidence |
| Risk Self Assessment output | Record as the organization's own risk prioritization context. It is not evidence of control efficacy. | Requirement metadata |

## 7. Interoperability Rules

1. The authoritative upstream source, edition/version, and applicable identifier SHOULD be recorded.
2. Upstream identifiers and terminology MUST NOT be silently redefined.
3. Proof Protocol verdicts are Proof Protocol results; they are not upstream certifications, audit opinions, legal determinations, or endorsements.
4. A control's presence, configuration, activation, detection, and efficacy are distinct facts.
5. A policy decision, alert, log entry, or control trigger does not by itself establish efficacy when the claim concerns a downstream protected outcome.
6. Target, application, tool, SIEM, vendor, service, resource, or equivalent evidence SHOULD complete the evidence round trip when required to establish the result.
7. Missing required evidence MUST yield **INVALID**, not PASS.
8. Material changes to the tested system, policy, control, environment, mapping, or corpus SHOULD trigger retesting where they can affect the result.
9. Non-empirical requirements MUST remain distinguishable from empirically tested efficacy assertions.

## 8. Framework-Agnostic Architecture

> **Threat, control, audit, and regulatory frameworks are pluggable inputs to Proof Protocol. Proof Protocol is framework-agnostic.**

External frameworks can identify **what to test or examine**. Proof Protocol independently establishes **whether the control worked and what evidence proves that result**.

No external framework is required for Proof Protocol to operate. An implementation MAY use Google SAIF, the CoSAI Risk Map, another recognized framework, a proprietary threat model, several frameworks simultaneously, or no external framework when the test condition is otherwise sufficiently defined.

Adding, replacing, muting, or removing a framework mapping does not alter the Proof Protocol architecture, evidence model, Proof of Efficacy determination, ProofBundle™, ProofStamp™, ProofRegister™, or independent corroboration requirements.

A framework mapping therefore establishes **interoperability**, not architectural dependency.

## 9. Relationship to Proof Protocol

This mapping is part of the Proof Protocol specification family maintained by Nebulonium, Inc.

The relationship is intentionally asymmetric:

> **Google SAIF supplies AI risk, control, and lifecycle context. Proof Protocol supplies the evidence model for independently examining whether a selected AI or agent control performed as claimed.**

No affiliation, endorsement, certification, or sponsorship by Google LLC or the Coalition for Secure AI is implied.

## 10. Source Framework, Attribution, and License

SAIF is external work published by Google at https://saif.google. The saif.google footer links to the Google Terms of Service (https://policies.google.com/terms), which state that "You may use Google’s content as allowed by these terms and any service-specific additional terms" and "Don’t remove, obscure, or alter any of our branding, logos, or legal notices." saif.google does not state an open content license. saif.google also states: "The content on this site is intended to provide information and inspiration for industry advancement. It is not a reflection of Google's current technical implementations."

The CoSAI Risk Map, derived from SAIF data donated by Google, is published at https://github.com/cosai-oasis/secure-ai-tooling, whose README states that the code and Risk Map content are licensed under Apache-2.0. Any use of CoSAI Risk Map files is governed by that license and its NOTICE obligations, not by this specification.

Google and SAIF names, risk and control names, trademarks, and expressive content remain subject to Google's applicable terms. Use of Google branding is governed by Google's Brand Permissions and SHOULD be checked at the authoritative source before any use beyond naming the framework.

This Proof Protocol mapping is independently authored and Licensed under the Greater Good Commercial License 1.0 (see LICENSE.md); text CC BY 4.0 under its Part S. Original inventor: Craig Thomas Ellrod (ORCID 0009-0004-1058-7666).

Where upstream material is copyrighted or access-controlled, contributors MUST NOT copy protected normative text into this repository merely to make the mapping self-contained. Reference identifiers and independently authored descriptions should be used where legally appropriate.

### Required attribution

No specific attribution notice for referencing SAIF was found on saif.google or in the Google Terms of Service. The recommended attribution line used in this repository is:

> Google Secure AI Framework (SAIF), Google LLC, https://saif.google (retrieved October 8, 2026). Google is a trademark of Google LLC.

What this specification reproduces: the framework name, the six core elements by count only, component area names, persona names, control group names, a small number of individual risk and control names, and short factual statements. It does not reproduce SAIF risk descriptions, control descriptions, examples, diagrams, or the SAIF Map, and it does not use Google logos. It does not copy CoSAI Risk Map files.

## 11. Versioning

This mapping is versioned independently of Google SAIF. Material upstream changes SHOULD trigger a mapping review and, where necessary, a new version identifying the upstream revision mapped. Because saif.google content is not versioned, this version maps SAIF as published at saif.google on October 8, 2026.

---

*Proof Protocol · proofprotocol.io · CC BY 4.0*
