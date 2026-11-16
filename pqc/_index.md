---
date: "2026-05-13T7:00:00Z"
title: PQC Readiness Extension
weight: 1
---

# PQC Readiness Extension

The Post-Quantum Cryptography (PQC) Readiness Extension adds quantum-safe transition criteria to the PKI Maturity Model. It introduces an extension-specific maturity signal alongside the baseline PKI MM categories, plus weight overlays that emphasize requirements most relevant to PQC migration.

The quantum threat fundamentally changes what PKI maturity means. An organization achieving Level 5 on every current PKI MM requirement may still face material cryptographic risk if its foundations are quantum-vulnerable. The Dutch government's "harvest-now, decrypt-later" framing makes this a **present-day** risk for long-lived confidentiality, not a future concern.

## Status

This extension is **under development**. It is authored and maintained by Kennedy Nwup (Afield AB), Vice Chair of the PKIMM Working Group.

- **Complete** — Governance module (strategy and vision, policies and documentation, compliance, processes and procedures, and cryptography): full Level 1–5 criteria, assessor guidance, evidence examples, overlay weights, and 25 status-labelled regulatory and standards references listed per category for display in the assessment application. Includes persona coverage for software vendors and certificate-consuming organizations (v0.4.0) and reworked segregation-of-duties criteria (v0.3.0).
- **Draft for review** — Management module (key management, certificate management, infrastructure management, change management and agility) and Operations module (resilience, automation, interoperability, monitoring and auditing): full Level 1–5 criteria, assessor guidance, and proposed requirement overlays, converted from the Module 2 and Module 3 source documents now in working group review. The content of these two modules is not yet endorsed.
- **In development** — Resources module: source content in drafting; PQC-critical considerations identified at outline level below.
- **YAML version** — `0.8.0` (draft). The extension version will move to `1.0.0` when all modules reach full Level 1–5 development and the working group endorses the content.

### Open review items

The following points are open and will be settled across the whole extension once the Resources module is added. Comments are welcome. Until then, scores produced with this draft are provisional: they should not be treated as final or compared with later versions, and the Resources categories contribute their baseline levels only, because they have no PQC criteria yet.

- **Relevance weights.** Governance uses a relevance weight of 5 in every category and Management uses 5, 5, 4 and 5. Operations sets each relevance weight to the category's requirement weight sum after overlays, rounded to a whole number as the schema requires (30, 5, 10 and 31), so that the PQC criteria carry about half of the extension category level in every category. The two approaches give the PQC criteria a different influence. Which rule applies is a working group decision, to be made once and applied consistently.
- **Overlay multipliers.** The multipliers for Management and Operations are provisional and will be reviewed as a set with the Governance overlays.
- **Evidence shared across overlays.** Where one piece of evidence can support several overlaid requirements, the extension should not weight the same underlying capability more than once. The Operations source document sets a rule on evidence reuse and claim separation; the same check is open for the Management overlays.

### Overlay design

Earlier drafts treated two overlay designs as competing candidates: Governance-centric overlays, per-requirement multipliers on the Governance categories, and capability-centric overlays on operational capabilities such as crypto-agility and PQC training (section 7 of the v1.3 proposal). Development since then has reconciled them by module rather than choosing between them. The Governance overlays are published in the current YAML. Overlays for the Management module, including change management and agility, and for the Operations module are included in the current YAML as drafts for review, and training-related overlays will follow with the Resources module. The working group reviews each module's overlays as part of that module's release.

The v2.0.0 model's Cryptography category is covered as of extension version 0.6.0, with a relevance entry and overlays on all six requirements.

## Scope

The extension targets the following audiences:

- **Certification Authority operators (CA / TSP)** — primary audience; most existing content reflects CA/TSP archetypes.
- **PKI architects and operators in enterprises** — assessing internal PKI quantum-readiness.
- **Auditors and consultants** — using the extension as part of broader PKI maturity engagements.

Persona coverage for **certificate-consuming organizations** and **software vendors** is now included in the Governance criteria (v0.4.0). Coverage for **AI-system-layer cryptographic governance** remains a known gap tracked for a later revision.

## What the extension covers

The YAML covers the Governance module in full: strategy and vision, policies and documentation, compliance, processes and procedures, and cryptography each receive PQC-specific Level 1–5 criteria. The Management and Operations modules are included as drafts for review. Resources is identified at outline level.

### Governance — Module G

#### Strategy and vision (G.strategy-and-vision)

Strategic direction for PQC transition: executive sponsorship of the quantum threat, the Mosca inequality applied to data lifetimes, organizational persona per the Dutch Migration Handbook, board-level visibility, and budget for PQC activities.

**Key transitions:**
- Level 2 → 3 — "Awareness to Action": formal strategy incorporation, executive sponsorship extended, working group established.
- Level 4 → 5 — "Execution to Leadership": competitive positioning, ecosystem contribution, crypto-agility as ongoing capability.

#### Policies and documentation (G.policies-and-documentation)

Policy framework for PQC: CP/CPS updates to incorporate NIST FIPS 203/204/205, deprecation schedules aligned with SP 800-131A Rev 3, hybrid-vs-pure PQC strategy, key management policy adjustments (larger keys, HSM support, stateful HBS state management), CBOM adoption, and multi-jurisdiction policy alignment (BSI / ANSSI hybrid versus CNSA 2.0 pure PQ).

#### Compliance (G.compliance)

Regulatory mapping and audit scope for PQC requirements: DORA ICT risk management (EU financial services from January 2025), eIDAS 2.0 cryptographic requirements, CNSA 2.0 timelines (US National Security Systems), NIS2 implementing measures, and the 18 EU Member States Joint Statement recommendations. Audit criteria evolution under WebTrust and ETSI scopes is tracked here.

#### Processes and procedures (G.processes-and-procedures)

Operational procedures transformed for PQC: key ceremony evolution (hybrid generation, quorum, HSM activation, stateful HBS state management), crypto-agility procedures per NIST CSWP 39, quantum risk assessment with Mosca inequality, change management for phased migration, incident response for cryptographic events, and extended segregation of duties for PQC-specific roles.

### Management — Module M (draft for review)

Management assesses whether the organization can execute the transition, with evidence that the mechanisms work under realistic conditions.

#### Key management (M.key-management)

Inventory of managed keys with algorithm, parameter set, and migration state; post-quantum key generation under ceremony control; handling of seed and expanded key formats; key-encapsulation key roles per NIST SP 800-227; hardware-module capability confirmed by test; and, where in scope, state control for stateful hash-based signing.

#### Certificate management (M.certificate-management)

Post-quantum and hybrid certificate profiles; validity policy that accounts for algorithm deprecation; relying-party validation across a representative population; enrollment-path readiness; revocation behavior under post-quantum signature sizes; trust-anchor and intermediate transition; and, where in scope, sustained verifiability of long-lived signatures.

#### Infrastructure management (M.infrastructure-management)

Post-quantum support across the components in the cryptographic path; measured capacity and performance effects; telemetry that distinguishes post-quantum operation from silent classical fallback; hardware-module firmware and validation readiness; and evidence for cloud and managed services.

#### Change management and agility (M.change-management-and-agility)

A rehearsed cryptographic change with rollback; dependency sequencing across systems; an emergency procedure for algorithm or implementation withdrawal; tracked migration exceptions; and a tested exit path from hybrid deployment.

### Operations — Module O (draft for review)

Operations assesses whether the cryptographic state that is running remains secure, observable, interoperable, and recoverable as systems change, fail, and recover.

#### Resilience (O.resilience)

Continuity and recovery when a cryptographic dependency can no longer be used; recovery that restores both the service and the approved cryptographic state; and control of backups and recovery artifacts so that restoration does not reintroduce prohibited cryptography.

#### Automation (O.automation)

Certificate lifecycle automation for post-quantum and transitional profiles, with validated outcomes, guardrails, and exception paths; deliberate manual operation of high-assurance processes is not treated as a deficiency.

#### Interoperability (O.interoperability)

Documented transition states for material integrations; a representative interoperability population; revalidation after material change; and temporary compatibility paths with owners and exit conditions.

#### Monitoring and auditing (O.monitoring-and-auditing)

Observation of the cryptographic mechanisms in use for material services; detection of unexpected classical fallback, regression, and drift; and audit evidence sufficient to reconstruct the cryptographic state relevant to an incident.

### Module R (outline only)

The following PQC-critical considerations are identified for the remaining module. Full Level 1–5 development is pending.

#### Resources — Module R (PQC people and sourcing considerations)

- **Sourcing (R.sourcing)** — vendor PQC roadmap assessment in procurement; contract requirements for PQC support timelines; third-party certificate provider PQC readiness; supply-chain security for cryptographic components.
- **Knowledge and Training (R.knowledge-and-training)** — PQC technical training for PKI operations staff; executive education on quantum risk; certification programs incorporating PQC; knowledge transfer from PQC migration projects.
- **Awareness (R.awareness)** — organization-wide quantum-threat awareness; developer education on PQC implications; stakeholder communication for migration activities.

## Product and service dependency

Organizational PKI maturity depends on the readiness of products and services in the dependency chain — Certificate Authority software, HSMs, IAM platforms, cloud PKI offerings, application frameworks, IoT firmware. An organization can achieve Level 5 on internal governance while being blocked from PQC deployment by a critical vendor not supporting quantum-safe algorithms until later in the decade.

The PKI Consortium's separate Post-Quantum Cryptography Maturity Model (PQCMM) assesses product / service PQC readiness. The PQC extension is designed to be used **alongside** PQCMM: the PKIMM extension scores the organization's governance and operational readiness; PQCMM scores the dependencies. Integration guidance is on the working group's roadmap.

## YAML definition

The machine-readable definition of the PQC Readiness Extension is in [`pqc-extension.yaml`](./pqc-extension.yaml). Tools consume the YAML directly; this page is the human-readable companion. The YAML is the canonical source for assessment use — the prose above is a summary. See also the generated [machine-readable definition](./definition/) page.

## References

- **NIST FIPS 203 / 204 / 205** — ML-KEM, ML-DSA, SLH-DSA (August 2024)
- **NIST SP 800-131A Rev. 3** — Transitioning the Use of Cryptographic Algorithms and Key Lengths
- **NIST CSWP 39** — Considerations for Achieving Cryptographic Agility
- **NIST SP 800-208** — Stateful Hash-Based Signatures
- **NIST SP 800-227** — Recommendations for Key-Encapsulation Mechanisms
- **NIST IR 8547** — Transition to Post-Quantum Cryptography Standards (October 2026)
- **CNSA 2.0** — NSA Commercial National Security Algorithm Suite 2.0 (2022)
- **Regulation (EU) 2022/2554 (DORA)** — Digital Operational Resilience Act
- **Regulation (EU) 2024/1183 (eIDAS 2.0)**
- **NIS2 Implementing Regulation 2024/2690**
- **18 EU Member States Joint Statement on Post-Quantum Cryptography**
- **Dutch PQC Migration Handbook**
- **CycloneDX Cryptography Bill of Materials (CBOM)**

## Attribution

This extension is based on the *Proposal for Post-Quantum Cryptography Readiness Extension to the PKI Maturity Model (PKIMM)* (Draft v1.3, December 2025) prepared for the PKI Consortium by Kennedy Nwup, Principal Consultant — Post-Quantum Cryptography & PKI Readiness, Afield AB.
