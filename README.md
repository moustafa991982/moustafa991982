# Moustafa El Bahaey

**Chief Systems Engineer · Automotive Cybersecurity & Embedded Systems**

18 years building secure embedded platforms across OEMs and Tier-1s — Ford, CEER Motors (Saudi EV OEM), Aptiv, Valeo, Arrow. Currently leading systems engineering at [EVRaid](https://www.evraid.com).

**What I do:** take security research and modern cryptography — post-quantum, confidential computing, hardware roots of trust — and make it deployable inside regulated automotive programs: ISO/SAE 21434, UN R155/R156, AUTOSAR Classic & Adaptive, QNX RTOS security, HSM/PKI architecture, SecOC, TARA, and the supplier-evidence machinery that certification actually demands. Research teams invent; OEM programs certify. I work the gap in between.

📍 Cairo, Egypt · 🌍 Available for international engagements (US · EU · GCC) · 🗣️ Arabic / English / German

---

## 🔐 Featured Projects

### [pqc-sdv-cvm](https://github.com/moustafa991982/pqc-sdv-cvm)

**What post-quantum TLS actually costs a Software-Defined Vehicle backend — measured end-to-end on Azure SEV-SNP, layer by layer.**

The performance behavior of hybrid and PQ TLS 1.3 is well established in the literature — KEMTLS and the measurement work of Schwabe, Celi, and Wiggers, plus the large-scale Cloudflare/Chrome hybrid deployments. This project does not re-claim those results; it **characterizes them under automotive deployment constraints** (virtual VCU → public-internet WAN → confidential VM) and surfaces operational findings the protocol literature doesn't cover:

- **Key security finding — silent attestation degradation in Azure Secure Key Release:** on Ubuntu 22.04 CVM kernels where `/dev/sev-guest` is not exposed, the runtime falls back from hardware-rooted MAA attestation to managed-identity RBAC **without failing closed**. The SKR architecture is preserved on paper while the trust anchor quietly weakens — directly relevant to anyone binding PQC key material to confidential VMs.
- **TLS 1.3 with hybrid X25519MLKEM768** terminated by nginx + OpenSSL 3.5 inside an AMD SEV-SNP confidential VM (`Standard_DC2as_v5`), keys held in Azure Key Vault Premium under attestation-gated Secure Key Release
- **Three certificate chains compared for the V2G/PnC PKI roadmap:** classical (ECDSA), mixed (ML-DSA root + sub-CA, ECDSA leaf — the realistic 2027–2030 shape), and full ML-DSA
- **Automotive-relevant measurements:** hybrid KEM +2.4 KB per handshake; PQ trust anchor +18 KB and 2.6× TCP segments on the wire; ML-DSA chains exceed Key Vault's 25 KB secret limit (documented workaround via Blob-served chains) — inputs for ISO 15118-20 certificate sizing, V2G Root rollover planning, and CNSA 2.0 migration timelines
- **Honest limitations catalogue** — 12 production-blocking issues encountered and worked around, written up so program teams don't rediscover them

### [HSMConfidentialContainer](https://github.com/moustafa991982/HSMConfidentialContainer)

**Confidential-computing HSM daemon for SDV secure boot key provisioning.**

A production-style HSM daemon in Go, packaged for Azure Confidential Containers on AMD SEV-SNP and Intel TDX (AKS / ACI). Demonstrates a cloud alternative to on-premise HSMs for OEM key-provisioning pipelines — end-of-line provisioning, fleet-scale credential rotation, and ISO 15118 Plug & Charge contract-certificate operations — built around remote-attestation flows with multi-arch images in Azure Container Registry.

### [QNX-Resource-manager-attacks-with-Secpol-enabled](https://github.com/moustafa991982/QNX-Resource-manager-attacks-with-Secpol-enabled)

**Offensive research on QNX 8.0 secpol — two supply-chain attack scenarios on automotive ECUs.**

1. **Trojan resource manager IPC backdoor** — abusing `transition_rm` / `secpol_transition_type()` flows to plant a malicious resource manager inside a hardened policy.
2. **Pre-transition entropy poisoning** — corrupting `/dev/random` consumers before the secpol transition takes effect, undermining downstream cryptographic operations.

Includes full secpol policy authoring, `secpolgenerate` / `secpolpush` workflows, root-cause analysis (`resmgr_init` typing, errno 314), and a video demonstration.

### [Cpyr](https://github.com/moustafa991982/Cpyr)

**Deep anomaly detection for in-vehicle networks — reference implementation for SAE 2021-01-0196 (SOTIF in practice).**

Semi-supervised deep learning for cyber-physical anomaly detection on automotive networks:

1. **Fuzz-attack detection on automotive Ethernet** — reconstruction autoencoders trained on normal traffic only; hex-to-binary preprocessing lets a **1.2 KB convolutional encoder match a 223 MB transformer** on separation quality — small enough for ECU deployment.
2. **LKA contextual anomaly detection (SOTIF case study)** — predictive context models catching single-frame contextual anomalies (e.g., LKA disabled during an uninitiated lane switch) with zero-batch-lag triggering.

Companion to SAE WCX 2021 *Putting Safety of Intended Functionality SOTIF into Practice* and the [ASRG talk](https://www.youtube.com/watch?v=z3uAQIN0nYw).

### [zephyrbank-llm-redteam](https://github.com/moustafa991982/zephyrbank-llm-redteam)

**Red-teaming a production-style LLM banking assistant — adversarial testing across the OWASP LLM risk categories.**

A hands-on security assessment of ZephyrBank, a retrieval-augmented chatbot for a fictional business bank, applying both manual adversarial prompting and Giskard's automated LLM scan. The same discipline I apply to automotive ECUs — think like the attacker, then document the failure mode so the team can fix it — carried into the LLM layer.

- **Threat categories exercised:** prompt injection and instruction override, sensitive-information / system-prompt disclosure, RAG data leakage, bias and stereotyped output, hallucination under adversarial framing, and denial-of-service style prompt abuse
- **Method:** manual probe design plus automated scanning, with each finding written up as an attack narrative → root cause → mitigation, mapped to the OWASP Top 10 for LLM Applications
- **Why it's here:** the bridge from 18 years of embedded/automotive security into AI security — the same TARA-style adversarial mindset applied to LLM-integrated systems, with a recorded walkthrough demonstrating the exploits end-to-end

Part of a broader AI-security focus that includes LLM threat modeling and adversarial ML — the direction I'm actively building toward alongside the automotive work.

### [AI Agent Portfolio](https://github.com/moustafa991982/ai-agent-portfolio)

**17+ production-deployed AI agents** on Mind Studio — research report generation with citations, competitive intelligence, communication automation, and domain RAG chatbots including an *EV Charging Management* documentation assistant tied to the e-mobility work above.

---

## 🛠️ Core Expertise

| Domain | |
| --- | --- |
| **Standards & Regulation** | ISO/SAE 21434 · UN R155 / R156 · ISO 15118-2/-20 · ASPICE for Cybersecurity · NSA CNSA 2.0 |
| **Platforms & RTOS** | QNX 8.0 · AUTOSAR Classic & Adaptive · Linux for safety-critical systems |
| **Cryptography & PKI** | HSM integration (Aurix, CycurHSM) · OEM / V2G / eMSP / CPO PKI chains · SecOC · MACsec · PQC deployment (ML-KEM, ML-DSA, hybrid TLS 1.3) |
| **Confidential Computing** | AMD SEV-SNP · Intel TDX · Azure Confidential VMs & Containers · Microsoft Azure Attestation · Secure Key Release |
| **Applied AI & AI Security** | LLM red-teaming · multi-agent workflow design · RAG architectures · safety-critical AI (SOTIF / ISO 21448) · vision-anomaly detection |
| **Methodology** | TARA · CSMS · SBOM (SPDX-2.3) analysis · attack-surface modeling · supplier deliverable assessment |

---

## 🎤 Speaking & Publications

- **IoT Tech Expo North America 2026** — *Designing Connected Devices with Security Built In* (Panel · San Jose, May 18–19, 2026)
- **SAE WCX Digital Summit 2021** — Abdulazim, A., **Elbahaey, M.**, Mohamed, A., *[Putting Safety of Intended Functionality SOTIF into Practice](https://doi.org/10.4271/2021-01-0196)*. SAE Technical Paper 2021-01-0196. Reference implementation: [Cpyr](https://github.com/moustafa991982/Cpyr).
- **Automotive Security Research Group (ASRG)** — [*AI-based Security & Safety Anomaly Detection*](https://www.youtube.com/watch?v=z3uAQIN0nYw) (2020) · applying ISO/PAS 21448 (SOTIF) to anomaly detection for unknown attack vectors, presented as CTO of Autonomous Instruments · [real-world vision-anomaly demo](https://www.youtube.com/watch?v=eAX6_KAtLiQ)
- **NVIDIA GTC 2021** — automotive cybersecurity session

Selected long-form writing on LinkedIn: ISO 15118 Plug & Charge PKI architecture, Azure Confidential Containers for SDV secure boot, post-quantum TLS migration for SDVs, supply-chain trust boundaries.

---

## 📜 Certifications & Training

- **PMP** — Project Management Professional
- **ISO/SAE 21434** — Automotive Cybersecurity Engineering
- **Embedded Security Bootcamp** — Barr Group, San Jose
- **QNX OS Security** — BlackBerry QNX
- **QNX Virtualization Fundamentals** — BlackBerry QNX

---

## 📫 Contact

For role discussions, advisory engagements, or speaking inquiries, the fastest path is LinkedIn. Happy to go deeper on any flagship project — ISO 21434 / UN R155 program work, ISO 15118 four-chain PKI design, post-quantum migration planning, or AUTOSAR Adaptive camera-fusion service design — on request.

<https://www.linkedin.com/in/moustafa-e-b-7726aa14/?locale=en>
