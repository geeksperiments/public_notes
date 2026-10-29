# Will Everyone Build an AI Factory? (Saiyam Pathak)

> **Speaker**: Saiyam Pathak (Head of Developer Relations, vCluster Labs / Loft Labs · CNCF Ambassador · Founder, Kubesimplify)  
> **Event**: [[ContainerDays Singapore 2026]] (ContainerDays & AI Context Track)  
> **Date & Time**: Tuesday, October 27, 2026 · 3:05 PM – 3:40 PM SGT  
> **Stage**: MainStage  
> **Subtitle / Hook**: *"Jensen just shipped one in a container."*  
> **Core Topics**: AI Factories vs Data Centers · NVIDIA DGX Containerized Pods · GPU Orchestration on Kubernetes · Multi-Tenancy with vCluster · GPU Sharing & Virtualization (HAMi & DRA)  
> **Vault Connections**: 
> - [[ContainerDays Singapore 2026]]
> - [[When Tokens Stop Being the Bottleneck - Operating Agentic Software Factories (Carl Ross)]]
> - [[Fireside Chat with Kelsey Hightower & Geet Bhanawat]]
> - [[Lessons from Operating an Internal LLM Gateway for Production Agentic Applications (Zhong Liang Ong & Yek Khan)]]
> - *Working Locally with Open Weight LLMs*
> - *AI Agent Engineering*

---

## ⚡ TL;DR (Key Takeaways in 60 Seconds)

- **From Data Centers to AI Factories**: Traditional data centers retrieve static data; AI factories consume energy and raw data to manufacture tokens at scale.
- **Hardware Modularization**: NVIDIA's containerized data centers (**NVIDIA DSX POD**) package complete Vera Rubin AI factories into shipping containers, slashing on-site deployment from **6 months down to 14 days**.
- **The 5% Utilization Crisis**: Unpartitioned physical GPU clusters frequently sit at 5–30% utilization due to fragmentation and static allocations.
- **Multi-Tenancy with vCluster**: AI engineers demand `cluster-admin` access for Ray, vLLM, and custom CRDs. Running **vCluster** provides isolated virtual control planes inside Kubernetes namespaces, granting teams admin autonomy without risking host cluster stability.
- **GPU Slicing & Disaggregated Serving**: Combining HAMi vGPU slicing and Dynamic Resource Allocation (DRA) with Prefill/Decode disaggregation maximizes hardware efficiency and lowers blended cost per token.

---

## 📸 Stage & Slides

![saiyam pathak will everyone build an ai factory](Attachments/cds26-saiyam-pathak-will-everyone-build-an-ai-factory.jpg)

> **Keynote Kickoff (~15:05 SGT)**: *Will everyone build an AI Factory? Jensen just shipped one in a container.* presented by Saiyam Pathak (Head of Developer Relations @ vCluster Labs) on the MainStage at Suntec Singapore.

![saiyam pathak gtc berlin jensen quotes](Attachments/cds26-saiyam-pathak-gtc-berlin-jensen-quotes.jpg)

> **The GTC Berlin Catalyst (~15:08 SGT)**: Jensen Huang at GTC Berlin (October 21, 2026): *"To be part of this AI economy, you don't want to just be consuming the AI; you want to be producing the AI."*

![saiyam pathak nvidia dsx pod container](Attachments/cds26-saiyam-pathak-nvidia-dsx-pod-container.jpg)

> **The Big Launch (~15:10 SGT)**: *An AI factory that ships in a container — NVIDIA DSX POD*. A complete Vera Rubin AI factory tested in modular containers, compressing on-site setup from 6 months to 14 days.

![saiyam pathak singapore port containers pun](Attachments/cds26-saiyam-pathak-singapore-port-containers-pun.jpg)

> **The Singapore Context (~15:11 SGT)**: *Meanwhile, in Singapore: 44.66 million TEU moved in 2025*. Punning on physical shipping containers vs software containers at ContainerDays.

![saiyam pathak yes everyone will build an ai factory](Attachments/cds26-saiyam-pathak-yes-everyone-will-build-an-ai-factory.jpg)

> **The Verdict (~15:12 SGT)**: The definitive answer from Saiyam Pathak: *"Yes. Everyone will build an AI factory."*

![saiyam pathak four sizes of ai factory](Attachments/cds26-saiyam-pathak-four-sizes-of-ai-factory.jpg)

> **The Four Tiers (~15:13 SGT)**: *Four sizes of AI factory — Same idea, different sizes*. From RTX Spark (1 petaflop in hand) to Google Cloud A5X (960,000 Rubin GPUs).

![saiyam pathak day 15 the factory is here now what](Attachments/cds26-saiyam-pathak-day-15-the-factory-is-here-now-what.jpg)

> **The Operational Turning Point (~15:14 SGT)**: *The Day After Delivery — Day 15: the factory is here. Now what?* Lined up outside: people, apps, and more and more AI agents.

![saiyam pathak day 15 four governance questions](Attachments/cds26-saiyam-pathak-day-15-four-governance-questions.jpg)

> **The 4 Governance Questions (~15:15 SGT)**: *Who gets which GPU? Who can see whose data? Whose upgrade breaks whom? Who pays for what?* The core platform dilemma of operating shared AI infrastructure.

![saiyam pathak 5 percent gpu utilization waste](Attachments/cds26-saiyam-pathak-5-percent-gpu-utilization-waste.jpg)

> **The 5% Utilization Crisis (~15:15 SGT)**: *What happens today, in one number: 5% average GPU utilization across tens of thousands of production Kubernetes clusters*. Alibaba study: median task uses only ~4% of a GPU.

![saiyam pathak 1956 malcom mclean ideal x first container ship](Attachments/cds26-saiyam-pathak-1956-malcom-mclean-ideal-x-first-container-ship.jpg)

> **The Historical Precedent (~15:16 SGT)**: *26 April 1956 · Newark, New Jersey — The first container ship leaves Newark*. Malcom McLean loads 58 trailer boxes onto the *Ideal X*.

![saiyam pathak why the shipping container won sealed standard shared](Attachments/cds26-saiyam-pathak-why-the-shipping-container-won-sealed-standard-shared.jpg)

> **The 3 Winning Principles (~15:16 SGT)**: *1956 to Today — Why the shipping container won: Sealed, Standard, Shared*. The architectural blueprint for modern multi-tenant AI factories.

![saiyam pathak jensen on ai agents sandboxing](Attachments/cds26-saiyam-pathak-jensen-on-ai-agents-sandboxing.jpg)

> **Jensen on AI Agents (~15:17 SGT)**: *GTC Berlin · On AI Agents: "The most important thing is to make sure the agent is secure. Every single time an agent is launched, the privileges are different."*

![saiyam pathak one sealed box per team tenant cluster vcluster](Attachments/cds26-saiyam-pathak-one-sealed-box-per-team-tenant-cluster-vcluster.jpg)

> **The Multi-Tenancy Blueprint (~15:18 SGT)**: *The Answer for Teams — One sealed box per team: a tenant cluster*. *"A namespace is a shelf in a shared room. A tenant cluster is its own box."*

![saiyam pathak a sealed box has five walls](Attachments/cds26-saiyam-pathak-a-sealed-box-has-five-walls.jpg)

> **The 5 Walls of Isolation (~15:18 SGT)**: *What Sealed Means — A sealed box has five walls*. 1) Own control plane, 2) Walls between workloads (vNode), 3) Own network, 4) Own storage, 5) Own machines (Private Nodes).

![saiyam pathak many teams one gpu portion slicing](Attachments/cds26-saiyam-pathak-many-teams-one-gpu-portion-slicing.jpg)

> **GPU Slicing in Practice (~15:19 SGT)**: *Many Teams, One GPU — Every team gets a portion of the GPU*. Fractional allocation (Team Chat, Team Code, Team Docs) sharing a single GPU.

![saiyam pathak hami gpu slicing yaml spec](Attachments/cds26-saiyam-pathak-hami-gpu-slicing-yaml-spec.jpg)

> **HAMi YAML Enforcement (~15:19 SGT)**: Slicing memory (`nvidia.com/gpumem: 4000`) and compute cores (`nvidia.com/gpucores: 30`). *HAMi enforces each portion; Kubernetes DRA brings this natively.*

![saiyam pathak teams want an endpoint not a gpu gateway](Attachments/cds26-saiyam-pathak-teams-want-an-endpoint-not-a-gpu-gateway.jpg)

> **The Developer Reality (~15:20 SGT)**: *What Teams Really Want — Teams want an endpoint, not a GPU*. Central AI Gateway with one URL, API keys, quotas, and routing. *"Behind every endpoint is an inference cluster, a tenant cluster built to serve."*

![saiyam pathak disaggregated prefill decode serving scale](Attachments/cds26-saiyam-pathak-disaggregated-prefill-decode-serving-scale.jpg)

> **Inference at Scale (~15:22 SGT)**: *Inside One Inference Cluster — How an endpoint is served at scale: Disaggregated Prefill & Decode*. KV-aware routing with NIXL KV-cache transfer between GPU clusters (NVIDIA Dynamo v1.6.0 & llm-d 1.0).

---

## 📐 Four Sizes of AI Factory: Same Idea, Different Sizes

AI factories are not one-size-fits-all mega-facilities. They exist across four distinct form factors depending on latency, privacy, and scale requirements:

| Tier | Scale / Form Factor | Hardware & Specs | Purpose & Target Persona |
| :--- | :--- | :--- | :--- |
| **1. In Your Hand** | Personal / Edge Device | **RTX Spark**<br>• 1 petaflop compute<br>• 128 GB unified VRAM | **Developer / Researcher**<br>Build, test prototypes, fine-tune small models, keep sensitive proprietary data strictly local. |
| **2. A Rack** | On-Prem Server Rack | Dedicated cluster rack in enterprise data center | **Corporate Enterprise**<br>Many teams sharing one internal AI cloud; governed inference & fine-tuning behind enterprise firewall. |
| **3. A Container** | Turn-Key ISO Container | **NVIDIA DSX POD**<br>• Vera Rubin architecture<br>• 14 days on-site bring-up | **Mid-Market / Regional Provider**<br>A self-contained modular factory dropped onto prepared pad with water & power. |
| **4. A Whole Port** | Hyper-Scale Mega-Facility | **Google Cloud (A5X instances)**<br>• Up to **960,000 Rubin GPUs** | **Frontier Labs & Global Hyper-Scalers**<br>Pre-training frontier foundational models at planetary scale. |

---

## 🎯 The Central Inquiry: From Data Centers to AI Factories

> **The Thesis**: *Will everyone build an AI factory?* **Yes.** Just as every enterprise eventually ran compute infrastructure (or containerized microservices), every company will operate or orchestrate an AI factory for continuous intelligence generation.

### 1. The Triple Container Metaphor & The Singapore Hook
- **The 1956 Historical Precedent (Malcom McLean)**:
  - On **26 April 1956** in Newark, New Jersey, trucking entrepreneur **Malcom McLean** loaded 58 trailer-sized boxes onto the *Ideal X* (a converted WWII oil tanker) bound for Houston.
  - Prior to McLean, loading loose "break-bulk" cargo took days of manual labor and cost roughly $5.86 per ton. Containerization dropped freight handling costs to $0.16 per ton—unleashing the modern globalized supply chain.
- **The Modern Singapore Scale**:
  - In 2025, Singapore set a world record by moving **44.66 million TEU** (twenty-foot equivalent container units) through its maritime ports (Source: *Maritime and Port Authority of Singapore*).
- **The Three Eras of Containerization**:
  1. **Physical Shipping Containers (1956–Present)**: Standardized global freight, turning custom irregular cargo into modular, stackable, intermodal boxes.
  2. **Software Containers (2013–Present: Docker / OCI / Kubernetes)**: Standardized application execution, turning bespoke server environments into hermetic, portable microservices.
- **Why the Shipping Container Won (The 3 Core Pillars)**:
  1. **Sealed**: *“The crane never opens the box. What is inside stays inside.”*
     - $\implies$ **AI Infrastructure Implication**: Tenant isolation, secret separation, and data privacy. Host infrastructure runs workloads without exposing raw training sets, model weights, or sensitive prompts.
  2. **Standard**: *“Same size, same corners. Every crane and every ship fits every box.”*
     - $\implies$ **AI Infrastructure Implication**: Standardized interfaces (OpenAI-compatible endpoints, OCI container specs, Kubernetes CRDs, and MCP protocols). Any compliant cloud, cluster, or on-prem pod can execute the workload.
  3. **Shared**: *“One ship carries boxes for many different owners.”*
     - $\implies$ **AI Infrastructure Implication**: True multi-tenancy. Multiplexing workloads across costly pooled bare-metal GPU clusters so organizations can escape the 5% utilization trap.
- **The Core Question**: *Just as standardization democratized global trade and software delivery, will modular infrastructure enable every enterprise to run an AI factory?*

### 2. Jensen Huang's GTC Berlin Mandate (Oct 21, 2026)
- **The Quotes**:
  > *"Every company in Europe will become an AI company."*  
  > *"To be part of this AI economy, you don't want to just be consuming the AI; you want to be producing the AI."*  
  > — **Jensen Huang**, CEO of NVIDIA (*GTC Berlin Keynote*, 21 October 2026)
- **The Core Deduction**: **Producing AI means running an AI factory.**
- **The Hardware Reality: NVIDIA DSX POD**:
  - **Architecture**: Powered by NVIDIA's next-gen **Vera Rubin** GPU architecture.
  - **Prefabricated & Partner-Tested**: Built and pre-tested by OEM partners inside standardized, modular ISO containers before shipping.
  - **Drastic Deployment Compression**: Drops deployment time from **6 months down to 14 days** on a site with power and liquid cooling ready.
- **The Classical Data Center vs. The AI Factory**:
  - **Classical Data Center**: Built to store, retrieve, manipulate, and serve static data (files, records, web requests). General-purpose CPUs, stateless microservices, human-facing apps.
  - **AI Factory**: Built for **continuous token generation**. Raw inputs (electricity, unstructured domain data, developer prompts) go in; manufactured intelligence (tokens, embeddings, inferences, fine-tuned weights) comes out.

```mermaid
flowchart LR
    subgraph Inputs["Factory Inputs"]
        Power["Power & Cooling<br/>(Megawatts)"]
        Data["Raw Domain Data<br/>& Prompts"]
    end

    subgraph AIFactory["The Modular AI Factory (Kubernetes + GPUs)"]
        K8s["Cluster Control Plane<br/>(vCluster Multi-Tenancy)"]
        GPU["GPU Slicing & Scheduling<br/>(HAMi / DRA / MIG)"]
        Runtimes["AI Engines<br/>(vLLM / KServe / Ray / Triton)"]
    end

    subgraph Outputs["Factory Outputs"]
        Tokens["Manufactured Intelligence<br/>(Tokens / Inferences)"]
        Weights["Custom Weights<br/>(LoRA / Fine-tunes)"]
    end

    Inputs --> AIFactory
    AIFactory --> Outputs
```

---

## ⚖️ The Dilemma: Rent Tokens vs. Build Your Own Factory

Will every enterprise and startup actually build their own AI Factory?

| Dimension | Option A: Renting Tokens (API Hyper-Scalers) | Option B: Building an AI Factory (vCluster + GPUs) |
| :--- | :--- | :--- |
| **Economics** | Low barrier to entry; pay-per-token; prohibitive at extreme scale ($\text{Cost} \to \infty$ for continuous agentic loops). | Capital intensive upfront; near-zero marginal cost per token at high continuous utilization. |
| **Data Privacy & Sovereignty** | Data egresses to third-party endpoints; regulatory and compliance hurdles (finance, defense, healthcare). | Data stays air-gapped or on-prem; fully sovereign and compliant. |
| **Latency & Reliability** | Subject to public cloud API throttling, regional outages, and quota contention. | Dedicated deterministic QoS; local NVLink / InfiniBand throughput. |
| **Operational Complexity** | Low (managed endpoint). | High (requires cluster orchestration, driver management, GPU bin-packing, and Day-2 observability). |

---

## ⚙️ The Kubernetes Challenge: Solving AI Infrastructure Friction

Building an AI factory on Kubernetes introduces severe friction between **Data Science/AI Engineers** and **Platform/Infrastructure Teams**:

### The Day 15 Reality: *"The Factory is Here. Now What?"*
Once the prefabricated container arrives on-site and bring-up finishes on Day 14, **Day 15 is where the operational bottleneck starts**:
- **The Queue Outside the Door**:
  - **Humans**: Data scientists and ML engineers running ad-hoc Jupyter notebooks and exploratory hyperparameter sweeps.
  - **Traditional Apps**: Web apps, batch processing pipelines, and internal search microservices.
  - **More and More AI Agents**: Autonomous coding swarms, synthetic evaluators, and reasoning loops consuming millions of tokens 24/7 (as discussed in [[When Tokens Stop Being the Bottleneck - Operating Agentic Software Factories (Carl Ross)]]).
- **The Inevitable Collision**: Without strict multi-tenancy and scheduling boundaries, rogue agent loops or misconfigured batch jobs exhaust GPU VRAM, crash nodes, and starve production user-facing traffic.
- **The Four Fundamental Questions of Day 15**:
  1. **"Who gets which GPU?"** (Resource allocation, priority scheduling, preemptible batch training vs zero-latency interactive inference, vGPU slicing).
  2. **"Who can see whose data?"** (Multi-tenancy isolation, strict namespace boundaries, preventing proprietary training data or agent prompt leaks).
  3. **"Whose upgrade breaks whom?"** (CRD collision, CUDA/driver version incompatibilities, operator blast radius across shared nodes).
  4. **"Who pays for what?"** (Cost attribution, token accounting, showback/chargeback to business units for expensive bare-metal GPU clusters).

### The Platform Dilemma: The 5% Utilization Crisis
1. **The 5% Utilization Shock**:
   - Across tens of thousands of production Kubernetes clusters, the average GPU utilization is an abysmal **5%** (*Cast AI, Kubernetes Optimization Report 2026* across AWS, GCP, and Azure; excluding frontier AI research labs).
   - **Alibaba Production Case Study (6,742 GPUs)**: In an empirical audit of 6,742 GPUs in production (*Weng et al., "MLaaS in the Wild", NSDI 2022*), the **median task used only ~4% of a GPU**.
   - **The Slicing Imperative**: Letting workloads safely **split and share GPUs cut the total GPUs needed in half**.
2. **Cluster Admin Demands**: AI frameworks require custom CRDs (`RayCluster`, `KServe`, `NVIDIA GPU Operator`), specialized kernel drivers, and privileged daemonsets. Platform teams cannot safely hand out `cluster-admin` on production clusters.
3. **Multi-Tenancy Isolation**: Standard Kubernetes namespaces isolate CPU and RAM well, but leak cluster-scoped resources (CRDs, ingress controllers, cluster roles) and fail to slice GPUs cleanly.

### The Answer for Teams: One Sealed Box Per Team (A Tenant Cluster)
> *“A namespace is a shelf in a shared room. A tenant cluster is its own box.”*  
> — **Saiyam Pathak**

- **The Fundamental Difference: A Shelf vs. A Box**:
  - **Namespaces (*A shelf in a shared room*)**: Isolate CPU and memory limits, but force all teams to share cluster-scoped primitives. If one team registers or upgrades an operator CRD, it risks breaking other teams sharing the room.
  - **Tenant Clusters (*Its own sealed box via vCluster*)**: Each workload team (`Team Chat`, `Team Code`, `Team Docs`) operates within its own sealed virtual container placed on the shared ship deck:
    1. **Own API Server**: Isolated virtual control plane; AI engineers get virtual `cluster-admin` without compromising host security.
    2. **Own CRDs and RBAC**: Complete autonomy to deploy disparate operator versions (`RayCluster`, `KServe`, `vLLM`) without namespace collisions.
    3. **Own Upgrades**: Teams perform framework and Kubernetes minor version upgrades independently on their own timeline.
- **The Shared Ship (*The Bare-Metal Host*)**:
  - The physical Kubernetes host acts as the cargo ship: managing bare-metal node pooling, InfiniBand networking, storage backplanes, and **HAMi / DRA** dynamic GPU slicing, ensuring maximum hardware utilization across all tenant boxes.

#### What "Sealed" Means: A Sealed Box Has Five Walls
To guarantee true multi-tenant safety and solve the Day 15 governance crisis, a tenant cluster erects **five structural walls**:
1. **Wall 1: Own Control Plane** — Its own API server per tenant; no shared `kube-apiserver` bottleneck or RBAC cross-pollution.
2. **Wall 2: Walls Between Workloads** — `vNode` technology sandboxes every pod without requiring the latency overhead of full hardware hypervisors.
3. **Wall 3: Own Network** — Zero traffic between boxes unless explicitly whitelisted via network policy or ingress contracts.
4. **Wall 4: Own Storage** — Persistent volumes, model checkpoints, and training data stay strictly locked inside the box.
5. **Wall 5: Own Machines (Private Nodes)** — Dedicated physical GPU nodes mapped per tenant when strict cache residency, raw throughput, or regulatory compliance demands dedicated hardware.

#### Beyond Whole Nodes: Fractional GPU Slicing ("Many Teams, One GPU")
While Wall 5 allows allocating dedicated *Private Nodes*, whole nodes are wasteful when median tasks use only 4% of a GPU.
- **Portion-Based Partitioning**:
  - A single physical GPU is safely divided into proportional virtual slices across tenant boxes (`Team Chat` gets ~50%, `Team Code` gets ~35%, `Team Docs` gets ~15%).
- **Enforcement via HAMi (`resources.limits`)**:
  - Teams specify fractional GPU requirements directly in standard Kubernetes pod manifests:
  ```yaml
  resources:
    limits:
      nvidia.com/gpu: 1        # a slice of one GPU
      nvidia.com/gpumem: 4000  # hard memory ceiling (4000 MiB)
      nvidia.com/gpucores: 30  # guaranteed compute share (30% of cores)
  ```
- **HAMi vs. Kubernetes DRA**:
  - **HAMi**: Operates as a device plugin and runtime interceptor that hard-enforces `gpumem` and `gpucores` limits so a rogue inference prompt cannot cause a CUDA out-of-memory crash across neighboring tenant pods.
  - **Kubernetes Dynamic Resource Allocation (DRA)**: The upstream cloud-native effort bringing structured parameter resource allocation natively into core Kubernetes (directly previewed in tomorrow's session: *DRA Allocates, But Who Enforces? GPU Sharing Gap with HAMi* by Ivan Porta).

```mermaid
flowchart TD
    subgraph HostCluster["Host Physical Kubernetes Cluster (Bare Metal GPUs)"]
        HostCP["Host K8s Control Plane<br/>(Admin & Node Scheduling)"]
        PhysicalGPUs["Pooled NVIDIA GPUs (H100/A100/L40S)<br/><i>HAMi vGPU / DRA Driver Layer</i>"]

        subgraph TeamA["Namespace: team-alpha"]
            VCA["<b>vCluster Alpha</b> (Agent Fleets)<br/>• Custom RayCluster CRDs<br/>• Full Virtual Admin Access"]
        end

        subgraph TeamB["Namespace: team-beta"]
            VCB["<b>vCluster Beta</b> (Fine-tuning & RAG)<br/>• Custom KServe / vLLM CRDs<br/>• Independent K8s Version"]
        end
    end

    HostCP --> TeamA
    HostCP --> TeamB
    TeamA --> PhysicalGPUs
    TeamB --> PhysicalGPUs
```

### Sandboxing the Agent Swarm: Dynamic Per-Invocation Privileges
- **Jensen Huang's Security Mandate**:
  > *“The most important thing is to make sure the agent is secure. Every single time an agent is launched, the privileges are different.”*  
  > — **Jensen Huang**, CEO of NVIDIA (*GTC Berlin Keynote*, 21 October 2026)
- **The Operational Reality**:
  - In an AI factory running continuous autonomous agent loops, static long-lived API tokens or privileged container runtimes invite catastrophic security failure.
  - Every single agent execution requires an **ephemeral sandbox** with dynamically bounded, least-privilege tool access (connecting directly to [[Securing AI Coding Agents with Kubernetes Sandboxes (Ryan Djurovich)]]).
  - **The Two-Tier Isolation Model**:
    1. **Cluster Multi-Tenancy (vCluster)**: Isolates teams, operators, and CRDs at the Kubernetes control plane layer.
    2. **Runtime Containment (Sandbox CRDs / gVisor / microVMs)**: Isolates untrusted agent code execution and dynamic egress at the pod/process layer.

---

## 🚪 The Abstraction Layer: Teams Want an Endpoint, Not a GPU

> *“Teams want an endpoint, not a GPU. Behind every endpoint is an inference cluster, a tenant cluster built to serve.”*  
> — **Saiyam Pathak**

```mermaid
flowchart LR
    subgraph Consumers["Workload Consumers"]
        TC["Team Chat"]
        TCode["Team Code"]
        TDocs["Team Docs"]
        Agents["<b>AI Agents</b>"]
    end

    subgraph GatewaySubstrate["AI Gateway Layer"]
        GW["Central AI Gateway<br/>• Single Endpoint URL<br/>• Keys, Quotas & Routing<br/>• Token Accounting"]
    end

    subgraph TenantInference["Inference Tenant Clusters (vClusters)"]
        ChatPod["<b>chat endpoint</b><br/><i>Inference Cluster (2 GPUs)</i>"]
        CodePod["<b>code endpoint</b><br/><i>Inference Cluster (1 GPU Slice)</i>"]
    end

    TC --> GW
    TCode --> GW
    TDocs --> GW
    Agents --> GW
    GW --> ChatPod
    GW --> CodePod
```

### The Universal Contract
- **The Client Interface**: Product developers and AI agent swarms should never have to know cluster IP addresses, manage CUDA versions, or allocate raw node resources. They consume a simple, unified URL:
  ```bash
  curl https://ai.example.internal/v1/chat/completions \
    -H "Authorization: Bearer $API_KEY" \
    -d '{"model": "chat", "messages": [{"role": "user", "content": "..."}]}'
  ```
- **The Decoupled Reality**:
  - The **Gateway** routes requests, enforces token rate limits, and audits caller identity.
  - Behind the endpoint, a specialized **tenant inference cluster (vCluster)** auto-scales vLLM, KServe, or Ray pods backed by dedicated GPUs (e.g. 2 GPUs for `chat`) or fractional slices (e.g. 1 GPU slice for `code`).
- **Direct Vault Synergy**: Completely mirrors the production gateway architecture in [[Lessons from Operating an Internal LLM Gateway for Production Agentic Applications (Zhong Liang Ong & Yek Khan)]] (Loge) and [[Securing AI Coding Agents with Kubernetes Sandboxes (Ryan Djurovich)]] (Agent Router).

### Inside the Inference Cluster: Disaggregated Prefill & Decode (PD Disaggregation)
Behind each endpoint URL (`chat` or `code`), high-scale serving splits the autoregressive generation pipeline into two decoupled, asymmetric worker pools:



```mermaid
flowchart LR
    Req["request"] --> FE["<b>Frontend</b><br/>OpenAI API"]
    FE --> Router["<b>Router</b><br/>KV-aware"]
    
    subgraph DisaggregatedInference["Inside One Inference Cluster"]
        Router --> Prefill["<b>Prefill</b><br/><i>reads the prompt</i><br/>[GPU] [GPU]"]
        Router --> Decode["<b>Decode</b><br/><i>writes the answer</i><br/>[GPU] [GPU]"]
        Prefill <-->|KV cache<br/>via NIXL| Decode
        
        Planner["<b>Planner</b><br/>adds or removes workers<br/>to keep latency on target"] -.- Prefill
        Decode -.- KVOffload["<b>KV offload</b><br/>older cache moves to<br/>CPU memory and SSD"]
    end
    
    Decode -.->|the answer, token by token| FE
```

#### Detailed Component Architecture
1. **Frontend (OpenAI API)**: Ingests user or agent inference requests, authenticates callers, manages sessions, and streams tokens back to the caller.
2. **KV-Aware Router**: Inspects the incoming prompt prefix and routes requests to workers already holding warm Key-Value (KV) cache entries, preventing redundant precomputation.
3. **Prefill Workers (*Reads the prompt*)**:
   - **Compute-Bound** workload: Processes multi-thousand token prompts in parallel forward passes across dedicated GPUs (`[GPU] [GPU]`) to minimize Time-To-First-Token (TTFT).
4. **Decode Workers (*Writes the answer*)**:
   - **Memory-Bandwidth Bound** workload: Sequentially outputs tokens one by one and streams them back to the frontend.
5. **NIXL (High-Speed KV Cache Transfer)**:
   - Hardware-accelerated transport (InfiniBand / Spectrum-X RDMA / NVLink) transferring generated KV cache states directly from Prefill GPUs to Decode GPUs without CPU bottlenecking.
6. **Planner (Latency-Based Autoscaling)**:
   - Dynamically adds or removes Prefill/Decode workers based on real-time latency targets (TTFT and inter-token arrival time) rather than raw CPU/GPU utilization.
7. **KV Offload (Hierarchical Cache Tiering)**:
   - Evicts older/colder KV cache pages from expensive GPU VRAM into host CPU main memory and NVMe SSDs, and retrieves them when conversational context resumes without re-evaluating prompt tokens.
8. **Underlying Runtime Implementations**:
   - **NVIDIA Dynamo 1.6**: Orchestrates disaggregated prefill/decode on top of **vLLM**, **SGLang**, or **TensorRT-LLM** (*Dynamo v1.6.0 release notes, 22 October 2026*).
   - **llm-d 1.0**: Implements native disaggregated routing and KV-splitting directly on top of the **Kubernetes Gateway API Inference Extension** (*llm-d 1.0 announcement, 20 October 2026*).

---

## 🛠️ The Reference Demo: Two Machines, One Small AI Factory

![saiyam pathak demo two machines one small ai factory](Attachments/cds26-saiyam-pathak-demo-two-machines-one-small-ai-factory.jpg)

Saiyam demonstrated a live, functioning production AI factory running across just two physical servers:

```mermaid
flowchart TD
    subgraph Machine1["Machine 1: Shared Machine (1 GPU in portions)"]
        subgraph CP1["vCluster Standalone (Control Plane Cluster)"]
            T_Chat["<b>team-chat</b><br/>• vLLM endpoint<br/>• Own API server"]
            T_Code["<b>team-code</b><br/>• vLLM endpoint<br/>• Own API server"]
            T_Docs["<b>team-docs</b><br/>• vLLM endpoint<br/>• Own API server"]
        end
        HAMi_Layer["HAMi: Every team gets a portion of the GPU"]
        subgraph Slices["One NVIDIA L4 (24 GB)"]
            S_Chat["chat (7 GB)"]
            S_Code["code (7 GB)"]
            S_Docs["docs (5 GB)"]
            S_Free["free (5 GB)"]
        end
        CP1 --> HAMi_Layer
        HAMi_Layer --> Slices
    end

    subgraph Machine2["Machine 2: Dedicated Machine (2 whole GPUs)"]
        subgraph InfCluster["Inference Cluster (Private Node)"]
            D_Router["Dynamo Frontend + KV-Aware Router"]
            subgraph Disagg["PD Serving"]
                P_Worker["Prefill (GPU 1)"]
                D_Worker["Decode (GPU 2)"]
                P_Worker -->|KV Transfer| D_Worker
            end
            D_Router --> Disagg
        end
    end
```

- **Machine 1 (Shared Machine — Sliced GPU)**:
  - Hardware: 1x **NVIDIA L4 (24 GB VRAM)**.
  - Multi-Tenancy: **vCluster Standalone** hosts isolated virtual control planes for `team-chat`, `team-code`, and `team-docs`. Each team manages their own vLLM instance and API server.
  - Slicing: **HAMi** partitions the 24 GB L4 into discrete portions: 7 GB for Chat, 7 GB for Code, 5 GB for Docs, leaving 5 GB free.
- **Machine 2 (Dedicated Machine — Private Node Disaggregation)**:
  - Hardware: 2 whole GPUs (Private Node — nothing else runs here).
  - Serving: Dedicated inference cluster running **Dynamo frontend + KV-aware router**, disaggregating Prefill onto GPU 1 and Decode onto GPU 2.

---

## 📐 Spectrum of Slicing: The Same Two Choices at Every Size

![saiyam pathak the same two choices at every size](Attachments/cds26-saiyam-pathak-the-same-two-choices-at-every-size.jpg)

Whether deploying on an engineer's desk or an enterprise hyperscale cloud, the fundamental architectural decision remains identical: **share in portions (HAMi) or allocate whole dedicated nodes (Private Nodes)**.

| Scale Tier | Physical Hardware | Tenancy & Slicing Model |
| :--- | :--- | :--- |
| **1. Your Desk** | A few DGX Sparks | Each team owns a Spark. HAMi splits memory and compute for the team's local agent fleets. |
| **2. This Demo** | 2 servers, 3x L4s | 3 teams share one machine in portions (HAMi); dedicated inference cluster gets its own private machine. |
| **3. One Big Box** | 8x RTX PRO 6000 GPUs | Internal teams share the box, allocated as whole GPUs or fractional portions. |
| **4. Many Boxes** | Racks of 8-GPU servers | High-priority enterprise customers get whole servers; internal development teams share the rest. |
| **5. A GB300 Rack** | NVL72: 72 GPUs, 1 NVLink domain | 72 Blackwell Ultra GPUs + 36 Grace CPUs in a unified NVLink domain per rack. Customers get whole trays or whole racks. |
| **6. Many Racks** | AI Cloud (Hyperscale) | **vMetal** abstracts bare-metal racks into elastic machines. Every enterprise customer gets dedicated private nodes. |

---

## 🏢 The Enterprise AI Factory: Layer by Layer

![saiyam pathak enterprise ai factory layer by layer](Attachments/cds26-saiyam-pathak-enterprise-ai-factory-layer-by-layer.jpg)
![saiyam pathak enterprise ai factory layer by layer vcluster platform](Attachments/cds26-saiyam-pathak-enterprise-ai-factory-layer-by-layer-vcluster-platform.jpg)

A complete enterprise AI factory architecture is organized into five decoupled layers:

```mermaid
flowchart TD
    subgraph ManagementPlane["Management & Governance Layer"]
        VP["<b>vCluster Platform</b><br/>• Self-Service Catalog • Workload Templates • Sleep-When-Idle • Billing & Chargeback Per Team"]
    end

    subgraph WorkloadBoxes["Workload Containers (Sealed Tenant Boxes)"]
        W_K8s["<b>Kubernetes</b><br/>(App Teams)"]
        W_Train["<b>Ray · Slurm</b><br/>(Model Training)"]
        W_Dyn["<b>Dynamo</b><br/>(Inference Serving)"]
        W_LLMD["<b>llm-d</b><br/>(Inference Serving)"]
    end

    subgraph VirtualCP["Dedicated Virtual Control Planes"]
        CP_1["Virtual CP"]
        CP_2["Virtual CP"]
        CP_3["Virtual CP"]
        CP_4["Virtual CP"]
    end

    subgraph CentralHostCP["Central Host Control Plane Cluster"]
        HostSched["Schedulers • NVIDIA GPU Operator • DRA • HAMi • Prometheus Metrics"]
    end

    subgraph BareMetalAbstraction["Bare-Metal Virtualization"]
        VMetal["<b>vMetal</b><br/>Turns physical racks into virtual machines, networks, and storage behind a single API"]
    end

    subgraph PhysicalBuilding["The Building (Physical Infrastructure)"]
        Hardware["Bare-metal GPU servers (Rubin/Blackwell) • Spectrum-X Network Fabric • NVMe Storage • Megawatt Power & Liquid Cooling"]
    end

    ManagementPlane --> WorkloadBoxes
    WorkloadBoxes --- VirtualCP
    VirtualCP --> CentralHostCP
    CentralHostCP --> BareMetalAbstraction
    BareMetalAbstraction --> PhysicalBuilding
```

1. **vCluster Platform**: Orchestrates self-service tenant provisioning, enterprise workload templates, automated sleep-when-idle power saving, and per-team cost attribution.
2. **Workload Containers (Tenant Clusters)**: Completely isolated runtime environments for general App teams (K8s), Training workloads (Ray / Slurm), and high-throughput inference (Dynamo / llm-d).
3. **Dedicated Control Planes**: Each tenant box gets its own virtual API server, eliminating noisy neighbor issues and CRD collisions on the host.
4. **Host Control Plane Cluster**: Centrally manages schedulers, the NVIDIA GPU Operator, Dynamic Resource Allocation (DRA), HAMi device plugins, and cluster telemetry.
5. **vMetal**: Cloud-native bare-metal abstraction that turns physical compute racks into composable machines, networks, and persistent storage behind a uniform API.
6. **The Building**: The raw physical substrate: bare-metal GPU servers, low-latency InfiniBand/NVLink fabric, fast checkpoint NVMe storage, and high-density liquid cooling.

---

## ⚡ Six Ways to Get More from Every GPU

![saiyam pathak six ways to get more from every gpu](Attachments/cds26-saiyam-pathak-six-ways-to-get-more-from-every-gpu.jpg)

To beat the 5% average utilization trap, Saiyam outlined six architectural techniques deployed at enterprise scale:

1. **Route to the Cache**: Direct repeated prompt prefixes to the exact worker that already has it in its KV cache (prefix-aware routing).
2. **Split Prefill and Decode**: Reading prompts (compute-intensive) and writing tokens (memory-bandwidth intensive) require fundamentally different GPU profiles; decouple and scale them independently.
3. **Offload the KV Cache**: Tier inactive KV cache to host CPU RAM and high-speed NVMe SSDs instead of wasting GPU VRAM or recomputing from scratch.
4. **Scale on Latency**: Auto-scale worker replicas when **Time-To-First-Token (TTFT)** or inter-token latency spikes, rather than scaling on misleading CPU/GPU utilization percentages.
5. **Right-Size the GPU**: Allocate fractional vGPU slices (HAMi) for smaller open-weight models (7B/14B), dedicated whole GPUs for massive frontier models, and private dedicated nodes for security-critical enterprise tenants.
6. **Sleep When Idle**: Automatically spin down idle tenant clusters during off-peak hours and release their GPUs back to the central pooling engine (**vCluster Sleep Mode**).

> **Enabling Open Tools**: Dynamo router, KVBM (KV-cache Block Manager) and Planner; llm-d on the Gateway API Inference Extension; HAMi; and vCluster Sleep Mode.

---

## 🚀 How to Start on Monday: Start Small, Then Grow

![saiyam pathak how to start on monday start small](Attachments/cds26-saiyam-pathak-how-to-start-on-monday-start-small.jpg)

Saiyam concluded with a concrete 4-step pragmatic roadmap for platform teams:

```mermaid
flowchart LR
    S1["<b>Step 1: Start with One Box</b><br/>• 1 GPU<br/>• 1 open model<br/>• Kubernetes on top"] --> S2["<b>Step 2: Give Teams Tenant Clusters</b><br/>• vCluster self-service<br/>• Nobody waits for tickets"]
    S2 --> S3["<b>Step 3: Slice the GPU</b><br/>• Fractional portions with HAMi<br/>• Graduate to native DRA"]
    S3 --> S4["<b>Step 4: Write House Rules</b><br/>• Quotas & rate limits<br/>• Sleep when idle<br/>• Metrics per team"]
```

- **Step 1: Start with One Box**: Don't wait for a $100M data center build-out. Take one server with a single GPU, pull down an open-weight model (e.g. Qwen 2.5 or Llama 3), and stand up Kubernetes.
- **Step 2: Give Every Team a Tenant Cluster**: Implement self-service tenant virtual clusters (`vCluster`). Eliminate internal IT ticketing friction so AI teams can innovate immediately.
- **Step 3: Slice the GPU**: Maximize hardware utilization by dividing physical GPUs into portions using **HAMi** today, and transition to Kubernetes native **DRA** as it matures.
- **Step 4: Write the House Rules**: Establish clear operational governance: tenant quotas, automatic sleep-when-idle policies, and granular token/GPU cost metrics per business unit.

---

## 💡 Key Takeaways & Synthesis

1. **Tokens as the Currency of the Future**:
   - As emphasized by Carl Ross (OpenAI) earlier today in [[When Tokens Stop Being the Bottleneck - Operating Agentic Software Factories (Carl Ross)]], software delivery is transitioning to continuous autonomous loops. AI factories are the physical engine behind this shift.
2. **Hardware in a Container, Software in a vCluster**:
   - Jensen Huang solved the hardware distribution problem by putting the physical data center into modular ISO containers.
   - The cloud-native community solves the operational distribution problem by putting multi-tenant AI control planes into virtual Kubernetes clusters (**vCluster**).
3. **The Hybrid Inevitability**:
   - Most enterprises will not build multi-billion dollar mega-factories like frontier labs, but they *will* operate "micro AI factories" for proprietary fine-tuning, low-latency agent loops, and sovereign inference.

---

## 🔗 Related Sessions & Notes

- 🌟 [[ContainerDays Singapore 2026]] — Full conference hub, timetable, and attendance tracker
- 🏭 [[When Tokens Stop Being the Bottleneck - Operating Agentic Software Factories (Carl Ross)]] — Operating autonomous agent swarms against continuous token output
- 💬 [[Fireside Chat with Kelsey Hightower & Geet Bhanawat]] — Infrastructure as a workload carrier; fixing underlying bottlenecks
- 🚪 [[Lessons from Operating an Internal LLM Gateway for Production Agentic Applications (Zhong Liang Ong & Yek Khan)]] — Production model routing and quota enforcement on Kubernetes
- 🛡️ [[Securing AI Coding Agents with Kubernetes Sandboxes (Ryan Djurovich)]] — Kubernetes `Sandbox` CRDs and runtime isolation for agent execution

