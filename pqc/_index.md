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
- **In development** — Management module: source content complete and under review; YAML conversion in progress. Operations and Resources modules: PQC-critical considerations identified at outline level.
- **YAML version** — `0.6.0`. The extension version will move to `1.0.0` when all modules reach full Level 1–5 development and the working group endorses the content.

### Overlay design

Earlier drafts treated two overlay designs as competing candidates: Governance-centric overlays, per-requirement multipliers on the Governance categories, and capability-centric overlays on operational capabilities such as crypto-agility and PQC training (section 7 of the v1.3 proposal). Development since then has reconciled them by module rather than choosing between them. The Governance overlays are published in the current YAML. Overlays for the Management module, including change management and agility, are drafted in the Module 2 source content now under review, and training-related overlays will follow with the Resources module. The working group reviews each module's overlays as part of that module's release.

The v2.0.0 model's Cryptography category is covered as of extension version 0.6.0, with a relevance entry and overlays on all six requirements.

## Scope

The extension targets the following audiences:

- **Certification Authority operators (CA / TSP)** — primary audience; most existing content reflects CA/TSP archetypes.
- **PKI architects and operators in enterprises** — assessing internal PKI quantum-readiness.
- **Auditors and consultants** — using the extension as part of broader PKI maturity engagements.

Persona coverage for **certificate-consuming organizations** and **software vendors** is now included in the Governance criteria (v0.4.0). Coverage for **AI-system-layer cryptographic governance** remains a known gap tracked for a later revision.

## What the extension covers

The published YAML covers the Governance module in full: strategy and vision, policies and documentation, compliance, and processes and procedures each receive PQC-specific Level 1–5 criteria. The Management module is developed in source form and under review; Operations and Resources are identified at outline level.

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

### Modules M, O, R — outline only

The following PQC-critical considerations are identified for the remaining modules. Full Level 1–5 development is pending.

#### Management — Module M (PQC technical considerations)

- **Key Management (M.key-management)** — algorithm inventory and CBOM generation; PQC key lifecycle (larger keys, longer generation times); stateful hash-based signature state management (XMSS, LMS); hybrid key management; HSM PQC algorithm support verification.
- **Certificate Management (M.certificate-management)** — hybrid certificate issuance (composite signatures, external keys); certificate validity periods versus algorithm security lifetimes; revocation strategy for quantum-vulnerable certificates; template updates; cross-certification for hybrid PKI.
- **Infrastructure Management (M.infrastructure-management)** — HSM firmware upgrade roadmaps; network capacity for larger PQC keys and signatures; storage for larger certificates; performance testing.
- **Change Management and Agility (M.change-management-and-agility)** — crypto-agility architecture enabling algorithm substitution; transition procedures; rollback for failed PQC deployments; configuration management for cryptographic parameters.

#### Operations — Module O (PQC security considerations)

- **Resilience (O.resilience)** — quantum threat in business continuity planning; recovery procedures for cryptographic compromise; redundancy for PQC algorithm availability.
- **Automation (O.automation)** — automated cryptographic inventory discovery; automated certificate replacement for PQC migration; CI/CD integration for PQC algorithm validation.
- **Interoperability (O.interoperability)** — PQC interoperability testing with relying parties; hybrid certificate compatibility verification; cross-vendor PQC algorithm interoperability; protocol-version negotiation.
- **Monitoring and Auditing (O.monitoring-and-auditing)** — algorithm usage monitoring and reporting; quantum-vulnerable algorithm detection; CBOM drift monitoring; audit trail for algorithm transitions.

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
- **CNSA 2.0** — NSA Commercial National Security Algorithm Suite 2.0 (2022)
- **Regulation (EU) 2022/2554 (DORA)** — Digital Operational Resilience Act
- **Regulation (EU) 2024/1183 (eIDAS 2.0)**
- **NIS2 Implementing Regulation 2024/2690**
- **18 EU Member States Joint Statement on Post-Quantum Cryptography**
- **Dutch PQC Migration Handbook**
- **CycloneDX Cryptography Bill of Materials (CBOM)**

## Attribution

This extension is based on the *Proposal for Post-Quantum Cryptography Readiness Extension to the PKI Maturity Model (PKIMM)* (Draft v1.3, December 2025) prepared for the PKI Consortium by Kennedy Nwup, Principal Consultant — Post-Quantum Cryptography & PKI Readiness, Afield AB.
