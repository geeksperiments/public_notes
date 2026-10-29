# ContainerDays & AI Context Singapore 2026 · Executive Conference Summary

> **Date**: Tuesday, October 27 – Wednesday, October 28, 2026  
> **Venue**: Suntec Singapore Convention & Exhibition Centre (1 Raffles Boulevard, Singapore 039593)  
> **Event URL**: [ContainerDays Singapore 2026](https://www.containerdays.io/containerdays-singapore-2026/) • [Full Agenda](https://www.containerdays.io/containerdays-singapore-2026/agenda/)  
> **Organizers**: Dockland Media Group, Supported by Singapore Exhibition & Convention Bureau (SECB)  
> **Keynote Speakers**: Kelsey Hightower, Saiyam Pathak (vCluster), Carl Ross (OpenAI), Jerry Chen (DaoCloud / d.run), Yashod Perera (WSO2)  
> **Public Vault Connections**: [AI-Generated Code == Code You Can Trust (AISG & Sonar)](./AI-Generated%20Code%20==%20Code%20You%20Can%20Trust%20-%20AISG%20&%20Sonar%20at%20EDB.md) • [Shipping Reliable AI Agents (Langfuse & ClickHouse)](./Shipping%20Reliable%20AI%20Agents%20-%20Building%20with%20Langfuse%20and%20ClickHouse%20(Max%20Deichmann).md) • [Build Agents with Google Agent CLI](./Build%20Agents%20with%20Google%20Agent%20CLI.md)

---

## ⚡ Executive Summary: The 5 Mega-Themes of ContainerDays 2026

ContainerDays & AI Context Singapore 2026 marked a decisive turning point in cloud-native computing: **the transition from "AI as a feature" to "AI as the primary consumer and operator of infrastructure."** Across two intensive days, engineering leaders from OpenAI, Kong, DaoCloud, SUSE, WSO2, and Google converged on five architectural realities:

1. 🛡️ **From Model Capabilities to System Boundaries**:
   Autonomous coding agents (Claude Code, Pi, OpenHands) cannot be trusted with raw credentials or unfettered network access. The industry is standardizing on **ephemeral Kubernetes Sandboxes (`agents.x-k8s.io/v1beta1`)**, Linux Landlock LSM, and microVMs (gVisor, QEMU) to hermetically seal execution environments.
2. 🤖 **The Death of ClickOps & The Machine User**:
   Internal Developer Portals (IDPs) built for *"a human with a browser"* are obsolete when autonomous agents deploy code at 3 AM. Platforms must expose **Model Context Protocol (MCP)** APIs with CEL-rendered 12-line abstractions rather than raw 400-line Kubernetes manifests.
3. 🏭 **The Token Factory Paradigm**:
   Enterprise accounting has flipped from *"requests per GPU"* to **blended cost per million tokens ($\$/\text{Mtok}$)**. Operating 229B to 2.8T parameter models demands Prefill/Decode (PD) disaggregation, LeaderWorkerSet (LWS) atomic groups, and 4-tier KV cache inventory pyramids (ContextStore) that treat KV blocks as reusable factory inventory.
4. 🚦 **Infrastructure-Level Agent Governance**:
   Unmanaged multi-agent meshes collapse under runaway token bills and privilege escalation. Centralized AI Gateways (Kong AI Gateway, Loge, Knoway) enforce token-level rate limiting ($TPM$), tool-level RBAC, and prompt injection guards at the network edge.
5. 🔁 **Harness Engineering Over Vibe Coding**:
   When inference token costs approach zero, code becomes cheap and disposable. The only non-regrettable engineering investments are **hermetic test harnesses**, **trace-derived evaluation graphs**, and **radically fast CI loops**.

---

## 📸 Venue & Kickoff

![CDS Theatre Kickoff](Attachments/cds26-theatre-stage.jpg)

> **CDS Theatre Kickoff**: Opening keynote stage at Suntec Singapore Convention Centre.

---

## 🧭 Attended Sessions & Technical Itinerary

### Day 1: Tuesday, October 27, 2026 (10 Sessions)

| Time | Room / Track | Session Title & Speaker | Core Technical Focus | Dedicated Note |
| :--- | :--- | :--- | :--- | :--- |
| **09:30 – 10:15** | CDS Theatre | **Confessions of a Portal Assistant**<br>— *Yashod Perera (WSO2)* | Moving from portal RAG chatbots to machine-readable MCP platform APIs. | [Read Note](./Confessions%20of%20a%20Portal%20Assistant%20%28Yashod%20Perera%29.md) |
| **10:15 – 10:50** | AIC Theatre | **Securing AI Coding Agents with K8s Sandboxes**<br>— *Ryan Djurovich (Podplane)* | Kubernetes `Sandbox` CRD, gVisor isolation, and Landlock LSM supervision. | [Read Note](./Securing%20AI%20Coding%20Agents%20with%20Kubernetes%20Sandboxes%20%28Ryan%20Djurovich%29.md) |
| **11:20 – 12:20** | Workshop | **Taming Agent Sprawl: Scaling Evals**<br>— *Timothy Lin (Resaro)* | Trace-derived topology graphs and automated synthetic edge-case generation. | [Read Note](./Taming%20Agent%20Sprawl%20-%20How%20We%20Scale%20Evals%20to%20Keep%20Up%20with%20Agents%20%28Timothy%20Lin%29.md) |
| **12:25 – 12:40** | Synergies | **Operating an Internal LLM Gateway**<br>— *Zhong Liang Ong & Yek Khan (Loge)* | Tailscale auth, credential decoupling, and why cross-model fallback breaks agents. | [Read Note](./Lessons%20from%20Operating%20an%20Internal%20LLM%20Gateway%20for%20Production%20Agentic%20Applications%20%28Zhong%20Liang%20Ong%20%26%20Yek%20Khan%29.md) |
| **12:50 – 13:25** | AIC Theatre | **Operating Agentic Software Factories**<br>— *Carl Ross (OpenAI)* | Asymptotic token economics, WASM actor swarms, and Single Problem Optimization. | [Read Note](./When%20Tokens%20Stop%20Being%20the%20Bottleneck%20-%20Operating%20Agentic%20Software%20Factories%20%28Carl%20Ross%29.md) |
| **14:25 – 14:55** | MainStage | **Fireside Chat with Kelsey Hightower**<br>— *Kelsey Hightower & Geet Bhanawat* | Fundamentals over hype, 1-5-60 telecom triage, and 5G network slicing. | [Read Note](./Fireside%20Chat%20with%20Kelsey%20Hightower%20%26%20Geet%20Bhanawat.md) |
| **15:05 – 15:40** | MainStage | **Will Everyone Build an AI Factory?**<br>— *Saiyam Pathak (vCluster Labs)* | Modular NVIDIA DSX PODs, HAMi GPU slicing, and vCluster multi-tenancy. | [Read Note](./Will%20Everyone%20Build%20an%20AI%20Factory%3F%20%28Saiyam%20Pathak%29.md) |
| **15:40 – 16:05** | SUSE Booth | **Enterprise Sovereign AI with SUSE AI Factory**<br>— *SUSE SEA Solutions Team* | SLES for NVIDIA live patching, Rancher Prime, and OpenShell agent sandboxing. | [Read Note](./Enterprise%20Sovereign%20AI%20-%20Building%20with%20SUSE%20AI%20Factory.md) |
| **16:10 – 16:45** | CDS Theatre | **Start Shipping AI Operable Products**<br>— *Khang Toh (fdeploy)* | Dual-user surfaces, the 7 operability primitives, and 8-minute SlackOps remediation. | [Read Note](./Stop%20Shipping%20Features%20with%20AI.%20Start%20Shipping%20AI%20Operable%20Products%20%28Khang%20Toh%29.md) |
| **16:55 – 17:30** | Synergies | **Governing the Agentic Stack on Kubernetes**<br>— *Robin Cher (Kong)* | 1 Gateway, 3 Profiles (LLM, MCP, A2A), token budgets, and distributed tracing. | [Read Note](./Governing%20the%20Agentic%20Stack%20on%20Kubernetes%20-%20MCP%2C%20A2A%2C%20and%20LLM%20Traffic%20%28Robin%20Cher%29.md) |

---

### Day 2: Wednesday, October 28, 2026 (6 Sessions & Workshops)

| Time | Room / Track | Session Title & Speaker | Core Technical Focus | Dedicated Note |
| :--- | :--- | :--- | :--- | :--- |
| **09:15 – 10:30** | Workshop | **Serve Your First LLM, Then Watch It Break**<br>— *Mumshad Mannambeth (KodeKloud)* | VRAM saturation, prefill vs decode, and llm-d KV cache affinity routing. | [Read Note](./Serve%20Your%20First%20LLM%2C%20Then%20Watch%20It%20Break%20at%20Scale%20%28Mumshad%20Mannambeth%29.md) |
| **11:00 – 11:30** | SUSE Booth | **Accelerating Cloud Delivery with SUSE BCI**<br>— *SUSE Showcase* | 24-hour upstream patch SLA, Sigstore provenance, and enterprise hardened images. | [Read Note](./Accelerating%20Cloud-Native%20Delivery%20with%20SUSE%20Application%20Collection.md) |
| **11:00 – 12:00** | Workshop | **Build the AI Context Layer for EPD**<br>— *Yethoven Tukimin (Notion)* | Relational knowledge graphs and Model Context Protocol (MCP) for IDE agents. | [Read Note](./Build%20the%20AI%20Context%20Layer%20for%20Your%20EPD%20Team%20%28Yethoven%20Tukimin%29.md) |
| **11:45 – 13:00** | Workshop | **Build Your Own Agent Platform on K8s**<br>— *Ryan Djurovich (Podplane)* | Hands-on agentic PaaS, Pi coding agent, Landlock LSM, and SPIFFE mTLS. | [Read Note](./Build%20Your%20Own%20AI%20Coding%20Agent%20Platform%20on%20Kubernetes%20%28Ryan%20Djurovich%29.md) |
| **13:55 – 14:30** | CDS Theatre | **Your Next Platform User Isn't Human**<br>— *Yashod Perera (OpenChoreo)* | Agent-native developer platforms, CEL-rendered abstractions, and SRE agents. | [Read Note](./Your%20Next%20Platform%20User%20Isn%27t%20Human%20-%20Building%20an%20AI-Native%20Developer%20Platform%20%28Yashod%20Perera%29.md) |
| **15:25 – 16:00** | CDS Theatre | **Building a High-Performance Token Factory**<br>— *Jerry Chen (DaoCloud / d.run)* | Heterogeneous compute pooling, ContextStore 4-tier KV cache, and MatrixHub. | [Read Note](./Building%20a%20High-Performance%20Token%20Factory%20%28Jerry%20Chen%29.md) |

---

## 📝 Day 1 Highlights & Key Takeaways

### 1. [Confessions of a Portal Assistant (Yashod Perera)](./Confessions%20of%20a%20Portal%20Assistant%20%28Yashod%20Perera%29.md)
- **The Problem**: Web portals built for humans fail when consumed by autonomous coding agents. Agents either scrape UI, generate invalid YAML, or bypass the portal to execute raw `kubectl apply`.
- **The Solution**: Treat MCP as the primary interface. Expose scoped domain abstractions (e.g. 12-line CEL `Component` specs) so agents cannot hallucinate unapproved cluster resources.
- **Key Artifacts**: [Full Architecture & Failure Case Studies](./Confessions%20of%20a%20Portal%20Assistant%20%28Yashod%20Perera%29.md).

![Yashod Perera Portal Assistant](Attachments/cds26-yashod-perera-intro.jpg)

---

### 2. [Securing AI Coding Agents with Kubernetes Sandboxes (Ryan Djurovich)](./Securing%20AI%20Coding%20Agents%20with%20Kubernetes%20Sandboxes%20%28Ryan%20Djurovich%29.md)
- **The Problem**: Traditional StatefulSets fail for ephemeral agent runs. Agents require isolated kernels, rapid teardown, and strictly segregated API credentials.
- **The Solution**: The upstream Kubernetes `Sandbox` CRD (`agents.x-k8s.io/v1beta1`) paired with `nono` (Linux Landlock LSM supervisor) and SPIFFE mTLS workload identities. Provider API keys never enter the sandbox container.
- **Key Artifacts**: [Manifests & gVisor Sandbox Architecture](./Securing%20AI%20Coding%20Agents%20with%20Kubernetes%20Sandboxes%20%28Ryan%20Djurovich%29.md).

![Ryan Djurovich Sandbox CRD](Attachments/cds26-ryan-djurovich-k8s-agent-sandbox-crd-gvisor-vs-statefulset.jpg)

---

### 3. [Taming Agent Sprawl: Scaling Evals (Timothy Lin)](./Taming%20Agent%20Sprawl%20-%20How%20We%20Scale%20Evals%20to%20Keep%20Up%20with%20Agents%20%28Timothy%20Lin%29.md)
- **The Problem**: Frameworks make multi-agent prototypes easy to build, but combinatorial decision branches make manual evaluation impossible.
- **The Solution**: Derive structural topology graphs directly from runtime OpenTelemetry traces. Synthesize adversarial test cases targeted at fragile graph junctions to establish automated CI/CD release gates.
- **Key Artifacts**: [Trace Topology Graph & Quality Gate Criteria](./Taming%20Agent%20Sprawl%20-%20How%20We%20Scale%20Evals%20to%20Keep%20Up%20with%20Agents%20%28Timothy%20Lin%29.md).

![Timothy Lin Evals](Attachments/cds26-timothy-lin-intro.jpg)

---

### 4. [Operating an Internal LLM Gateway (Zhong Liang Ong & Yek Khan)](./Lessons%20from%20Operating%20an%20Internal%20LLM%20Gateway%20for%20Production%20Agentic%20Applications%20%28Zhong%20Liang%20Ong%20%26%20Yek%20Khan%29.md)
- **The Problem**: Decentralized API key distribution across engineering teams leads to credential leaks, zero cost visibility, and unmanaged model drift.
- **The Solution**: **Loge**, an internal Kubernetes LLM gateway with Tailscale ACLs, explicit vs. family-alias routing, and strict retry disciplines (same-model retry allowed; cross-model fallback blocked to avoid breaking JSON schemas).
- **Key Artifacts**: [Routing Tiers & Gateway Architecture](./Lessons%20from%20Operating%20an%20Internal%20LLM%20Gateway%20for%20Production%20Agentic%20Applications%20%28Zhong%20Liang%20Ong%20%26%20Yek%20Khan%29.md).

![Loge Internal Gateway Architecture](Attachments/cds26-loge-shared-model-gateway-run-as-infrastructure.jpg)

---

### 5. [Operating Agentic Software Factories (Carl Ross)](./When%20Tokens%20Stop%20Being%20the%20Bottleneck%20-%20Operating%20Agentic%20Software%20Factories%20%28Carl%20Ross%29.md)
- **The Problem**: As inference token costs trend toward zero, writing code is no longer the bottleneck. The only durable investments are verification harnesses.
- **The Solution**: WASM actor swarms distributed via OCI registries (Zot + ORAS), asynchronous NATS mailboxes, and Single Problem Optimization (SPO) workers landing code directly on trunk via deterministic Grader actors.
- **Key Artifacts**: [Software Factory Blueprint & 14 Embedded Slides](./When%20Tokens%20Stop%20Being%20the%20Bottleneck%20-%20Operating%20Agentic%20Software%20Factories%20%28Carl%20Ross%29.md).

![Carl Ross Software Factory Blueprint](Attachments/cds26-carl-ross-software-factories-title-slide.jpg)

---

### 6. [Fireside Chat with Kelsey Hightower & Geet Bhanawat](./Fireside%20Chat%20with%20Kelsey%20Hightower%20%26%20Geet%20Bhanawat.md)
- **Core Insights**: *"AI is just another workload."* Technology does not fix broken team architectures or messy data; it simply accelerates what is already there. Focus on Linux and networking fundamentals.
- **Singtel 1-5-60 Benchmark**: 1 min fault detection $	o$ 5 min agentic diagnosis $	o$ 60 min service restoration across nationwide telecom networks.
- **Key Artifacts**: [Full Discussion Notes & Onstage Photos](./Fireside%20Chat%20with%20Kelsey%20Hightower%20%26%20Geet%20Bhanawat.md).

![Kelsey Hightower Onstage](Attachments/cds26-fireside-chat-panel-james-kok-kelsey-hightower-geet-bhanawat-stage.jpg)

---

### 7. [Will Everyone Build an AI Factory? (Saiyam Pathak)](./Will%20Everyone%20Build%20an%20AI%20Factory%3F%20%28Saiyam%20Pathak%29.md)
- **The Problem**: Operating enterprise AI clusters leads to severe GPU under-utilization (5–30%) and multi-tenant permission conflicts.
- **The Solution**: Modular containerized data centers (NVIDIA DSX POD) deployed in 14 days, coupled with HAMi vGPU slicing and **vCluster** virtual control planes granting AI engineers `cluster-admin` freedom without host cluster instability.
- **Key Artifacts**: [GPU Slicing YAML Specs & vCluster Architecture](./Will%20Everyone%20Build%20an%20AI%20Factory%3F%20%28Saiyam%20Pathak%29.md).

![Saiyam Pathak AI Factory](Attachments/cds26-saiyam-pathak-will-everyone-build-an-ai-factory.jpg)

---

### 8. [Enterprise Sovereign AI with SUSE AI Factory](./Enterprise%20Sovereign%20AI%20-%20Building%20with%20SUSE%20AI%20Factory.md)
- **The Problem**: National data residency and IP protection require turnkey on-prem infrastructure rather than public cloud APIs.
- **The Solution**: SLES for NVIDIA (kernel Live Patching for zero-downtime training), Rancher Prime multi-cluster management, and NVIDIA OpenShell runtime sandboxing with NeuVector L7 security.
- **Key Artifacts**: [SUSE AI Factory Operator & Blueprint Architecture](./Enterprise%20Sovereign%20AI%20-%20Building%20with%20SUSE%20AI%20Factory.md).

![SUSE Sovereign AI Factory](Attachments/cds26-suse-sovereign-ai-demands-diy-pitfall-vs-ai-factory.jpg)

---

### 9. [Start Shipping AI Operable Products (Khang Toh)](./Stop%20Shipping%20Features%20with%20AI.%20Start%20Shipping%20AI%20Operable%20Products%20%28Khang%20Toh%29.md)
- **The Problem**: AI accelerates feature synthesis, but "LGTM Engineering" (approving unread 1,000-line agent PRs) spikes production change failure rates.
- **The Solution**: Build for dual users (Human SREs + Autonomous Agents) using the 7 Primitives of Operability (Outcome Intent, Journey Context, Recovery Paths, Safe Actions).
- **Key Artifacts**: [5 Pillars Architecture & 8-Minute Autonomous Remediation Loop](./Stop%20Shipping%20Features%20with%20AI.%20Start%20Shipping%20AI%20Operable%20Products%20%28Khang%20Toh%29.md).

![Khang Toh Operable Products](Attachments/cds26-khang-toh-stop-shipping-features-with-ai-operable-products-intro.jpg)

---

### 10. [Governing the Agentic Stack on Kubernetes (Robin Cher)](./Governing%20the%20Agentic%20Stack%20on%20Kubernetes%20-%20MCP%2C%20A2A%2C%20and%20LLM%20Traffic%20%28Robin%20Cher%29.md)
- **The Problem**: Multi-agent point-to-point sprawl causes unmanaged token costs, prompt injections, and unauthenticated MCP tool calls.
- **The Solution**: Kong AI Gateway with 3 declarative Kubernetes CRD profiles: LLM Profile (budgets & prompt guard), MCP Profile (tool RBAC), and A2A Profile (agent identity & rate limits). Data plane traffic stays strictly local.
- **Key Artifacts**: [Reference Architecture & Jaeger Distributed Tracing](./Governing%20the%20Agentic%20Stack%20on%20Kubernetes%20-%20MCP%2C%20A2A%2C%20and%20LLM%20Traffic%20%28Robin%20Cher%29.md).

![Kong AI Gateway Reference Architecture](Attachments/cds26-robin-cher-reference-architecture-one-gateway-three-profiles.jpg)

---

## 📝 Day 2 Highlights & Key Takeaways

### 11. [Serve Your First LLM, Then Watch It Break (Mumshad Mannambeth)](./Serve%20Your%20First%20LLM%2C%20Then%20Watch%20It%20Break%20at%20Scale%20%28Mumshad%20Mannambeth%29.md)
- **The Problem**: 8B models saturate 16GB GPUs on weight loading alone. Stateless multi-turn chat resends full conversation history, while naive Kubernetes `Service` round-robin routing causes 100% KV cache misses.
- **The Solution**: Disaggregate prefill from decode and deploy intelligent KV cache affinity routers (**llm-d**) to pin sessions and reuse cached prompt prefixes.
- **Key Artifacts**: [PagedAttention, Prefill vs Decode, & llm-d Architecture](./Serve%20Your%20First%20LLM%2C%20Then%20Watch%20It%20Break%20at%20Scale%20%28Mumshad%20Mannambeth%29.md).

![Mumshad Mannambeth LLM Serving](Attachments/cds26-mumshad-on-stage-title-slide.jpg)

---

### 12. [Accelerating Cloud Delivery with SUSE BCI](./Accelerating%20Cloud-Native%20Delivery%20with%20SUSE%20Application%20Collection.md)
- **The Problem**: Over 80% of open-source container images carry unpatched critical CVEs; manual enterprise audits stall developer velocity.
- **The Solution**: Pre-audited enterprise container images rebuilt within 24 hours of upstream CVE disclosures, signed with Sigstore/Cosign and verified via Rancher Prime.
- **Key Artifacts**: [Supply Chain Security & 4-Stage Delivery Workflow](./Accelerating%20Cloud-Native%20Delivery%20with%20SUSE%20Application%20Collection.md).

![SUSE BCI Application Collection](Attachments/cds26-suse-application-collection-title-booth.jpg)

---

### 13. [Build the AI Context Layer for EPD (Yethoven Tukimin)](./Build%20the%20AI%20Context%20Layer%20for%20Your%20EPD%20Team%20%28Yethoven%20Tukimin%29.md)
- **The Problem**: Disconnected silos across Product (PRDs), Design (Figma), and Engineering (GitHub) lead to coding agent hallucinations.
- **The Solution**: Centralize organizational context in Notion relational schemas and expose them to Cursor/Claude Code via Model Context Protocol (`@modelcontextprotocol/server-notion`).
- **Key Artifacts**: [EPD Relational Schema & MCP Integration Workflow](./Build%20the%20AI%20Context%20Layer%20for%20Your%20EPD%20Team%20%28Yethoven%20Tukimin%29.md).

---

### 14. [Build Your Own Agent Platform on K8s (Ryan Djurovich)](./Build%20Your%20Own%20AI%20Coding%20Agent%20Platform%20on%20Kubernetes%20%28Ryan%20Djurovich%29.md)
- **The Problem**: Coding agents require dedicated, disposable developer environments that cannot compromise production Kubernetes clusters.
- **The Solution**: Podplane lightweight QEMU microVMs running Pi coding agents inside Kubernetes `Sandbox` CRDs, supervised by Linux Landlock LSM with SPIFFE mTLS authentication.
- **Key Artifacts**: [5-Part Hands-on Lab & Manifest Walkthrough](./Build%20Your%20Own%20AI%20Coding%20Agent%20Platform%20on%20Kubernetes%20%28Ryan%20Djurovich%29.md).

![Ryan Djurovich Workshop QR](Attachments/cds26-ryan-djurovich-workshop-qr-ryan0x44-singapore2026.jpg)

---

### 15. [Your Next Platform User Isn't Human (Yashod Perera)](./Your%20Next%20Platform%20User%20Isn%27t%20Human%20-%20Building%20an%20AI-Native%20Developer%20Platform%20%28Yashod%20Perera%29.md)
- **The Core Inversion**: Shift from *"building an assistant for the developer portal"* to **"building a platform an autonomous agent can use."**
- **The Solution**: OpenChoreo architecture exposing Control Plane MCP (94 scoped domain tools) and Observability MCP (condition summaries) with CEL-rendered 12-line Component specs.
- **Key Rule**: *"An SRE agent is only as honest as your topology."* Governance gaps become agent hallucinations.
- **Key Artifacts**: [Platform Topology, CEL Schemas, & Autonomous RCA Loops](./Your%20Next%20Platform%20User%20Isn%27t%20Human%20-%20Building%20an%20AI-Native%20Developer%20Platform%20%28Yashod%20Perera%29.md).

![Yashod Perera AI Native Platform](Attachments/cds26-yashod-perera-your-next-platform-user-isnt-human-title.jpg)

---

### 16. [Building a High-Performance Token Factory (Jerry Chen)](./Building%20a%20High-Performance%20Token%20Factory%20%28Jerry%20Chen%29.md)
- **The Defining Thesis**: *"You don't deploy a model. You operate a factory."* Accounting flips to **blended cost per million tokens ($\$/\text{Mtok}$)**.
- **The Architecture**: Heterogeneous compute pooling with HAMi/DRA/Kueue TAS boosts GPU utilization from **30% to 80%+** across 10+ accelerator families (~70,000 GPUs on `d.run`).
- **Distributed Serving & Storage**: PD Disaggregation managed as atomic LeaderWorkerSet (LWS) groups; 4-tier KV cache inventory via **ContextStore** delivers up to **24x token output**; **MatrixHub** hydrates 1.6TB models at **25.8 GB/s** wire-speed.
- **Key Artifacts**: [6 Architectural Layers, Benchmark Fleet Results, & Six Production Patterns](./Building%20a%20High-Performance%20Token%20Factory%20%28Jerry%20Chen%29.md).

![Jerry Chen Token Factory](Attachments/cds26-jerry-chen-building-a-high-performance-token-factory-title.jpg)

---

## 🎯 Production Patterns to Apply on Monday

1. **Stop Deploying Raw Containers for Agents**: Transition coding agents from standard pods to ephemeral Kubernetes `Sandbox` CRDs with Linux Landlock LSM filesystem isolation.
2. **Never Pass Raw Upstream API Keys to Agents**: Intercept and enrich inference and Git traffic at external gateways (Kong AI Gateway, Loge) using workload mTLS (SPIFFE).
3. **Disaggregate Prefill from Decode**: Separate compute-heavy prompt ingestion from memory-bandwidth-bound token generation to slash TTFT and scale independently.
4. **Treat KV Caches as Managed Factory Inventory**: Implement multi-tier KV cache offloading (GPU HBM $	o$ Host DRAM $	o$ Local NVMe $	o$ Shared Storage) via tools like ContextStore to avoid expensive prompt recomputation.
5. **Give Autonomous Agents Fewer Words**: Replace raw 400-line Kubernetes YAML with CEL-rendered, schema-restricted domain components exposed over MCP.
6. **Alert on P99 Latency, Never Averages**: Multi-tenant GPU serving suffers from extreme noisy-neighbor starvation under long contexts; closed-loop SLAs must trigger on tail latency.

---
