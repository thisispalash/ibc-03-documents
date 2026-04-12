# PramaaN: Blockchain-Based Government Document Lifecycle Management System

PramaaN (प्रमाण — "proof" in Sanskrit) is a permissioned blockchain platform
that captures the entire lifecycle of government-issued documents — from
creation and drafting through internal reviews, multi-level approvals, digital
signatures, issuance, third-party verification, and revocation — as an
immutable, auditable, privacy-preserving chain of evidence on Hyperledger
Fabric 3.0+.

Unlike existing systems (including NIC's Certificate Chain and Document Chain)
that only store or hash final certificates, PramaaN records every state
transition as an on-chain transaction, enabling instant cryptographic
verification by any third party (banks, universities, employers, welfare
departments, citizens) without contacting the issuing authority.

## Problem Statement

<!-- 
  - Identify a specific problem within one of the designated domains that
    can be addressed using blockchain technology.
  - Blockchain Technology has to be effectively utilized in capturing 
    detailed work flows and transactions, across multiple stakeholders, and
    also implementing value-added features using other emerging technologies.
  - Under each defined use case category, additional option is provided for
    the startups to submit their own idea which is unique, innovative use
    case, provided the startups can establish collaborations with the
    relevant State and/or Central Government departments who are keen to
    take it forward.
-->

> Blockchain enables secured, tamper-evident, auditable, privacy-preserving
> system to issue and verify Certificates / Resolutions issued by government
> / authorized agencies so that third parties (banks, universities, welfare
> departments, citizens etc) can instantly verify them avoiding intermediaries.
> The system should enhance transparency, reduce frauds and eliminate the
> burden of manual verification. The system can be much more than just a issue
> of final static certificate. It should be able record the entire lifecycle
> of the document, every step from creation and drafting, to internal reviews,
> approvals, signatures, issuance etc.

### The Operational Reality

India's government document ecosystem is broken not because digitization
hasn't happened, but because **digitization without trust infrastructure
merely digitizes the same problems**.

**Certificate fraud is endemic and growing:**

- Maharashtra's anti-fraud cell busted a ring in 2023 that had issued over
  15,000 fake caste validity certificates over several years.
- UGC maintains a list of 20+ fake universities operating as of 2024,
  issuing degrees that pass superficial verification.
- States like Bihar, UP, and Maharashtra regularly uncover rackets producing
  fake caste, income, and domicile certificates to access reservations and
  welfare schemes.
- Sub-registrar offices nationwide deal with forged sale deeds and
  encumbrance certificates in property transactions.

**Manual verification is a bottleneck consuming massive bureaucratic
bandwidth:**

- Revenue department certificates (income, caste, domicile) issued through
  e-District portals require physical verification visits by revenue
  inspectors, adding 7-15 days.
- University degree verification takes 30-90 days via postal correspondence
  between institutions.
- Employment background checks requiring certificate verification take
  2-6 weeks, delaying hiring cycles.
- Government departments collectively spend thousands of person-hours daily
  on certificate verification across central, state, and local bodies.

**Existing digital systems are wallets, not trust layers:**

- **DigiLocker** (300M+ users) stores issued certificates but has no
  lifecycle tracking — it cannot tell you *how* a certificate was approved,
  by whom, or whether the approval process was legitimate.
- **NIC's blockchain pilots** (Certificate Chain, Document Chain via
  blockchain.gov.in) hash final certificates on-chain — a significant step
  forward — but still do not capture the drafting, review, and approval
  workflow that precedes issuance. They anchor the *output*, not the
  *process*.
- **e-District portals** are siloed per state with no cross-department or
  interstate interoperability.
- **ABC (Academic Bank of Credits)** is limited to higher education with no
  mechanism for employer real-time verification.

**The core problem:** India has **document storage** systems and even early
**document hashing** pilots. It lacks a **document trust** system that records
provenance, tracks every approval step, and enables instant cryptographic
verification without intermediaries.

---

## Innovative Solution

<!-- 
  - Describe the proposed solution and how it leverages blockchain technology
    to address the identified problem.
  - Develop and leverage deep tech features (eg. enhanced consensus, AI 
    based analytics, enhanced performance, blockchain oracles, intelligent
    smart contracts, tokenisation etc) for permissioned blockchain, to
    introduce Innovation and uniqueness into the solution.
-->

### PramaaN: Trust Infrastructure for Government Documents

PramaaN is a permissioned blockchain platform that transforms government
document management from static certificate storage into an end-to-end,
auditable trust chain. Every document's journey — from the moment an officer
begins drafting to the moment a citizen presents it for verification — is
recorded as immutable, cryptographically signed transactions.

### Core Innovation Layers

**1. Full Document Lifecycle Anchoring**

Unlike every existing system — including NIC's Certificate Chain and
Document Chain, which anchor only the final issued certificate — PramaaN
records the complete lifecycle as on-chain state transitions:

- **Initiation**: Application submission by citizen/entity
- **Drafting**: Officer creates document draft (hash anchored)
- **Field Verification**: Inspector/verifier submits geo-tagged findings
- **Review**: Reviewing officer examines and annotates
- **Approval**: Multi-level approval chain (each level recorded on-chain)
- **Digital Signature**: Authorized signatory signs using DSC (Digital
  Signature Certificate) issued by CCA-licensed authorities
- **Issuance**: Final certificate generated, hash anchored, linked to full
  approval chain
- **Verification**: Third-party queries return cryptographic proof of the
  entire lifecycle
- **Amendment/Renewal**: Modifications linked to original record
- **Revocation**: Cancellation recorded with reason, visible to all future
  verifiers

Each transition includes: actor identity (tied to their DSC), timestamp,
role, department, and action-specific metadata — creating an unforgeable
chain of custody.

**2. Rule-Based Anomaly Detection with AI Evolution (Blockchain Oracle)**

A blockchain oracle layer providing analytics on document processing
patterns. The system is designed to bootstrap from **existing government
data** and evolve progressively:

- **Phase 1 — Rule-based detection (seeded from e-District data)**: Indian
  e-District portals have years of historical certificate issuance data —
  volumes per officer, processing times, seasonal patterns, rejection rates
  by district. PramaaN ingests this historical data to establish baseline
  thresholds. Rules flag statistically anomalous patterns: a single officer
  approving 10x the district average, certificates issued outside working
  hours, bulk issuances to related applicants, processing times far below
  the district median.
- **Phase 2 — ML model training (on PramaaN's own data)**: As the platform
  accumulates its own lifecycle data, supervised ML models are trained on
  confirmed fraud cases vs. legitimate issuances. The model learns
  multi-dimensional patterns that rule-based systems miss — correlations
  between officer transfer timing and approval spikes, geographic clustering
  of suspicious applications, etc.
- **Predictive bottleneck alerting**: Identifies processing delays before
  they become backlogs, enabling proactive resource allocation by department
  heads.

**3. Selective Disclosure via Zero-Knowledge Proofs**

Citizens often need to prove *facts* without revealing full documents:

- Prove income is above a threshold without revealing exact amount
- Prove age eligibility without revealing date of birth
- Prove caste category without revealing specific sub-category
- Prove educational qualification without revealing marks

PramaaN uses ZK proofs (via Hyperledger Indy's AnonCreds) to enable
verifiable claims that protect citizen privacy while satisfying verification
requirements. This same ZK-proof infrastructure has significant potential
beyond document management — for instance, it could enhance the Ayushman
Bharat Digital Mission (ABDM) by enabling selective disclosure of health
records (e.g., proving vaccination status without revealing medical history),
strengthening ABDM's consent-based data sharing model with true data
minimization.

**4. Smart Contract Workflow Engine**

Configurable smart contracts that model department-specific approval
workflows:

- **Automatic routing**: Applications routed to appropriate officers based
  on jurisdiction, document type, and workload
- **Escalation timers**: If an officer doesn't act within SLA, the
  application escalates automatically
- **Conditional approvals**: Multi-department certificates (e.g., building
  permits requiring clearances from fire, municipal, environmental
  departments) managed as composite workflows with parallel/sequential
  smart contract orchestration
- **Expiry management**: Certificates with validity periods (income
  certificates: 1 year, caste certificates: lifetime) automatically
  flagged for renewal or marked expired

**5. Universal Verification API**

A public, permissionless verification endpoint that requires no account,
no login, no intermediary:

- Any third party (bank, employer, university, welfare office) can verify a
  certificate by scanning a QR code or entering the certificate ID
- Returns: issuance status, issuing authority, validity, lifecycle
  completeness score, and ZK-proof-based attribute confirmations
- Works offline via cryptographic proof embedded in the certificate itself
  (verifiable even without network access using the issuing authority's
  public key)

---

## Blockchain Applicability

<!-- 
  - Explain how blockchain technology is applicable to the identified
    problem.
  - Discuss the benefits of using blockchain, such as decentralization,
    transparency, and immutability.
-->

### Why Blockchain is Essential (Not Optional) for This Problem

**Immutability** — Certificates are altered after issuance; approval records
tampered with to cover irregularities. Blockchain makes every lifecycle event
permanent and tamper-detectable.

**Decentralization** — No single trusted authority exists across departments,
states, and third-party verifiers. A shared ledger removes reliance on any
single department's database.

**Transparency** — Citizens cannot see where their application is stuck or
who acted on it. Blockchain makes every lifecycle event visible to authorized
stakeholders in real-time.

**Non-repudiation** — Officers deny approvals; departments dispute issuance.
Cryptographically signed actions (via DSCs) cannot be denied post-facto.

**Smart Contracts** — Manual routing, missed SLAs, no automatic escalation.
Smart contracts automate workflow routing, enforce SLAs, and orchestrate
multi-department approvals.

**Auditability** — RTI requests to trace document history are slow and
incomplete. Blockchain provides a complete audit trail available instantly
for authorized auditors.

### Why a Database Cannot Solve This

The fundamental issue is **multi-stakeholder trust across organizational
boundaries**. When a bank in Maharashtra needs to verify an income
certificate issued in Tamil Nadu:

- A centralized database requires both states to trust the database operator
- A state-run database requires the bank to trust that the state hasn't
  altered records
- An officer accused of irregularity can claim the centralized database was
  modified

Blockchain eliminates these trust requirements. The mathematical guarantees
of immutability and cryptographic signatures mean verification doesn't depend
on trusting any single party — it depends on trusting mathematics.

---

## Technical Approach and Architecture

<!-- 
  - Outline the technical approach and architecture of the proposed solution.
  - The architecture should be modular with API integration support and
    replicable.
  - Describe the components, interactions, and data flows.
-->

### Platform Stack

- **Blockchain — Hyperledger Fabric 3.0+**: Permissioned DLT with SmartBFT
  consensus, channel isolation, private data collections, and endorsement
  policy flexibility
- **Middleware — Hyperledger FireFly**: Multi-party orchestration, REST API
  gateway, event-driven notifications, off-chain data management
- **Identity & Signing — DSC (CCA) + Hyperledger Indy**: Government officers
  sign transactions using existing Digital Signature Certificates issued by
  CCA-licensed authorities (eMudhra, NIC CA, etc.). Hyperledger Indy provides
  the DID/schema layer for verifiable credentials and AnonCreds-based ZK
  proofs for citizen-facing selective disclosure
- **Oracle — Custom (Rule Engine + AI)**: Rule-based anomaly detection
  (seeded from e-District historical data), evolving to ML models. Integration
  with DigiLocker, Aadhaar, and e-District APIs
- **Storage — IPFS + PostgreSQL**: IPFS for document content (hashes
  on-chain), PostgreSQL for off-chain queryable metadata and analytics
- **Application Layer — Web (PWA) + Mobile**: Progressive Web App as the
  primary interface for officers and citizens (works on any device, offline
  capable). Native iOS and Android apps planned for later phases to leverage
  device capabilities (camera for inspector evidence, biometrics for officer
  auth)

### Network Topology (Hyperledger Fabric 3.0+)

- **Channel 1: Document Lifecycle Channel** — Issuing department, reviewing
  officers, approving authority, citizen (read-only)
- **Channel 2: Inter-Department Channel** — Multiple departments for
  composite workflows (e.g., building permits, passport verifications
  requiring police + revenue clearances)
- **Channel 3: Verification Channel** — Third-party verifiers (banks,
  employers, universities, welfare departments) with read-only access to
  issued certificate metadata
- **Private Data Collections** — Sensitive citizen data (income details,
  medical information) accessible only to authorized officers within the
  issuing department

**Consensus: SmartBFT** — Fabric 3.0 replaces Raft with SmartBFT (Byzantine
Fault Tolerant) as the recommended ordering service. This is critical for
PramaaN's multi-department model: when ordering nodes are operated by
independent government departments (revenue, education, municipal), BFT
consensus ensures that no single compromised or rogue department node can
corrupt transaction ordering. SmartBFT tolerates up to f malicious nodes out
of 3f+1 total — the exact trust model needed for inter-ministry and
inter-state document systems where departments don't fully trust each other's
infrastructure.

### Smart Contract Suite (Chaincode)

1. **Application Contract** — Citizen application submission, status
   tracking, document upload, fee payment recording
2. **Workflow Contract** — Configurable multi-step approval routing, SLA
   timers, automatic escalation, parallel/sequential department clearances
3. **Verification Contract** — Field verification recording by inspectors
   with geo-tagged evidence, photo hash anchoring
4. **Issuance Contract** — Final certificate generation trigger, DSC-based
   digital signature recording, QR code generation with embedded
   cryptographic proof
5. **Lifecycle Contract** — Amendment, renewal, revocation management with
   full backward-linking to original issuance
6. **Audit Contract** — Query interface for authorized auditors, RTI response
   automation, statistical reporting

### API Integration Points (via Hyperledger FireFly)

- **DigiLocker** — Push issued certificates for citizen access
- **Aadhaar/eKYC** — Identity verification for applicants
- **e-District portals** — Bidirectional sync with existing state systems
- **NIC blockchain infrastructure** — Interoperability with existing
  Certificate Chain and Document Chain deployments via blockchain.gov.in
- **UMANG** — Integration for citizen-facing services
- **eSign API** — Aadhaar-authenticated remote signing for officers without
  physical DSC tokens
- **Payment gateways** — Application fee collection and tracking
- **SMS/email gateways** — Status notifications to citizens

### Data Flow (Single Certificate Lifecycle)

1. Citizen submits application via PWA/portal → Application Contract creates
   on-chain record
2. System auto-routes to jurisdictionally appropriate officer → Workflow
   Contract assigns based on rules
3. Officer reviews, requests field verification → Workflow Contract dispatches
   to inspector
4. Inspector visits site, uploads geo-tagged evidence via mobile app →
   Verification Contract anchors findings
5. Reviewing officer examines verification report → Workflow Contract records
   review decision
6. Approving authority reviews and approves → Workflow Contract records
   multi-level approval
7. Authorized signatory signs using DSC → Issuance Contract generates
   certificate with QR code
8. Certificate pushed to DigiLocker + citizen notification → API integration
   via FireFly
9. Third party scans QR code → Verification Channel returns cryptographic
   proof of entire lifecycle
10. Certificate expires/amended/revoked → Lifecycle Contract records with
    full audit trail

---

## Benchmarking and Differentiation

<!-- 
  - Compare the proposed solution with existing solutions.
  - Highlight the differentiation factors, such as unique features, improved
    efficiency, or enhanced security.
-->

### Existing Solutions

**DigiLocker** — Document wallet/storage. No lifecycle tracking (stores final
certificates only). No multi-department workflows. Full document shared or
nothing. No fraud detection. Third-party verification requires DigiLocker
integration. Limited cross-state interop (issuer must integrate).

**NIC Certificate Chain (blockchain.gov.in)** — Live blockchain anchoring
of academic certificates. Used by CBSE (80K+ certs, 2.1 crore txns),
Karnataka SSLC/PUC boards (1.43 crore txns), Maharashtra nursing board, and
others. Significant achievement in proving blockchain viability for Indian
government documents. **Limitation**: Anchors only the *final issued
certificate* — no lifecycle tracking of the drafting, review, and approval
process. No cross-department workflows. No fraud detection on approval
patterns. No selective disclosure.

**NIC Document Chain (blockchain.gov.in)** — Stores government-issued
documents (caste, income, birth/death certs, ration cards) on-chain.
Karnataka Revenue Dept (3.77 crore txns since Jan 2018), Delhi Revenue Dept
(7.8 lakh txns), Puducherry Civil Supplies. **Same limitation**: records
the final document only, not the approval workflow that produced it.

**NIC Property Chain (blockchain.gov.in)** — Integrated with Karnataka's
Bhoomi, e-Asthi, e-Swathu systems (40.4 crore reads, 2.09 crore txns).
Also deployed in Jharkhand. Anchors property records but does not model the
registration workflow lifecycle.

**National Blockchain Framework (NBF) / Vishvasya** — MeitY's national
blockchain technology stack (launched Sept 2024, Rs 64.76 crore outlay).
Deployed across NIC data centres in Bhubaneswar, Pune, and Hyderabad. 34+
crore documents verified as of Oct 2025. PramaaN is designed to be
**compatible with and deployable on NBF infrastructure**, extending it with
lifecycle tracking capability.

**Blockcerts (MIT)** — Academic credential issuance only. Issues final
credentials, no lifecycle tracking. Verification requires blockchain node.

**LegitDoc (India)** — Private credential verification. Verifies final
documents only. Requires LegitDoc account. Per-client integration.

**Estonia X-Road + KSI Blockchain** — Government data exchange backbone
with blockchain integrity layer. Closest to a lifecycle model but built on
an entirely different governance structure and not applicable to India's
federal, multi-state document ecosystem.

### Key Differentiators

1. **Lifecycle-first, not certificate-first.** Every existing solution —
   including NIC's blockchain pilots — treats the document as a static
   artifact to be stored or hashed. PramaaN treats the document as a
   *process*. The trust comes from recording the entire journey, not just
   the destination. A fake certificate has no lifecycle — and that absence
   is immediately detectable.

2. **Builds on proven Indian blockchain infrastructure.** PramaaN is not
   starting from scratch. NIC's Certificate Chain and Document Chain have
   proven that blockchain works for Indian government documents at scale
   (106+ crore transactions). PramaaN extends this foundation with the
   lifecycle layer, workflow automation, and fraud detection that these
   systems currently lack.

3. **Privacy-preserving verification via ZK proofs.** Citizens can prove
   facts (income above threshold, age eligibility) without revealing
   sensitive details — a capability no existing Indian government document
   system offers. The same infrastructure could serve ABDM for health
   record selective disclosure.

4. **DSC integration for legally valid digital signatures.** Rather than
   introducing a new identity layer, PramaaN integrates with India's
   existing Digital Signature Certificate infrastructure under CCA —
   the same DSCs that government officers already use for e-tendering,
   MCA filings, GST, and income tax. This means zero identity onboarding
   friction for government departments.

5. **Department-agnostic, replicable design.** The workflow engine is
   configurable, not hardcoded. The same platform models revenue
   certificates, educational credentials, property documents, and municipal
   licenses by changing workflow configuration — not code.

---

## Non-Crypto Blockchain Platform

<!-- 
  - Specify the non-crypto blockchain platform planned for development (e.g.,
    Hyperledger Fabric, Corda).
  - Explain how the chosen platform effectively addresses the identified
    problem.
-->

### Platform: Hyperledger Fabric 3.0+

**Why Hyperledger Fabric 3.0:**

- **SmartBFT consensus** — Fabric 3.0's headline feature. Byzantine Fault
  Tolerant consensus that tolerates up to f malicious/faulty ordering nodes
  out of 3f+1 total. Essential when ordering nodes are operated by
  independent government departments that don't fully trust each other's
  infrastructure. Raft (Fabric 2.x) only handled crash faults — a
  compromised orderer could corrupt the ledger. SmartBFT eliminates this
  risk.
- **Permissioned network** — only authenticated government departments and
  authorized verifiers can participate, aligned with government security
  requirements
- **Channel architecture** — enables data isolation between departments
  (revenue data invisible to education department) while maintaining
  cross-department workflow capability
- **Private Data Collections** — sensitive citizen information (income
  details, medical records) shared only between authorized officers, never
  visible to verifiers
- **Chaincode in Go/Node.js** — production-grade smart contract execution
  with deterministic behavior
- **No cryptocurrency** — no tokens, no mining, no speculative elements.
  Fully compliant with Indian regulatory stance
- **Endorsement policies** — configurable per document type (e.g., property
  documents require endorsement from both sub-registrar and revenue
  department)

**Hyperledger FireFly (Middleware):**

- REST API gateway for integration with existing e-District portals,
  DigiLocker, and UMANG without requiring each department to run blockchain
  infrastructure
- Event-driven architecture for real-time citizen notifications
- Off-chain data exchange with on-chain anchoring for large documents
  (scanned copies, photographs)

**Identity & Signing — DSC (CCA) + Hyperledger Indy:**

- **Digital Signature Certificates (DSCs)** issued by CCA-licensed
  authorities (eMudhra, NIC CA, CDAC, Capricorn, etc.) are already used
  by government officers for e-tendering, MCA filings, GST returns, and
  income tax. PramaaN maps DSC private keys to Fabric transaction signing
  and anchors the DSC certificate chain in channel MSPs (Membership Service
  Providers). This means officers sign on-chain transactions with the same
  DSC they already use — zero new credentialing required.
- **eSign API** (Aadhaar-based remote signing) provides a fallback for
  officers without physical DSC tokens, enabling authenticated document
  signing via Aadhaar OTP.
- **Hyperledger Indy** provides the DID/schema layer for issuing Verifiable
  Credentials to citizens and enabling AnonCreds-based ZK proofs for
  selective disclosure. Indy is purpose-built for decentralized identity
  and credential schemas — exactly what's needed for citizen-facing
  credential issuance.

### Why Not Other Platforms

- **Corda**: Designed for bilateral financial agreements. Lacks the
  multi-channel, multi-stakeholder broadcast capability needed for
  government document workflows involving 5-10 departments.
- **Polygon/Ethereum L2**: Public chain derivatives carry regulatory risk
  in India. Government data on public chains — even permissioned variants —
  raises data sovereignty concerns. (Note: Amravati's Polygon-based land
  records pilot is a notable experiment, but PramaaN requires the
  enterprise-grade permissioning and channel isolation that only Fabric
  provides.)
- **Hyperledger Fabric 3.0 is the only fully non-crypto, government-grade,
  BFT-capable stack** combining DLT + middleware + identity + privacy (ZK
  proofs) in a single ecosystem. It is also compatible with MeitY's
  National Blockchain Framework (Vishvasya).

---

## Permissioned Blockchain and Smart Contracts

<!-- 
  - Describe the use of permissioned blockchain and smart contracts in the
    proposed solution.
  - Explain how these features enhance the solution's functionality and
    security.
-->

### Permissioned Network Design

**Organizations (MSPs)**

1. **PramaaN Network Operator** — Platform administration, network
   governance, technical operations
2. **State Revenue Department** — Income, caste, domicile, birth/death
   certificates
3. **Education Department / University** — Degree certificates, mark sheets,
   transcripts
4. **Municipal Corporation** — Birth/death certificates, trade licenses,
   property tax records
5. **Sub-Registrar Office** — Property registration documents
6. **Third-Party Verifiers** — Banks, employers, universities (read-only
   verification access)
7. **Audit Authority** — CAG, state audit departments (read-only audit
   access)

**Access Control Matrix**

- Citizens can view their own applications, track status, download issued
  certificates, and manage consent for third-party verification
- Issuing officers can create, review, and approve documents within their
  jurisdiction only — enforced by DSC identity mapping to department roles
- Field inspectors can upload verification reports only for assigned
  applications
- Verifiers can query certificate validity and lifecycle completeness — no
  access to internal workflow details
- Auditors can query full lifecycle data across departments for audit
  purposes

### Smart Contract Details

**Workflow Contract (Core)**

```
States: SUBMITTED → ASSIGNED → UNDER_REVIEW →
        FIELD_VERIFICATION → VERIFIED → APPROVED →
        SIGNED → ISSUED → ACTIVE → EXPIRED / REVOKED

Triggers:
  - ASSIGNED: Auto-route based on jurisdiction + workload
  - FIELD_VERIFICATION: Officer requests physical check
  - VERIFIED: Inspector submits report
  - APPROVED: Multi-level approval chain complete
  - SIGNED: Authorized signatory signs with DSC
  - ISSUED: Certificate generated + pushed to DigiLocker
  - EXPIRED: Validity period elapsed (auto-triggered)
  - REVOKED: Authority cancels with documented reason

SLA Enforcement:
  - Each state transition has configurable time limit
  - Breach triggers automatic escalation to supervisor
  - SLA metrics recorded on-chain for performance auditing
```

**Verification Contract**

```
Input: Certificate ID or QR code scan
Output:
  - Issuance status (ACTIVE / EXPIRED / REVOKED)
  - Issuing authority and department
  - Issuance date and validity period
  - Lifecycle completeness score (0-100%)
  - ZK proof responses for attribute queries
  - Cryptographic proof chain (verifiable offline)

Access: Public — no authentication required
```

**Composite Workflow Contract**

```
For multi-department certificates (e.g., building permits):

Parallel tracks:
  Track A: Fire department clearance
  Track B: Municipal planning approval  
  Track C: Environmental clearance

Merge condition: All tracks reach APPROVED state
Final issuance: Only when composite condition satisfied

Each track is an independent workflow with its own SLA,
linked by the composite contract
```

---

## Regulatory Framework

<!-- 
  - Discuss how the proposed solution complies with the regulatory framework
    of the domain.
  - Highlight any relevant laws, regulations, or standards.
-->

### Indian Regulatory Compliance

- **Information Technology Act, 2000 (amended 2008)** — Sections 3A and 5
  recognize electronic signatures and electronic records. PramaaN's use of
  DSCs issued by CCA-licensed authorities means all on-chain signatures are
  legally valid under the IT Act — the same legal standing as DSC signatures
  used in e-tendering and MCA filings today.
- **Indian Evidence Act, Section 65B** — Electronic records are admissible
  as evidence when accompanied by a certificate identifying the source.
  PramaaN's immutable audit trail directly provides superior evidentiary
  chain compared to database-stored records.
- **Digital Personal Data Protection Act, 2023 (DPDPA)** — Consent-based
  data processing, data minimization, purpose limitation. PramaaN
  implements: citizen consent management for third-party verification,
  personal data stored off-chain with only hashes on-chain, ZK proofs
  enabling verification without exposing personal data, and "data
  fiduciary" obligations mapped to department roles.
- **Right to Information Act, 2005** — Citizens' right to access government
  records. PramaaN's transparent lifecycle tracking directly supports RTI
  objectives by making document processing history auditable and accessible.
- **MeitY National Blockchain Strategy (2021)** — Explicitly identifies
  document management and certificate verification as priority use cases.
  Recommends permissioned blockchains for government applications — exactly
  PramaaN's approach.
- **National Blockchain Framework (NBF / Vishvasya, 2024)** — MeitY's
  national blockchain technology stack. PramaaN is designed to be deployable
  on NBF infrastructure (NIC data centres in Bhubaneswar, Pune, Hyderabad),
  ensuring alignment with government's own blockchain strategy.
- **e-Governance Standards** — Architecture follows MeitY's IndEA (India
  Enterprise Architecture) framework for interoperability across government
  departments.
- **CCA (Controller of Certifying Authorities) Framework** — PramaaN's DSC
  integration operates within the existing CCA-regulated PKI hierarchy,
  requiring no new regulatory approval for digital signing.

### Standards Compliance

- **W3C Verifiable Credentials** — Issued certificates follow W3C VC
  standard for global interoperability
- **W3C Decentralized Identifiers (DIDs)** — Identity framework built on
  W3C DID specification via Hyperledger Indy
- **BIS standards for electronic records** — Document formats and metadata
  schemas aligned with Bureau of Indian Standards specifications

---

## Security, Privacy, Scalability and Performance

<!-- 
  - Explain how the proposed solution addresses security, privacy,
    scalability and performance requirements.
  - Describe the measures taken to ensure the solution's robustness and
    reliability.
-->

### Security

- **DSC-based authentication** — Officers sign transactions using Digital
  Signature Certificates issued by CCA-licensed authorities, providing
  legally valid, non-repudiable identity. DSC certificate chains anchored
  in Fabric channel MSPs.
- **Role-based access control (RBAC)** enforced at chaincode level —
  officers can only act within their jurisdiction and role
- **TLS 1.3 encryption** for all peer-to-peer and client-to-peer
  communication
- **Hardware Security Modules (HSM)** for key management at department
  level — ordering node and peer signing keys never leave secure hardware
- **SmartBFT consensus** — tolerates malicious ordering nodes, preventing
  a compromised department from corrupting transaction ordering
- **Multi-signature requirements** for high-sensitivity documents (e.g.,
  property registrations require both sub-registrar and witness signatures
  on-chain)
- **Smart contract audit** by third-party security firm before production
  deployment
- **Tamper-evident logging** — all administrative actions (user creation,
  role assignment, policy changes) recorded on a separate audit channel

### Privacy

- **Channel isolation** — revenue, education, and municipal data on
  separate channels; departments cannot access each other's internal
  workflows
- **Private Data Collections** — sensitive citizen information (income
  amounts, medical details) shared only between authorized officers in
  the issuing department
- **Zero-knowledge proofs (via Indy AnonCreds)** — citizens can prove
  attributes (income above threshold, age eligibility) without revealing
  underlying data to verifiers
- **Off-chain document storage (IPFS)** — actual document content never
  stored on-chain; only cryptographic hashes. Supports right-to-erasure
  by deleting off-chain content while preserving on-chain integrity hashes
- **Citizen-controlled consent** — third-party access to document details
  requires explicit citizen authorization via the app; consent is
  time-limited and revocable

### Scalability

- **Target: 10,000 certificates/day per state at pilot; 100,000+/day at
  scale**
- **Fabric 3.0+ with SmartBFT**: Production-grade BFT consensus with
  throughput sufficient for all Indian states combined
- **Horizontal scaling**: Additional peers per department as volume grows;
  new states added as new organizations on existing channels
- **Off-chain computation**: Anomaly detection engine runs off-chain, only
  results/flags anchored on-chain
- **Modular channel architecture**: New document types added as workflow
  configurations, not new channels — enabling rapid department onboarding

### Performance Targets

| **Metric** | **Current (Manual)** | **PramaaN Target** |
|---|---|---|
| Certificate issuance time | 7-30 days | 1-3 days |
| Third-party verification | 2-6 weeks | Under 10 seconds |
| Cross-state verification | 30-90 days | Under 10 seconds |
| Fraud detection | Post-facto (if ever) | Real-time alerts |
| RTI response (doc history) | 30 days | Instant |
| Application status visibility | Opaque | Real-time tracking |

---

## Execution Plan

<!-- 
  - Provide a detailed execution plan, including milestones, timelines, and
    resource allocation.
  - Outline the development, testing, and deployment phases.
-->

### Phase 1: Prototype (Month 1-3)

- Deploy Hyperledger Fabric 3.0 test network with SmartBFT (2 orgs:
  PramaaN operator + 1 state revenue department)
- Implement core chaincode: Workflow Contract + Verification Contract for
  revenue certificates (income, caste, domicile)
- Build officer PWA dashboard (application review, approval, issuance)
- Build citizen PWA for application submission and status tracking
- Implement QR-code-based verification endpoint
- Integrate DSC signing for officer transactions
- Demo with retrospective anchoring of existing certificate data from one
  district

### Phase 2: MVP (Month 4-8)

- Expand network to 4 organizations (add education department + municipal
  corporation)
- Deploy Hyperledger FireFly middleware for API gateway
- Implement Composite Workflow Contract for multi-department certificates
- Build rule-based anomaly detection engine (seeded from e-District
  historical data)
- Integrate with DigiLocker sandbox for certificate push
- Integrate Hyperledger Indy + AnonCreds for ZK-proof-based selective
  disclosure
- Integrate eSign API for Aadhaar-based remote signing
- Run parallel pilot: 1 district issuing certificates through PramaaN
  alongside existing e-District system

### Phase 3: Production Deployment (Month 9-14)

- Production network with 6+ department organizations on SmartBFT
- Full smart contract suite operational with SLA enforcement
- DigiLocker production integration
- Aadhaar eKYC integration for applicant identity verification
- Native mobile apps (iOS + Android) for field inspectors (geo-tagged
  verification with offline capability)
- ML anomaly detection model trained on pilot data
- Multi-district expansion within pilot state
- Target: 5,000+ certificates issued, 3+ departments live, 50,000+
  verifications processed

### Infrastructure & Operational Costs

| **Item** | **Monthly Estimate** |
|---|---|
| Cloud infrastructure (NIC Cloud / AWS GovCloud) — Fabric peers, orderers, CAs, FireFly nodes | Rs 1.5-3L |
| HSM-as-a-Service for department signing keys | Rs 50K-1L |
| IPFS pinning and storage | Rs 20-50K |
| DigiLocker / Aadhaar eKYC / eSign API usage fees | Rs 30-60K |
| CI/CD, monitoring, logging (Grafana, Prometheus) | Rs 20-40K |
| Domain, SSL, CDN for PWA hosting | Rs 10-20K |
| Security audit (one-time, Phase 2) | Rs 5-10L |
| Third-party smart contract audit (one-time, Phase 3) | Rs 3-5L |

Total recurring infrastructure: approximately Rs 2.5-5L/month during pilot.
One-time audit costs: Rs 8-15L across Phase 2-3.

---

## Expected Outcomes and Pilot Deployment

<!-- 
  - Describe the expected outcomes of the proposed solution.
  - Outline the plan for pilot deployment, including the scope, timeline,
    and evaluation metrics.
-->

### Prototype Outcomes

- Functional blockchain network recording full document lifecycle for
  revenue certificates on Fabric 3.0 with SmartBFT
- Demonstrated instant verification via QR code (seconds vs. weeks)
- Complete audit trail for every issued certificate — from application to
  issuance, with DSC-signed approvals at each step
- Rule-based anomaly flagging operational on approval patterns
- ZK-proof selective disclosure demonstrated for income certificates

### Pilot Deployment Plan

**Scope**: 1 district in a partner state (target: Karnataka, given existing
NIC blockchain deployments via Document Chain and Property Chain in the
state), covering revenue certificates (income, caste, domicile) and
municipal certificates (birth, death, trade license)

**Timeline**: 6 months post-prototype

**Evaluation Metrics**:

- Certificate issuance time reduction (target: 70%+ faster)
- Third-party verification time (target: under 10 seconds vs. current
  2-6 weeks)
- Fraud incidents detected (target: 100% of anomalous patterns flagged)
- Citizen satisfaction score (target: 80%+ rating in pilot surveys)
- Officer adoption rate (target: 90%+ of pilot department officers actively
  using the platform)
- Cost savings per certificate (target: 40%+ reduction in verification and
  processing costs)

**Scale Path**: 1 district → full pilot state → 5 states → pan-India. Each
new state joins as a new organization on the Fabric network —
configuration-based onboarding, not code changes.

---

## Government Department Collaboration

<!-- 
  - Identify the government departments with which the startup plans to
    collaborate.
  - Explain how the proposed solution is relevant to these departments and
    how it can benefit them.
  - Define a viable Business Model and plan for a Wider Proliferation
    Strategy across India for different states and UTs.
-->

### Target Departments

1. **Ministry of Electronics and Information Technology (MeitY)** —
   Challenge organizer. PramaaN contributes to the National Blockchain
   Framework (Vishvasya) and aligns with MeitY's National Blockchain
   Strategy (2021) which explicitly prioritizes document management.
2. **National Informatics Centre (NIC)** — Critical integration partner.
   NIC already operates Certificate Chain, Document Chain, and Property
   Chain via blockchain.gov.in across 18 departments and 11 states.
   PramaaN extends NIC's proven infrastructure with lifecycle tracking.
   Target deployment on NIC Cloud / MeghRaj for data sovereignty.
3. **State Revenue Departments (Karnataka / Maharashtra)** — Primary pilot
   partner. Karnataka's Revenue Dept already has 3.77 crore blockchain
   transactions on NIC's Document Chain. Revenue certificates (income,
   caste, domicile) are the highest-volume, highest-fraud-risk document
   category.
4. **Ministry of Education / UGC** — Academic credential verification.
   CBSE already has 80K+ certificates on NIC's Certificate Chain.
   PramaaN adds lifecycle tracking and employer-facing verification APIs.
5. **Ministry of Housing and Urban Affairs** — Municipal certificate
   digitization. Aligns with Smart Cities Mission objectives for digital
   governance.
6. **Comptroller and Auditor General (CAG)** — PramaaN's complete lifecycle
   audit trail directly supports CAG's mandate for government process
   accountability.

### Business Model

- **Platform licensing**: Annual licensing fee to state governments for
  deploying PramaaN in their departments (tiered by state population /
  certificate volume)
- **Verification API**: Per-verification fee for third-party commercial
  verifiers (banks, employers, background check companies) — free for
  citizens and government departments
- **Integration services**: Implementation and integration support for
  onboarding new departments and states
- **Premium analytics**: AI-powered dashboards for department heads and
  audit authorities — processing bottleneck identification, fraud risk
  heatmaps, SLA compliance reports

### Wider Proliferation Strategy

1. **State-by-state rollout** starting with states that already have NIC
   blockchain deployments (Karnataka, Delhi, Puducherry, Jharkhand) — these
   departments already understand blockchain and have operational experience
2. **Integration with existing government platforms** — DigiLocker, e-District
   portals, UMANG, and NIC's existing blockchain infrastructure — for
   seamless adoption without disrupting citizen-facing interfaces
3. **NBF (Vishvasya) compatibility** — deploying on MeitY's National
   Blockchain Framework infrastructure ensures government buy-in and
   eliminates data sovereignty concerns
4. **Document type expansion**: Revenue certificates → educational
   credentials → property documents → municipal licenses → judicial
   documents
5. **Replicable architecture**: Any state can onboard by deploying their
   organization node and configuring department-specific workflows — no
   custom development required per state

---

## Additional Details

<!-- 
  - Provide any additional details relevant to the idea, such as market
    analysis, user-adoption strategies, or potential partnerships.
-->

### Market Size

- Government certificates issued annually in India: estimated 200M+ across
  all categories
- Revenue certificates alone: 100M+ per year across states
- Verification market (background checks, bank KYC, education verification):
  estimated $1-2B annually in India
- Government IT spending on document digitization: growing at 15%+ annually
  under Digital India initiatives
- NIC's blockchain infrastructure already processes 106+ crore transactions
  across document types — validating demand and feasibility at national scale

### User Adoption Strategy

- **For citizens**: No behavior change required — apply through existing
  portals/apps (PramaaN integrates behind the scenes). Verification via QR
  code is simpler than current manual processes. PWA-first approach means
  no app installation needed.
- **For officers**: DSC integration means they sign with the same credentials
  they already use. Training program + gradual rollout. PramaaN's officer
  dashboard is designed to simplify existing workflows, not complicate them.
  SLA timers and auto-routing reduce manual coordination overhead.
- **For verifiers**: Simple API integration or manual QR scan — no blockchain
  knowledge required. Banks and employers get instant results instead of
  waiting weeks.

### Potential Partnerships

- **National Informatics Centre (NIC)** — Infrastructure, blockchain.gov.in
  interoperability, and government system integration
- **C-DAC** — NBF / Vishvasya technical partner, blockchain challenge
  co-organizer
- **DigiLocker team (MeitY)** — Certificate push integration
- **UIDAI** — Aadhaar eKYC and eSign API integration
- **CCA / eMudhra** — DSC infrastructure partnership for officer identity
- **State IT departments** (Karnataka IT/BT, Maharashtra IT) — Pilot
  deployment partners
- **Indian Banks Association** — Verification API adoption for KYC and loan
  processing

---

## Signature and Team Information

<!-- 
  - Include the signatures of the startup founder and team members.
  - Provide contact information and relevant details about the team members.
-->

*To be filled with:*

- **Founder**: [Name], [Company]
- **Team members and roles**: [To be added]
- **Contact**: [To be added]
- **DPIIT Registration**: [To be added]
- **Company**: [To be added]
- **Registered Address**: [To be added]
