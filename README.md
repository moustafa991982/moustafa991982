# Moustafa El Bahaey

**Chief Systems Engineer · Automotive Cybersecurity & Embedded Systems**

18 years building secure embedded platforms across OEMs and Tier-1s — Ford, CEER Motors (Saudi EV OEM), Aptiv, Valeo, Arrow. Currently leading systems engineering at [EVRaid](https://www.evraid.com).

I work where automotive functional safety, cybersecurity engineering, and modern confidential-computing trust models intersect — ISO/SAE 21434, UN R155/R156, AUTOSAR Classic & Adaptive, HSM/PKI architecture, QNX RTOS security, SecOC, post-quantum cryptography for SDV, and TARA methodology.

📍 Silver Spring, Maryland, USA · 🌍 Available for international engagements · 🗣️ Arabic / English / German

#PQC
---

## 🔐 Featured Projects

### [pqc-sdv-cvm](https://github.com/moustafa991982/pqc-sdv-cvm)
**Post-quantum TLS to a Software-Defined Vehicle cloud backend — end-to-end on Azure SEV-SNP.**

A measurement-grade reference architecture for what it actually costs to make an SDV cloud backend quantum-safe today, broken down by which layer of the stack you harden. Runs on real Azure infrastructure with measurements captured over a public-internet WAN path from a QEMU simulated VCU.

- **TLS 1.3 with hybrid X25519MLKEM768 KEM** terminated by nginx + OpenSSL 3.5 inside an Azure AMD SEV-SNP confidential VM (`Standard_DC2as_v5`)
- **Three certificate chains compared side-by-side:** `classical` (ECDSA throughout), `mixed` (ML-DSA-87/65 root + sub-CA, ECDSA leaf — the realistic 2027–2030 V2G PKI shape), `pqc` (ML-DSA all the way)
- **Azure Key Vault Premium with Secure Key Release** — wrap keys bound to MAA attestation policies; leaf private keys as SKR-released secrets; cert chains served from Azure Blob Storage (ML-DSA chains exceed Key Vault's 25 KB secret limit — documented design pattern)
- **Measured findings:** hybrid PQC KEM costs **+2.4 KB per handshake** to defeat harvest-now-decrypt-later; PQ-protecting the trust anchor costs **+18 KB** and **doubles TCP segments** on the wire; PQ leaf adds another **+3 KB** per handshake
- **Honest limitations catalogue** — 12 production-blocking issues encountered and worked around, including the "Path 3" framing for SEV-SNP attestation on Ubuntu 22.04 CVM kernels (`/dev/sev-guest` not yet exposed, runtime falls back to managed-identity RBAC while preserving the SKR architecture)
- Relevant to ISO 15118-20 PnC certificate-chain sizing, V2G Root rollover planning, NSA CNSA 2.0 timeline guidance


### [HSMConfidentialContainer](https://github.com/moustafa991982/HSMConfidentialContainer)
**Confidential-computing HSM daemon for Software-Defined Vehicle secure boot key provisioning.**

A production-style HSM daemon packaged for Azure Confidential Containers, targeting AMD SEV-SNP and Intel TDX confidential VMs on AKS / ACI. Demonstrates a modern alternative to on-premise HSMs for SDV key-provisioning pipelines, with hardware-rooted attestation and tenant isolation in the cloud.

- Multi-arch Docker image published to Azure Container Registry
- Built in Go, designed around remote-attestation flows
- Use case: OEM key-provisioning at end-of-line, fleet-scale credential rotation, cryptographic operations for ISO 15118 Plug & Charge contract certificates



### [QNX-Resource-manager-attacks-with-Secpol-enabled](https://github.com/moustafa991982/QNX-Resource-manager-attacks-with-Secpol-enabled)
**Offensive security research on QNX 8.0 secpol — supply-chain attack scenarios on automotive ECUs.**

Two attack scenarios discovered during ECU security research, demonstrated against QNX 8.0 with secpol policy enforcement enabled:

1. **Trojan resource manager IPC backdoor** — exploiting `transition_rm` and `secpol_transition_type()` flows to inject a malicious resource manager into a hardened policy.
2. **Pre-transition entropy poisoning** — corrupting `/dev/random` consumers before the secpol transition takes effect, undermining downstream cryptographic operations.

Includes the secpol policy authoring, `secpolgenerate` / `secpolpush` workflows, and root-cause analysis (`resmgr_init` typing, errno 314).



### [Cpyr](https://github.com/moustafa991982/Cpyr)
**Deep anomaly detection for in-vehicle networks — reference implementation for SAE 2021-01-0196 (SOTIF in practice).**

A semi-supervised deep learning framework for detecting cyber-physical anomalies on automotive networks, addressing two distinct problems with a shared codebase:

1. **Fuzz-attack detection on automotive Ethernet** — reconstruction-based autoencoders (Conv encoder, U-Net, Einstein-sum, U-Net + transformer-decoder variants) trained only on normal traffic. Hex-to-binary preprocessing collapses the output space and enables a **1.2 KB convolutional encoder** to match a 223 MB transformer on separation quality — small enough for ECU deployment.
2. **LKA contextual anomaly detection (SOTIF case study)** — predictive context models (VIS predictor, LKA predictor) detect single-frame contextual anomalies, e.g., LKA disabled during a lane switch the driver did not initiate. Achieves **instantaneous trigger** (zero-batch lag) on the injected anomaly, validated with both BCE and SSIM losses.

Companion to the SAE WCX 2021 paper *Putting Safety of Intended Functionality SOTIF into Practice* and the [ASRG community talk](https://www.youtube.com/watch?v=z3uAQIN0nYw).


### [AI Agent Portfolio](https://github.com/moustafa991982/ai-agent-portfolio)
**Production-deployed AI agents for research, content automation, sales intelligence, and RAG-based document Q&A.**

A curated collection of 17+ AI agents built and deployed on Mind Studio, covering executive workflows from automated research reports and competitive intelligence to a domain-specific *EV Charging Management* RAG chatbot that ties directly into the e-mobility space I work in. Each agent is live and remixable.

- **Research & intelligence:** webpage / YouTube / PDF summarizers, multi-source research report generator with citations, website-change monitor, company intelligence crawler
- **Communication automation:** email thread summarizer & response drafter, personalized cold-outreach generator, LinkedIn post generator with human-review workflow, daily news digest delivery
- **Domain RAG chatbots:** "Ask the Docs" assistants for Mind Studio and for EV charging station documentation


---

## 🛠️ Core Expertise

| Domain | |
|---|---|
| **Standards & Regulation** | ISO/SAE 21434 · UN R155 / R156 · ISO 15118-2/-20 · ASPICE for Cybersecurity · NSA CNSA 2.0 |
| **Platforms & RTOS** | QNX 8.0 · AUTOSAR Classic & Adaptive · Linux for safety-critical systems |
| **Cryptography & PKI** | HSM integration (Aurix, CycurHSM) · OEM / V2G / eMSP / CPO PKI chains · SecOC · MACsec · **post-quantum cryptography (ML-KEM, ML-DSA, hybrid TLS 1.3)** |
| **Confidential Computing** | AMD SEV-SNP · Intel TDX · Azure Confidential VMs & Containers · Microsoft Azure Attestation · Secure Key Release |
| **Applied AI** | Multi-agent workflow design · RAG architectures · safety-critical AI (SOTIF / ISO 21448) · vision-anomaly detection |
| **Methodology** | TARA · CSMS · SBOM (SPDX-2.3) analysis · attack-surface modeling |

---

## 🎤 Speaking & Publications

- **IoT Tech Expo North America 2026** — *Designing Connected Devices with Security Built In* (Panel · San Jose, May 18–19, 2026)
- **SAE WCX Digital Summit 2021** — Abdulazim, A., **Elbahaey, M.**, Mohamed, A., *[Putting Safety of Intended Functionality SOTIF into Practice](https://doi.org/10.4271/2021-01-0196)*. SAE Technical Paper 2021-01-0196. Reference implementation: [Cpyr](https://github.com/moustafa991982/Cpyr).
- **Automotive Security Research Group (ASRG)** — [*AI-based Security & Safety Anomaly Detection*](https://www.youtube.com/watch?v=z3uAQIN0nYw) (2020) · companion talk to the SAE paper above, applying ISO/PAS 21448 (SOTIF) to anomaly detection for unknown attack vectors. Presented as CTO of Autonomous Instruments — see the [real-world vision-anomaly demo](https://www.youtube.com/watch?v=eAX6_KAtLiQ) showing predictive collision alerts on reckless-driving scenarios.
- **NVIDIA GTC 2021** — automotive cybersecurity session

Selected long-form writing on LinkedIn covers ISO 15118 Plug & Charge PKI architecture, Azure Confidential Containers for SDV secure boot, post-quantum TLS migration for SDVs, and supply-chain trust boundaries.

---

## 📜 Certifications & Training

- **PMP** — Project Management Professional
- **ISO/SAE 21434** — Automotive Cybersecurity Engineering
- **Embedded Security Bootcamp** — Barr Group, San Jose
- **QNX OS Security** — BlackBerry QNX
- **QNX Virtualization Fundamentals** — BlackBerry QNX

---

## 📫 Contact

For role discussions, advisory engagements, or speaking inquiries, the fastest path is LinkedIn. Happy to share more detail on any flagship project or my broader portfolio — including ISO 21434, UN R155, ISO 15118 four-chain PKI design, post-quantum migration planning, and AUTOSAR Adaptive Platform camera fusion service design — on request.

https://www.linkedin.com/in/moustafa-e-b-7726aa14/?locale=en
