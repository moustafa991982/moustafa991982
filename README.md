# Moustafa El Bahaey

**Chief Systems Engineer · Automotive Cybersecurity & Embedded Systems**

18 years building secure embedded platforms across OEMs and Tier-1s — Ford, CEER Motors (Saudi EV OEM), Aptiv, Valeo, Arrow. Currently leading systems engineering at [EVRaid](https://www.evraid.com).

I work where automotive functional safety, cybersecurity engineering, and modern confidential-computing trust models intersect — ISO/SAE 21434, UN R155/R156, AUTOSAR Classic & Adaptive, HSM/PKI architecture, QNX RTOS security, SecOC, and TARA methodology.

📍 Silver Spring, Maryland, USA · 🌍 Available for international engagements · 🗣️ Arabic / English / German

---

## 🔐 Featured Projects

### [HSMConfidentialContainer](https://github.com/moustafa991982/HSMConfidentialContainer)
**Confidential-computing HSM daemon for Software-Defined Vehicle secure boot key provisioning.**

A production-style HSM daemon packaged for Azure Confidential Containers, targeting AMD SEV-SNP and Intel TDX confidential VMs on AKS / ACI. Demonstrates a modern alternative to on-premise HSMs for SDV key-provisioning pipelines, with hardware-rooted attestation and tenant isolation in the cloud.

- Multi-arch Docker image published to Azure Container Registry
- Built in Go, designed around remote-attestation flows
- Use case: OEM key-provisioning at end-of-line, fleet-scale credential rotation, cryptographic operations for ISO 15118 Plug & Charge contract certificates

**Why it matters for hiring teams:** Bridges classical automotive HSM patterns (Infineon Aurix HSM, Bosch CycurHSM) with confidential-cloud primitives — a stack very few engineers have hands-on with end to end.

### [QNX-Resource-manager-attacks-with-Secpol-enabled](https://github.com/moustafa991982/QNX-Resource-manager-attacks-with-Secpol-enabled)
**Offensive security research on QNX 8.0 secpol — supply-chain attack scenarios on automotive ECUs.**

Two attack scenarios discovered during ECU security research, demonstrated against QNX 8.0 with secpol policy enforcement enabled:

1. **Trojan resource manager IPC backdoor** — exploiting `transition_rm` and `secpol_transition_type()` flows to inject a malicious resource manager into a hardened policy.
2. **Pre-transition entropy poisoning** — corrupting `/dev/random` consumers before the secpol transition takes effect, undermining downstream cryptographic operations.

Includes the secpol policy authoring, `secpolgenerate` / `secpolpush` workflows, and root-cause analysis (`resmgr_init` typing, errno 314).

**Why it matters for hiring teams:** Concrete demonstration of supply-chain threat modeling on a safety-certified RTOS — directly relevant to UN R155 CSMS evidence, ISO 21434 TARA, and post-SBOM attestation strategies.

### [AI Agent Portfolio](https://github.com/moustafa991982/ai-agent-portfolio)
**Production-deployed AI agents for research, content automation, sales intelligence, and RAG-based document Q&A.**

A curated collection of 17+ AI agents built and deployed on Mind Studio, covering executive workflows from automated research reports and competitive intelligence to a domain-specific *EV Charging Management* RAG chatbot that ties directly into the e-mobility space I work in. Each agent is live and remixable.

- **Research & intelligence:** webpage / YouTube / PDF summarizers, multi-source research report generator with citations, website-change monitor, company intelligence crawler
- **Communication automation:** email thread summarizer & response drafter, personalized cold-outreach generator, LinkedIn post generator with human-review workflow, daily news digest delivery
- **Domain RAG chatbots:** "Ask the Docs" assistants for Mind Studio and for EV charging station documentation

**Why it matters for hiring teams:** Demonstrates I don't just architect security for AI systems — I ship practical AI automation. The combination of safety-critical embedded engineering + applied agentic AI is a rare profile, particularly relevant for SDV trust boundaries and AI-assisted security operations.

---

## 🛠️ Core Expertise

| Domain | |
|---|---|
| **Standards & Regulation** | ISO/SAE 21434 · UN R155 / R156 · ISO 15118-2/-20 · ASPICE for Cybersecurity |
| **Platforms & RTOS** | QNX 8.0 · AUTOSAR Classic & Adaptive · Linux for safety-critical systems |
| **Cryptography & PKI** | HSM integration (Aurix, CycurHSM) · OEM/V2G/eMSP/CPO PKI chains · SecOC · MACsec · post-quantum readiness |
| **Confidential Computing** | AMD SEV-SNP · Intel TDX · Azure Confidential Containers · remote attestation |
| **Applied AI** | Multi-agent workflow design · RAG architectures · safety-critical AI (SOTIF / ISO 21448) · vision-anomaly detection |
| **Methodology** | TARA · CSMS · SBOM (SPDX-2.3) analysis · attack-surface modeling |

---

## 🎤 Speaking & Publications

- **IoT Tech Expo North America 2026** — *Designing Connected Devices with Security Built In* (Panel · San Jose, May 18–19, 2026)
- **Automotive Security Research Group (ASRG)** — [*AI-based Security & Safety Anomaly Detection*](https://www.youtube.com/watch?v=z3uAQIN0nYw) (2020) · applying ISO/PAS 21448 (SOTIF) to anomaly detection for unknown attack vectors. Presented as CTO of Autonomous Instruments, where I led development of *Cpyr* — see the [real-world vision-anomaly demo](https://www.youtube.com/watch?v=eAX6_KAtLiQ) showing predictive collision alerts on reckless-driving scenarios.
- **NVIDIA GTC 2021** — automotive cybersecurity session
- **SAE World Congress** — published research

Selected long-form writing on LinkedIn covers ISO 15118 Plug & Charge PKI architecture, Azure Confidential Containers for SDV secure boot, and supply-chain trust boundaries for SDVs.

---

## 📜 Certifications & Training

- **PMP** — Project Management Professional
- **ISO/SAE 21434** — Automotive Cybersecurity Engineering
- **Embedded Security Bootcamp** — Barr Group, San Jose
- **QNX OS Security** — BlackBerry QNX
- **QNX Virtualization Fundamentals** — BlackBerry QNX

---

## 📫 Contact

For role discussions, advisory engagements, or speaking inquiries, the fastest path is LinkedIn. Happy to share more detail on any flagship project or my broader portfolio — including ISO 21434, UN R155, ISO 15118 four-chain PKI design, and AUTOSAR Adaptive Platform camera fusion service design — on request.

https://www.linkedin.com/in/moustafa-e-b-7726aa14/?locale=en
