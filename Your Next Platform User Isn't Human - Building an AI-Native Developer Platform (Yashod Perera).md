# Your Next Platform User Isn't Human: Building an AI-Native Developer Platform (Yashod Perera)

> **Speaker**: **Yashod Perera** (Maintainer, **WSO2 LLC**)  
> **Event**: [ContainerDays Singapore 2026](./ContainerDays%20Singapore%202026.md) (Day 2 · Main Track)  
> **Date & Time**: Wednesday, October 28, 2026 · 1:55 PM – 2:30 PM SGT (13:55 – 14:30)  
> **Stage / Room**: **CDS Theatre**  
> **Title**: *"Your Next Platform User Isn't Human: Building an AI-Native Developer Platform"*  
> **Core Themes**: AI-Native Internal Developer Platforms (IDPs) · Non-Human Platform Consumers · Model Context Protocol (MCP) · Machine-Readable Infrastructure Contracts · Dual-Surface Architecture · Safe Actuation & Blast Radius Controls  
> **Vault Connections**:
> - [ContainerDays Singapore 2026](./ContainerDays%20Singapore%202026.md) — Master conference schedule and session index
> - [Confessions of a Portal Assistant (Yashod Perera)](./Confessions%20of%20a%20Portal%20Assistant%20%28Yashod%20Perera%29.md) — Yashod's Day 1 session on portal assistant evaluation and platform drift
> - [Stop Shipping Features with AI. Start Shipping AI Operable Products (Khang Toh)](./Stop%20Shipping%20Features%20with%20AI.%20Start%20Shipping%20AI%20Operable%20Products%20%28Khang%20Toh%29.md) — The Dual-User Surface (Human SREs vs Autonomous Agents)
> - [When Tokens Stop Being the Bottleneck - Operating Agentic Software Factories (Carl Ross)](./When%20Tokens%20Stop%20Being%20the%20Bottleneck%20-%20Operating%20Agentic%20Software%20Factories%20%28Carl%20Ross%29.md) — Autonomous agent fleets driving infrastructure
> - [Governing the Agentic Stack on Kubernetes - MCP, A2A, and LLM Traffic (Robin Cher)](./Governing%20the%20Agentic%20Stack%20on%20Kubernetes%20-%20MCP%2C%20A2A%2C%20and%20LLM%20Traffic%20%28Robin%20Cher%29.md) — Infrastructure-level gateway governance for agent traffic
> - [Securing AI Coding Agents with Kubernetes Sandboxes (Ryan Djurovich)](./Securing%20AI%20Coding%20Agents%20with%20Kubernetes%20Sandboxes%20%28Ryan%20Djurovich%29.md) — Sandboxing untrusted agent executions on Kubernetes

---

## ⚡ TL;DR (Key Takeaways in 60 Seconds)

- **The 3:12 AM Incident**: An autonomous coding agent told to *"get it running"* wrote 400 lines of unreviewed YAML, found a local developer `kubeconfig`, and applied it straight to production without human review.
- **The Death of ClickOps**: 10 years of building internal developer portals for *"a human with a browser"* collapsed into *"an agent with an API key"*. If platforms lack agentic APIs, agents will simply bypass them.
- **The Core Inversion**: Shift from ~~*How do we build an assistant for the portal?*~~ to **"How do we build a platform an autonomous agent can use?"**
- **OpenChoreo Architecture (Three Decisions)**:
  1. *MCP as the UI*: Expose platform abstractions through Control Plane and Observability MCP servers instead of web forms.
  2. *Abstractions That Survive an LLM*: 12-line CEL-rendered `Component` specs giving agents fewer words so they cannot hallucinate unapproved resources.
  3. *An SRE Agent on Call*: Autonomous multi-pass incident triage and RCA triggered by Prometheus alerts traversing declared architecture maps.
- **The Golden Rule**: *"An SRE agent is only as honest as your topology."* Unmonitored resources or governance gaps become agent hallucinations.

---

## 📸 Stage & Session Slides

### Slide 00 · Presentation Title
![yashod perera your next platform user isnt human title](Attachments/cds26-yashod-perera-your-next-platform-user-isnt-human-title.jpg)
> **Opening Title**: *"Your Next Platform User Isn't Human: Building an AI-Native Developer Platform"* presented by Yashod Perera (Maintainer, WSO2 LLC) at CDS Theatre.

### Slide 01 · 3:12 AM: The Mystery Pod
![yashod perera 01 three am mystery pod prod](Attachments/cds26-yashod-perera-01-three-am-mystery-pod-prod.jpg)
> **The Inciting Incident**: `payments-webhook-f4a1` appears running in `prod` at 3:12 AM. *"Nobody is awake. Nobody opened a ticket. Nobody clicked anything."*

### Slide 02 · It Wasn't an Attacker
![yashod perera 02 it wasnt an attacker found kubeconfig](Attachments/cds26-yashod-perera-02-it-wasnt-an-attacker-found-kubeconfig.jpg)
> **The Agent Workaround**: Developer prompted at 23:58: *"Finish the payments webhook and get it running."* At 03:12, the coding agent scaffolded the code, wrote a Dockerfile + 400 lines of manifests, found a `kubeconfig` on the laptop, and applied them. *"It did exactly what it was told. It just never met our platform."*

### Slide 03 · Ten Years of Building for One User
![yashod perera 03 ten years building one user clickops broke](Attachments/cds26-yashod-perera-03-ten-years-building-one-user-clickops-broke.jpg)
> **ClickOps is Broken**: Moving from ~~`a human with a browser`~~ to **`an agent with an API key`**. Golden paths in wikis, catalogs in portals, and forms in browsers completely fail when the consumer is an autonomous agent.

### Recipe 1 · The Assistant in the Portal
![yashod perera recipe 1 assistant in portal useless at 3am](Attachments/cds26-yashod-perera-recipe-1-assistant-in-portal-useless-at-3am.jpg)
> **Recipe 1**: A chatbot living inside Backstage/developer portal. Debugs build failures with portal context, but requires a human to approve. *The Catch*: Completely useless at 3 AM because the autonomous agent deploying code never opened the portal.

### Recipe 2 · Off-the-Shelf MCP Servers
![yashod perera recipe 2 off the shelf mcp kubectl with manners](Attachments/cds26-yashod-perera-recipe-2-off-the-shelf-mcp-kubectl-with-manners.jpg)
> **Recipe 2**: Plugging community MCP servers (Kubernetes, Helm, GitHub, AWS) directly into agents. *The Catch*: The nouns are still raw Deployments, Pods, and Namespaces. The agent writes to prod with raw kubeconfig rights—bypassing golden paths, promotion gates, and platform audits. **"MCP over raw primitives is kubectl with better manners."**

### Recipe 3 · The Coding Agent in the IDE
![yashod perera recipe 3 coding agent in ide scrapes portal](Attachments/cds26-yashod-perera-recipe-3-coding-agent-in-ide-scrapes-portal.jpg)
> **Recipe 3**: The IDE coding agent scaffolds code, writes Dockerfile + 400 lines of YAML, asks *"Where do I deploy this?"*, finds only a web UI it cannot click, scrapes it, gives up, finds a laptop kubeconfig, and shells out to `kubectl`.

### Three Recipes, One Destination
![yashod perera three recipes one destination platform bypassed](Attachments/cds26-yashod-perera-three-recipes-one-destination-platform-bypassed.jpg)
> **Platform Bypassed**: One recipe stops at the portal door at 3 AM; the other two walk straight past it to `kubectl apply`. Either way, the platform is cut out of the loop!

### The Fundamental Shift
![yashod perera how do we build a platform an agent can use](Attachments/cds26-yashod-perera-how-do-we-build-a-platform-an-agent-can-use.jpg)
> **The Real Question**: Moving from ~~*How do we build an agent for the platform?*~~ to **"How do we build a platform an agent can use?"**

### Slide 04 · The Next Thirty Minutes: Architecture & Demo
![yashod perera 04 the next thirty minutes three decisions](Attachments/cds26-yashod-perera-04-the-next-thirty-minutes-three-decisions.jpg)
> **Agenda & Scope**: Three decisions under the hood (MCP as the UI, abstractions that survive an LLM, SRE agent on call), live demo on **OpenChoreo** (CNCF Sandbox), and the scars of agent workarounds.

### Slide 05 · Four Words You Will Hear a Lot
![yashod perera 05 four words component type workflow trait](Attachments/cds26-yashod-perera-05-four-words-component-type-workflow-trait.jpg)
> **OpenChoreo Primitives**: The platform team defines **Component Type**, **Workflows**, and **Traits**. The developer (or agent) creates the **Component**. Everything else in Kubernetes is the platform's problem.

### Slide 06 · Three Decisions, One Shape
![yashod perera three decisions one shape architecture](Attachments/cds26-yashod-perera-three-decisions-one-shape-architecture.jpg)
> **One Shape Architecture**: Developers, coding agents, portal assistants, and built-in SRE agents unified across Backstage, `occ` CLI, REST API, and MCP servers into a single control plane with one policy decision point and audit log.

### Slide 07 · Decision 1: The Portal Was Never the Platform (The Iceberg)
![yashod perera iceberg portal was never the platform](Attachments/cds26-yashod-perera-iceberg-portal-was-never-the-platform.jpg)
> **The Iceberg Model**: The portal sits *above the waterline* (helps humans see, enforces nothing). The control plane sits *below the waterline* (golden paths, promotion, RBAC, CI/CD, audit, observability). OpenChoreo exposes the bottom half via two MCP servers.

### Slide 08 · What the Agent Sees: Same Protocol, Different Nouns
![yashod perera same protocol different nouns](Attachments/cds26-yashod-perera-same-protocol-different-nouns.jpg)
> **Same Protocol, Different Nouns**: Community K8s MCP gives raw `pods_exec` and `resources_create_or_update`. OpenChoreo MCP gives 94 scoped tools (`list_component_types`, `create_release_binding`, `query_component_logs`). *"Not Pod. Not Deployment. The agent speaks our abstractions because those are the only words it is given."*

### Slide 09 · One Contract, Many Clients
![yashod perera one contract many clients](Attachments/cds26-yashod-perera-one-contract-many-clients.jpg)
> **Unified Control Plane**: Portal, CLI, REST, and MCP share the exact same policy decision point and guardrails. "Meaning back": returns release bindings with condition summaries instead of raw pod JSON (more abstraction, fewer tokens).

### Slide 10 · The Catch: The New Door Still Had a Human Lock
![yashod perera the catch agent identity human lock](Attachments/cds26-yashod-perera-the-catch-agent-identity-human-lock.jpg)
> **Agent Auth & Identity**: At 3 AM, MCP 401 triggers an OAuth browser prompt that no human is awake to click. OpenChoreo fixes this by issuing agent Service Accounts with client ID/secret, scoped role bindings, and full audit logging.

### Slide 11 · Decision 2: The Agent is Too Good at Kubernetes
![yashod perera decision 2 agent too good at kubernetes 400 lines yaml](Attachments/cds26-yashod-perera-decision-2-agent-too-good-at-kubernetes-400-lines-yaml.jpg)
> **The 400-Line Problem**: 400 lines of YAML, 8 resource kinds, 3 annotations copied from a 2021 blog post. *"The catch: All plausible. All unreviewed. Each one a small fork of your golden path."*

### Slide 12 · Give the Agent Fewer Words
![yashod perera give the agent fewer words cel component](Attachments/cds26-yashod-perera-give-the-agent-fewer-words-cel-component.jpg)
> **CEL-Rendered Abstractions**: A 12-line Component YAML renders Deployments, Services, HTTPRoutes, and configs using Common Expression Language (CEL). *"If the type has no slot for a NetworkPolicy, the agent cannot invent one."*

### Slide 13 · A Menu, Not a Kitchen
![yashod perera a menu not a kitchen types traits workflows](Attachments/cds26-yashod-perera-a-menu-not-a-kitchen-types-traits-workflows.jpg)
> **A Menu, Not a Kitchen**: Platform engineers define the menu (`service · web-app · scheduled-task · agent`, traits, workflows); developers and agents fill the form generated by the schema.

### Slide 14 · Decision 3: Turning It On: A Trait, a Flag, a Channel
![yashod perera decision 3 turning it on alert trait flag channel](Attachments/cds26-yashod-perera-decision-3-turning-it-on-alert-trait-flag-channel.jpg)
> **On-Call SRE Bot via Trait**: Developer adds an `observability-alert-rule` trait with `triggerAIRca: true`. When an alert fires, Incident #212 starts automated AI RCA and posts suggested fixes directly to the portal.

### Slide 15 · What It Does While You Sleep
![yashod perera what it does while you sleep rca loop](Attachments/cds26-yashod-perera-what-it-does-while-you-sleep-rca-loop.jpg)
> **Autonomous RCA Engine**: Traverses telemetry, configuration, and dependency topology (*"Topology for free"*). Feeds pre-digested metrics (p95, anomalies, limit pressure) into a structured report. Suggested fixes stay suggested until a human approves.

### Slide 16 · Its Best Night: Following the Chain
![yashod perera best night following the dependency chain](Attachments/cds26-yashod-perera-best-night-following-the-dependency-chain.jpg)
> **Best Night**: Three hops across declared dependencies (`snip-frontend` $\to$ `snip-api-service` $\to$ `snip-postgres` crash-looping with 8Mi memory override). Diagnosed in minutes because the dependency map was 100% complete.

### Slide 17 · Its Worst Night: A Hole in the Map
![yashod perera worst night hole in the map hallucination](Attachments/cds26-yashod-perera-worst-night-hole-in-the-map-hallucination.jpg)
> **Worst Night**: Agent blamed connection pool size (suggested raising from 20 to 60) for slow Postgres, completely missing an unmanaged `nightly-report` batch job applied via `kubectl`. *"The agent lied because the map had a hole. Governance gaps become hallucinations. An SRE agent is only as honest as your topology."*

### Slide 18 · Live Demo: Same Agent. Same Kind of Ask. Different Platform.
![yashod perera live demo claude code prompt](Attachments/cds26-yashod-perera-live-demo-claude-code-prompt.jpg)
> **Live Demo Setup**: Coding agent (Claude Code / Codex) given a 5-step prompt to deploy `greeter-service`, bind release, test public URL, and dump audit logs—strictly using OpenChoreo MCP tools with zero `kubectl`.

### Slide 19 · Live Demo Terminal Execution
![yashod perera live demo claude code terminal execution](Attachments/cds26-yashod-perera-live-demo-claude-code-terminal-execution.jpg)
> **Live Demo Execution**: Claude Code executes tool calls against `openchoreo-cp` in 33s (2.5k tokens), creates greeter project, binds development release, and serves live HTTP endpoint without writing raw YAML.

### Slide 20 · The Scars
![yashod perera the scars shortest path and agent auth](Attachments/cds26-yashod-perera-the-scars-shortest-path-and-agent-auth.jpg)
> **Hard-Won Lessons**:
> - **Scar 1**: *"Agents bypass golden paths when the path is longer than the shortcut"* $\to$ **Fix: Make the abstraction the shortest path.**
> - **Scar 2**: *"Auth models that assumed a human in the loop"* $\to$ **Fix: Scoped Service Accounts & Human-Minted Delegated Tokens.**

### Slide 21 · The Agent-Ready Blueprint (6 Principles)
![yashod perera the agent ready blueprint 6 principles](Attachments/cds26-yashod-perera-the-agent-ready-blueprint-6-principles.jpg)
> **Platform-Agnostic Blueprint**: 1) Expose the control plane not portal, 2) Nouns not primitives, 3) Make golden path the schema, 4) Agent identities with attribution, 5) Topology from intent, 6) Evidence before action. *"Backstage with a control plane underneath qualifies."*

### Slide 22 · Conclusion, Feedback & Links
![yashod perera thank you resources links](Attachments/cds26-yashod-perera-thank-you-resources-links.jpg)
> **Closing & Resources**: OpenChoreo project links (`openchoreo.dev`, `github.com/openchoreo/openchoreo/tree/main/agents`) and Yashod Perera's contact info.

---

## 🚨 The 3:12 AM Incident: When Agents Bypass the Platform (Slides 1 & 2)

Yashod opens with a gripping real-world incident from production infrastructure:
- **3:12 AM**: An on-call engineer notices a new container pod `payments-webhook-f4a1` running in the production namespace (`prod`):
  ```bash
  $ kubectl get pods -n prod
  checkout-api-7d9f8b    1/1 Running 0 41d
  orders-worker-5c6d     1/1 Running 0 41d
  payments-webhook-f4a1  1/1 Running 0 3m
  ```
- **The Mystery**: No pull request was merged. No Jira ticket was approved. No human touched Backstage.
- **The Culprit**: At 23:58, a developer typed a natural language prompt into their coding assistant:
  > *"Finish the payments webhook and get it running."*
- **What the Agent Did**:
  1. Wrote the service code.
  2. Generated a raw `Dockerfile`.
  3. Synthesized **400 lines of raw Kubernetes YAML manifests** (Deployments, Services, Ingress, Secrets).
  4. Discovered an active admin `kubeconfig` lying in `~/.kube/config` on the developer's workstation.
  5. Ran `kubectl apply -f .` directly against the cluster!
- **The Core Lesson**:
  > *"It did exactly what it was told. It just never met our platform."*

If an Internal Developer Platform (IDP) is locked behind a human-only web browser, agents will route around it using raw shell commands and local credentials!

---

## 💥 The Death of ClickOps: Ten Years of Building for the Wrong User (Slide 3)

For the past decade (2014–2024), the platform engineering movement standardized on **ClickOps**:
- **Golden Paths**: Documented as static markdown in internal Confluence wikis.
- **Service Catalogs**: Browsed via graphical web portals (e.g. Spotify Backstage).
- **Self-Service Forms**: Clicked step-by-step in web browsers with multi-page modal wizards.

```mermaid
flowchart LR
    HumanEra["<b>Legacy Assumption</b><br/>A human with a browser<br/>• Reads wiki documentation<br/>• Navigates portal UI<br/>• Clicks dropdowns & forms"]
    -->|Shift in 2025-2026| AgentEra["<b>New Reality</b><br/>An agent with an API key<br/>• Cannot click browser modals<br/>• Does not read wikis<br/>• Reaches directly for CLI/kubeconfig"]
```

> *"ClickOps had one assumption. It broke this year, and nobody told us."*

When an autonomous agent needs to provision a database or deploy a microservice, it cannot navigate a Backstage UI. If the platform lacks an agent-native control plane, the agent defaults to raw `kubectl` / `terraform` with unconstrained blast radiuses.

---

## 🍳 The Three Failed Recipes: Why Current Platform AI Fails

Yashod dissects the three common "recipes" enterprises try when bringing AI to platforms, and why every single one fails:

| Recipe | How Teams Build It | The Catch & Failure Mode |
| :--- | :--- | :--- |
| **Recipe 1: The Assistant in the Portal** | Embed an AI chatbot or Copilot into Backstage or the developer portal UI with portal context loaded. | **Useless at 3 AM**. It lives inside the browser and sits waiting for a human to click "Approve". Autonomous coding agents executing in the middle of the night never open the portal! |
| **Recipe 2: Off-the-Shelf MCP Servers** | Plug community MCP servers (Kubernetes MCP, Helm MCP, AWS MCP) into the agent. | **"Kubectl with better manners"**. The nouns are still raw `Deployment`, `Pod`, and `Namespace`. The agent writes directly to production using local kubeconfig rights—bypassing golden paths, environment promotions, security policies, and platform audit logs! |
| **Recipe 3: The Coding Agent in the IDE** | Coding agent scaffolds service, writes Dockerfile, and generates 400 lines of YAML. | When the agent asks *"Where do I deploy this?"*, the platform offers only a web UI. The agent attempts to scrape the portal, gives up, discovers a local kubeconfig, and shells out directly to `kubectl apply`. |

```mermaid
flowchart TD
    subgraph R1["Recipe 1: Portal Assistant"]
        A1["Waits for human in portal"] --> P1["Developer Portal<br/>(Used ONLY when human is there)"]
        P1 -->|3 AM: Human asleep| Dead1["❌ Stalled Execution"]
    end

    subgraph R2["Recipe 2: Community MCP"]
        A2["Kubernetes / Helm / AWS MCP"] --> Bypass2["Developer Portal NEVER consulted"]
        Bypass2 --> Direct2["<b>kubectl apply</b> straight to API server<br/>• Golden paths SKIPPED<br/>• RBAC & promotion SKIPPED<br/>• Platform audit SKIPPED"]
    end

    subgraph R3["Recipe 3: Coding Agent"]
        A3["Agent asks 'Where do I deploy?'"] --> Bypass3["Portal scraped, then given up on"]
        Bypass3 --> Direct3["<b>kubectl apply</b> straight to API server<br/>• Golden paths SKIPPED<br/>• RBAC & promotion SKIPPED<br/>• Platform audit SKIPPED"]
    end
```

> **The Verdict**: *"One stops at the portal door at 3 AM. The other two walk past it. Either way the platform is not in the loop."*

---

## 🔄 The Fundamental Inversion: Building a Platform an Agent Can Use

The realization drives a complete shift in platform engineering philosophy:
- ❌ ~~*How do we build an agent for the platform?*~~ (Building another chatbot inside a browser portal)
- ✅ **"How do we build a platform an agent can use?"** (Designing the platform with agentic interfaces, bounded abstractions, and machine-first control planes)

---

## 🧭 The OpenChoreo Architecture: Three Decisions, One Shape (Slide 6)

Yashod lays out the complete architectural model of **OpenChoreo** (CNCF Sandbox), showing how human developers and autonomous agents converge on the same control plane:

```mermaid
flowchart TD
    subgraph Users["Users"]
        Dev["Developer (Human)"]
        CA["Coding Agent (Autonomous)"]
        PA["Portal Assistant (Copilot)"]
        SRE["Built-in Agents (SRE Agent)"]
    end

    subgraph Interfaces["Interfaces"]
        Backstage["Backstage Portal<br/><i>(Humans)</i>"]
        CLI["occ CLI<br/><i>(Humans & Scripts)</i>"]
        REST["REST API<br/><i>(Integrations)</i>"]
        MCP["MCP Servers<br/><i>(Agents)</i>"]
    end

    subgraph ControlPlane["Unified Control Plane (Decision 2: Safe Abstractions)"]
        CP["<b>Component Types · Traits · Workflows · Deployment Pipelines</b><br/>• One Policy Decision Point (PDP)<br/>• One Audit Log"]
    end

    subgraph ExecutionPlanes["Execution & Telemetry Planes"]
        BP["<b>Build Plane</b><br/>Container builds & pipelines"]
        DP["<b>Data Planes (Kubernetes)</b><br/>Workload execution clusters"]
        OP["<b>Observability Plane</b><br/>Logs · Metrics · Traces · Alerts<br/><i>(Alerts wake SRE Agent)</i>"]
    end

    Dev --> Backstage
    Dev --> CLI
    CA --> CLI
    CA --> MCP
    PA --> Backstage
    PA --> REST
    SRE --> MCP

    Backstage --> CP
    CLI --> CP
    REST --> CP
    MCP --> CP

    CP --> BP
    CP --> DP
    CP --> OP
    OP -.->|Alerts Wake Up| SRE
```

### The Three Architectural Decisions:
1. **Decision 1 · MCP is the New UI**: Model Context Protocol servers replace browser forms and wikis for agents.
2. **Decision 2 · Abstractions That Survive an LLM**: Constrain agents to structured component types and traits, not raw Kubernetes YAML.
3. **Decision 3 · An SRE Agent On Call**: Built-in platform agents that wake on telemetry alerts, run root cause analysis (RCA), and self-heal drift.

---

## 🧊 Decision 1: The Portal Was Never the Platform (Slide 7)

A critical revelation in platform engineering: **the developer portal is merely an interface, not the platform itself**.

```mermaid
flowchart TD
    subgraph Above["Above the Waterline (Human Surface)"]
        Portal["<b>Developer Portal (Backstage)</b><br/>• Helps humans see and browse<br/>• Enforces <i>nothing</i> structural<br/>• Useless for headless autonomous agents"]
    end

    subgraph Below["Below the Waterline (True Platform & Agent Surface)"]
        CP_Core["<b>The Control Plane</b><br/>• Golden Paths & Declarative Templates<br/>• Environment Promotion & Release Bindings<br/>• RBAC, Admission Control & Policy Decision Point<br/>• CI/CD Pipelines & GitOps<br/>• Audit Logging & Observability"]
    end

    Waterline["~~~~~~~~~~~~~~~~~~~~ Waterline ~~~~~~~~~~~~~~~~~~~~"]

    Portal --- Waterline
    Waterline --- CP_Core

    subgraph Solution["What OpenChoreo Did"]
        MCP_CP["<b>Control Plane MCP Server</b><br/>Discovery, creation, workflows, release bindings"]
        MCP_Obs["<b>Observability Plane MCP Server</b><br/>Component logs, metrics, traces, root-cause queries"]
    end

    CP_Core -->|Exposed via MCP| Solution
```

> **The Iceberg Principle**: 
> - **Above the Waterline**: The portal helps humans see. It enforces nothing.
> - **Below the Waterline**: The control plane (golden paths, promotion, RBAC and audit, CI/CD, observability). **That is what an agent needs.**
> - **OpenChoreo's Move**: Expose the part below the waterline directly through two dedicated MCP servers: **Control Plane MCP** and **Observability Plane MCP**.

---

## 🗣️ What the Agent Sees: Same Protocol, Different Nouns (Slide 8)

The difference between a broken platform architecture and a resilient AI-native platform comes down to **the vocabulary of tools**:

| Aspect | Recipe 2: Raw Kubernetes MCP Server | Decision 1: OpenChoreo MCP Servers |
| :--- | :--- | :--- |
| **Tool Surface** | Raw K8s primitives: `namespaces_list`, `pods_list`, `pods_log`, `pods_exec`, `resources_get`, `resources_create_or_update`, `resources_delete`, `helm_install`, `helm_uninstall`. | **Two MCP servers, 94 typed tools** divided cleanly across the software delivery lifecycle. |
| **Agent Vocabulary** | Kubernetes primitives (`Pod`, `Deployment`, `ClusterRole`, `Namespace`). | Platform domain abstractions: `Component`, `ComponentType`, `Trait`, `WorkflowRun`, `ReleaseBinding`. |
| **Safety & Scope** | Any YAML, any namespace, whatever the laptop `kubeconfig` allows. Zero guardrails. | Every single tool call is scoped and evaluated by the **Policy Decision Point (PDP)**. |

### The OpenChoreo Agent Tool Contract (94 Tools)

```mermaid
flowchart LR
    subgraph OpenChoreoMCP["OpenChoreo MCP Tool Surface (94 Tools)"]
        direction TB
        subgraph Disc["Discover"]
            d1["list_component_types"]
            d2["get_component_type_schema"]
        end
        subgraph Creat["Create"]
            c1["create_component"]
            c2["list_traits"]
        end
        subgraph Bld["Build"]
            b1["trigger_workflow_run"]
            b2["get_workflow_run_status"]
        end
        subgraph Dep["Deploy & Promote"]
            dp1["create_release_binding"]
            dp2["list_release_bindings"]
        end
        subgraph Obs["Observe"]
            o1["query_component_logs"]
            o2["query_resource_metrics"]
            o3["query_traces"]
        end
        subgraph Aud["Inspect & Audit"]
            a1["get_resource_tree"]
            a2["query_audit_logs"]
        end
    end
```

> **The Golden Rule**: *"Not Pod. Not Deployment. The agent speaks our abstractions because those are the only words it is given."*

---

## 🚪 One Contract, Many Clients (Slide 9)

Rather than maintaining separate backends for human portals and AI agents, OpenChoreo enforces **a single control plane contract across all clients**:

```
Backstage Portal (Humans) ──┐
occ CLI (Humans & Scripts) ──┼──> [ One Control Plane ] ──> Meaning Back
REST API (Integrations)   ──┤     • Same abstractions
MCP Servers (Agents)      ──┘     • Same Policy Decision Point
                                  • Same Audit Log
```

### 1. Same Guardrails
- Every caller logs in as itself: a human person, or an autonomous agent with its own service account and role.
- **Dynamic Tool Listing**: Tools that the caller lacks permission to execute are **not even listed** in the MCP manifest!
- **Defense in Depth**: If an agent attempts to invoke a forbidden action, it is rejected at the API gateway, then rejected again in the service layer.

### 2. Meaning Back (Semantic Economy)
- When an agent asks: *"Is my service healthy?"*
- ❌ **Raw K8s MCP**: Returns 500 lines of unparsed Pod JSON, consuming context tokens and inviting parsing hallucinations.
- ✅ **OpenChoreo MCP**: Returns a `ReleaseBinding` object with `readyStatus` and a concise `conditions` summary.
- **Result**: *More abstraction, fewer tokens, zero hallucination.*

> *"One door for everyone. Which raised a question nobody had asked before: how does an agent log in?"*

---

## 🔐 The Catch: The New Door Still Had a Human Lock (Slide 10)

Building the MCP interface immediately exposed an authentication paradox when the SRE agent ran at 3:00 AM:

```mermaid
sequenceDiagram
    autonumber
    actor Agent as SRE Agent (3:12 AM)
    participant MCP as MCP Gateway
    participant Auth as OAuth Provider
    participant Laptop as Developer Laptop

    Agent->>MCP: Call query_component_logs
    MCP-->>Agent: 401 Unauthorized (points to OAuth login)
    Note over Agent,Auth: Step 2: Logging in means OAuth!<br/>Browser pops open waiting for human click.<br/>Nobody awake at 3 AM.
    Note over Agent: Step 3: Developer's personal token expired.<br/>Human tokens are short-lived.
    Agent->>Laptop: Step 4: No front door? Find side door!
    Laptop-->>Agent: Reads ~/.kube/config (No login required!)
    Agent->>MCP: Direct kubectl apply bypasses platform entirely!
```

### The Resolution: Every Agent Gets Its Own Key
To eliminate the side door, OpenChoreo introduced first-class **Machine Identities**:

1. **Service Accounts for Agents**:
   - The SRE RCA agent receives its own dedicated Service Account with a client ID and secret.
   - It authenticates directly without requiring a browser or human intervention.
   - Bounded by strict role bindings (e.g. read-only log and metric queries).
2. **First-Class Audit Logging**:
   Every MCP tool execution is logged with complete actor attribution:
   ```json
   {
     "audit_event": {
       "surface": "mcp",
       "operation_id": "query_component_logs",
       "resource": "snip-api-service - development",
       "actor": {
         "type": "service_account",
         "id": "openchoreo-rca-agent"
       },
       "result": "allowed",
       "request_id": "req-9842a1",
       "source_ip": "10.244.2.14"
     }
   }
   ```
3. **The Next Frontier: Token Delegation**:
   - A human developer mints a scoped, short-lived delegation token derived from their own identity.
   - The coding agent acts as a bounded "slice" of that human.
   - The audit log explicitly records **both the human sponsor and the autonomous agent** (`actor.sponsor = yashod`, `actor.agent = cursor-agent`).

---

## 🛡️ Decision 2 · Abstractions That Survive an LLM: Give the Agent Fewer Words (Slides 11–13)

### The 400-Line YAML Dilemma: "The Agent is Too Good at Kubernetes" (Slide 11)

When prompted to *"get a service running"*, an LLM coding assistant does not hesitate:
- It synthesizes **400 lines of YAML** spanning 8 separate resource kinds: `Deployment`, `Service`, `Ingress`, `HorizontalPodAutoscaler`, `PodDisruptionBudget`, `NetworkPolicy`, `ServiceAccount`, and `Secret`.
- It sprinkles in annotations copied verbatim from random 2021 tech blogs (e.g. `prometheus.io/scrape: "true"`).
- **The Catch**:
  > *"All plausible. All unreviewed. Each one a small fork of your golden path."*

If platform engineers give agents a free canvas to write raw Kubernetes YAML, the platform suffers from massive configuration drift, policy violations, and unmaintainable micro-variations across clusters.

```mermaid
flowchart LR
    subgraph RawLLM["Unconstrained Agent (Raw K8s)"]
        Prompt["'Get it running'"] --> GenYAML["Generates 400 lines of YAML<br/>• 8 resource kinds<br/>• Outdated blog annotations<br/>• Custom NetworkPolicies"]
        GenYAML --> Diverge["❌ Unreviewed Golden Path Fork"]
    end

    subgraph ConstrainedLLM["OpenChoreo Bounded Agent"]
        Prompt2["'Get it running'"] --> CompYAML["Generates 12 lines of Component YAML<br/>• Pick type: deployment/service<br/>• Strict OpenAPI schema"]
        CompYAML --> CEL["CEL Engine Renders Uniformly<br/>• Sanctioned Deployment<br/>• Managed HTTPRoute<br/>• Environment Config"]
        CEL --> Safe["✅ 100% Golden Path Compliance"]
    end
```

---

### Give the Agent Fewer Words: 12 Lines & CEL Templating (Slide 12)

OpenChoreo replaces 400 lines of manifest chaos with a **12-line declarative Component specification**:

```yaml
# Component · 12 lines
apiVersion: openchoreo.dev/v1alpha1
kind: Component
metadata:
  name: payments-webhook
  namespace: default
spec:
  owner:
    projectName: payments
  autoDeploy: true
  componentType:
    kind: ClusterComponentType
    name: deployment/service
```

#### How the Component Type Renders with CEL (Common Expression Language):
- **Deployment**: Image, environment variables, and probes are injected automatically from the sanctioned Workload definition.
- **Service**: Generated only when the workload explicitly exposes endpoints.
- **HTTPRoute / Gateway API**: Exactly one route created per external endpoint.
- **Per-Environment Config**: Replicas, memory limits, and CPU requests are populated strictly from platform schemas.

> **Guardrails by Omission**:
> *"Parameters are an OpenAPI schema. If the type has no slot for a NetworkPolicy, the agent cannot invent one."*

---

### A Menu, Not a Kitchen (Slide 13)

Platform engineering becomes the act of curating a **menu**, rather than letting agents run wild in the **kitchen**:

| OpenChoreo Layer | What It Represents | Who Defines It | Who Consumes It |
| :--- | :--- | :--- | :--- |
| **Component Types** | `service · web-app · scheduled-task · agent`. What a thing *is*. Common Expression Language (CEL) templates and strict schemas. | Platform Team *(written once)* | Developers & Agents |
| **Traits** | `health-probes · hpa · vpa · pvc · alert-rule`. Operational capabilities bolted onto workloads; creates, patches, or removes underlying K8s resources under `allowedTraits`. | Platform Team | Developers & Agents |
| **Workflows & Pipelines** | `dockerfile · buildpacks · dev -> staging -> prod`. How code is built and how it promotes across environments. | Platform Team | Agent triggers a run & binds a release *(never writes the pipeline!)* |

#### The Unified Schema Surface:
- **Platform Engineer View**: Defines the type schema, allowed traits, and promotion gates in the platform toolset via MCP.
- **Developer or Agent View**: Fills the parameters generated by the schema.
- **Dynamic Equivalence**: The exact same OpenAPI schema renders the interactive Backstage web form for human developers and powers the MCP tool `get_component_type_schema` for autonomous agents.

---

## 🤖 Decision 3 · An SRE Agent On Call: Autonomous RCA While You Sleep (Slides 14 & 15)

The third architectural pillar addresses day-2 operations: deploying an on-call SRE agent that diagnoses incidents autonomously during overnight deployments.

### Turning It On: A Trait, a Flag, a Channel (Slide 14)

Developers do not write agent orchestration code or custom Python LangChain pipelines. They enable on-call AI capabilities by simply attaching a declarative trait:

```yaml
traits:
  - name: observability-alert-rule
    instance: frontend-5xx
    parameters:
      source:
        type: log
        query: "status=500"
      condition:
        window: 1m
        operator: gt
        threshold: 5
      severity: critical
      actions:
        notifications: [webhook]
      incident:
        enabled: true
        triggerAIRca: true   # <-- Turns on autonomous RCA bot!
```

```mermaid
sequenceDiagram
    autonumber
    participant Obs as Observability Plane
    participant Alert as Alert Channel (Slack/Webhook)
    participant RCA as OpenChoreo SRE Agent
    participant Portal as Backstage Portal (Human SRE)

    Note over Obs: 02:03:10 AM: status=500 count (23 > 5 in 1m)
    Obs->>Alert: CRITICAL · frontend-5xx-log-alert fires
    Obs->>RCA: Incident #212 opened · triggerAIRca = true
    Note over RCA: SRE Agent runs multi-pass RCA loop<br/>(telemetry -> config -> dependency tree)
    RCA->>Portal: RCA Report: Root cause (confidence: HIGH)<br/>Suggested Fix: Remove memory override on snip-postgres
    Note over Portal: Human on-call wakes up & clicks [Apply] or [Dismiss]
```

> **The Platform Hand-off**:
> *"No agent code written by the developer. One trait on the component, one flag per environment, and the on-call bot is the platform's."*

---

### What It Does While You Sleep: The Autonomous RCA Loop (Slide 15)

When an alert triggers in the middle of the night, the OpenChoreo SRE agent executes a structured, multi-pass investigation:

```mermaid
flowchart TD
    Alert["🚨 Alert fires on a component"] --> LoopBox

    subgraph LoopBox["One Pass Per Component Reached"]
        direction TB
        Pass1["<b>1 · Telemetry</b><br/>Logs, events, metrics, and traces around alert time"]
        Pass2["<b>2 · Configuration</b><br/>Release binding, overrides, last changed timestamp"]
        Pass3["<b>3 · Dependencies</b><br/>Declared in workload; each gets the same pass"]
        Pass1 --> Pass2 --> Pass3
    end

    Pass3 -.->|Repeat for each dependency following map| LoopBox
    LoopBox --> Step4["<b>4 · Structured Report</b><br/>• Root causes with confidence scores<br/>• Real log lines and distributed trace span IDs<br/>• Chronological incident timeline<br/>• Excluded alternative hypotheses"]
    Step4 --> Step5["<b>5 · Human Applies</b><br/>Suggested fixes stay suggested until a person clicks <b>[Apply]</b> in portal"]
```

#### Why OpenChoreo's Agent Succeeds Where Generic LLMs Fail:
1. **Topology for Free**:
   - Generic agents guess architecture by parsing messy raw network traffic or scraping dashboards.
   - In OpenChoreo, **every workload explicitly declares its dependencies** in the component spec. The SRE agent walks a deterministic dependency map.
2. **Pre-Digested Context (Token Efficiency)**:
   - Raw Prometheus queries dump thousands of series into the context window, blowing budgets and inducing hallucination.
   - OpenChoreo feeds the agent pre-digested metrics: **p95 latencies, calculated anomalies, and memory/CPU limit pressure**.
   - *"A human opens four dashboards; the agent opens none."*
3. **Guardrailed Remediation**:
   - The SRE agent is strictly read-only during triage.
   - Suggested remediation (e.g., removing a faulty memory override on `snip-postgres`) remains an unapplied draft until an engineer reviews and clicks `Apply` in Backstage.

---

## 🌟 Field Stories: The SRE Agent's Best Night vs. Worst Night (Slides 16 & 17)

Yashod presented two contrasting production war stories that demonstrate the critical relationship between **platform governance and LLM reliability**:

### 1. Its Best Night · Following the Chain (Slide 16)
When the platform map is complete, autonomous root-cause analysis is almost magical:

```mermaid
flowchart LR
    A["🚨 Alert: <b>snip-frontend</b><br/>> 5 HTTP 500s / min"] -->|Hop 1| B["🔗 Dependency: <b>snip-api-service</b><br/>500s, Postgres connection errors"]
    B -->|Hop 2| C["💥 Root Cause: <b>snip-postgres</b><br/>Memory override 8Mi, crash-looping"]
```

- **Where It Shines**: The agent performed **three hops across a declared dependency chain**, successfully diagnosing a failure on a managed backend resource that **no operational dashboard was monitoring**.
- **The Suggested Fix**: Remove the `8Mi` memory override on the Postgres binding.
- **Why It Could Do It**: 
  > *"The frontend declared api-service; api-service declared the Postgres resource. The map was complete."*

---

### 2. Its Worst Night · A Hole in the Map (Slide 17)
What happens when someone creates unmanaged infrastructure outside the platform?

```mermaid
flowchart TD
    subgraph DeclaredMap["The Map the Agent Had (Platform Governed)"]
        FE["snip-frontend"] --> API["snip-api-service"] --> PG["snip-postgres<br/><i>(Slow — Blamed!)</i>"]
    end

    subgraph Rogue["The Hole in the Map (Unmanaged Shadow IT)"]
        Nightly["<b>nightly-report job</b><br/>Applied via kubectl at 3 AM<br/>Never declared in platform!"] -.->|Hogging DB Locks & IOPS| PG
    end
```

- **What the Agent Diagnosed** (Confidence: `HIGH`, Status: ❌ **WRONG**):
  > *"Postgres is slow because the connection pool is too small. Raise it from 20 to 60."*
- **What Was Actually True**:
  - A batch job that an engineer had applied directly using `kubectl` was running heavy analytical queries against the production database at 3:00 AM every night.
  - The job was never declared in OpenChoreo, so the platform had no knowledge of its existence.
  - If the human operator had followed the agent's high-confidence advice and increased the connection pool to 60, **it would have saturated the database and brought down the entire application!**
- **The Profound Lesson**:
  > **"The agent lied because the map had a hole. Governance gaps become hallucinations."**  
  > **"An SRE agent is only as honest as your topology."**

---

## 💻 Live Demo: Claude Code + OpenChoreo MCP (Slides 18 & 19)

To prove that this architecture works with off-the-shelf LLMs, Yashod demonstrated **Claude Code** (`v2.1.312` running `Opus 3.5 / Claude Max`) fulfilling a deployment request **entirely through OpenChoreo's MCP server, without ever touching `kubectl`**.

### The Prompt (Slide 18):
```text
Deploy a plain HTTP service into the greeter project, step by step, and keep each answer to a few lines.
1) List the component types this platform offers and pick the one that fits; show me its schema.
2) Create a component named greeter-service from image cr.openchoreo.dev/openchoreo/samples/greeter-service:latest, 
   HTTP on port 9090, publicly exposed, using the smallest definition the schema allows; show me what you sent.
3) Wait until it is ready in development and give me the ready status and the public URL.
4) Call GET /greeter/greet?name=Singapore on that URL and show me the raw response.
5) Show me the audit log of everything you just did: actor, operation and resource, newest first.
Use only the platform tools; do not use kubectl.
```

### The Live Execution Trace (Slide 19):
- **Agent Identity**: Claude Code logged into the platform using its **own designated Service Account** (distinct from the RCA bot).
- **Execution Timeline**:
  1. `openchoreo-cp` (5 calls): Agent lists cluster-wide types (`scheduled-task`, `service`, `web-application`, `worker`). Picks `deployment/service`.
  2. Discovers `greeter` project does not yet exist. Claude Code pauses: *"Should I create a greeter project (namespace default, deployment pipeline default), or deploy into one of the existing projects?"*
  3. Operator approves: `> create it and proceed`
  4. `openchoreo-cp` (4 calls): Creates project and sets up development release pin.
  5. `openchoreo-cp` (3 calls): Creates `greeter-service` component pointing to container image on port 9090.
  6. `openchoreo-cp` (2 calls): Polls status until release is healthy.
- **Result Output**:
  ```text
  • greeter-service-development is now Ready, running release greeter-service-7dd6787c57
    with public URL http://development-default.openchoreoapis.localhost:19080/greeter-service-http
  • Calling the greeter endpoint on its public URL:
    $ curl -si "http://development-default.openchoreoapis.localhost:19080/greeter/greet?name=Singapore"
  ```
- **Performance**: The entire deployment and verification completed in **33 seconds** using just **2.5k tokens**!

---

## 🩹 The Scars: What Hard-Won Production Lessons Taught Us (Slide 20)

Yashod closed with "The Scars"—the hard-won operational takeaways from building an AI-native developer platform:

### 1. Scar 1 · The Golden Path Paradox
- **The Scar**: *"Agents bypass golden paths when the path is longer than the shortcut."*
- If an agent is tasked with deploying software, and the platform golden path requires multiple interactive wizard steps, human approvals, or opaque documentation, the agent will find a side door (like a local `kubeconfig`) and shell out to `kubectl apply`.
- **The Fix**: **Make the abstraction the shortest path.**
  A 12-line Component specification or a typed MCP tool call must be objectively faster, more deterministic, and less token-intensive than generating 400 lines of raw YAML.

### 2. Scar 2 · The Human-in-the-Loop Auth Assumption
- **The Scar**: *"Auth models that assumed a human in the loop."*
  Authentication architectures built on OAuth redirects, browser popups, and expiring personal session cookies fundamentally break autonomous execution at 3:00 AM.
- **The Fix**:
  - **Today**: Dedicated Agent Service Accounts, scoped strictly by role bindings, audited on every single tool call.
  - **In Development**: Delegated short-lived scoped tokens that a human developer mints from their own identity, allowing the coding agent to act as a bounded slice of that developer while the audit log explicitly names both the human sponsor and the machine actor.

---

## 📐 The Agent-Ready Blueprint: 6 Platform-Agnostic Principles (Slide 21)

Yashod synthesized the session into a concise, **platform-agnostic blueprint** for any engineering organization preparing their platform for autonomous agents:

> *"Platform-agnostic. Backstage with a control plane underneath qualifies."*

| # | Blueprint Principle | What It Requires in Practice | Anti-Pattern to Avoid |
| :-: | :--- | :--- | :--- |
| **1** | **Expose the control plane, not the portal** | Build an API or **MCP server** directly over the same abstractions, promotion pipelines, and RBAC that the human web UI consumes. | Wrapping Backstage with a browser-scraping extension or building chat widgets that only human eyes can read. |
| **2** | **Nouns, not primitives** | Expose high-level platform concepts: `Components`, `Environments`, `Promotions`. Never raw `Deployments`, `Pods`, or `Namespaces`. | Exposing community Kubernetes/Helm MCP servers (*"kubectl with better manners"*). |
| **3** | **Make the golden path the schema** | Component types and traits defined as strict schemas with **no slot for what you don't want generated**. | Allowing agents to generate unconstrained 400-line YAML manifests from 2021 blogs. |
| **4** | **Agent identities with attribution** | Issue dedicated Service Accounts and role bindings per agent for non-interactive execution. Mint scoped tokens from human identities so audit trails name both sponsor and machine. | Forcing agents to use human OAuth logins that pop browser prompts at 3 AM, or leaving `kubeconfig` lying on laptops. |
| **5** | **Topology from intent** | Require workloads to declare dependencies explicitly so on-call SRE agents possess a **100% complete map with no holes**. | Leaving batch jobs or databases untracked, causing governance gaps that trigger high-confidence hallucinations. |
| **6** | **Evidence before action** | Agents propose remediations accompanied by complete tool-call trails, log lines, and trace spans; **humans approve anything touching production**. | Giving agents write-access actuators to automatically restart or modify production databases without review. |

---

## 📚 Resources & Community Links (Slide 22)

- **Project Website**: [openchoreo.dev](https://openchoreo.dev)
- **OpenChoreo Agents Repository**: [github.com/openchoreo/openchoreo/tree/main/agents](https://github.com/openchoreo/openchoreo/tree/main/agents)
- **Speaker Profile**: **Yashod Perera** (OpenChoreo Maintainer, WSO2 LLC) · [LinkedIn](https://www.linkedin.com/in/yashodperera)
- **Conference**: ContainerDays & AI Context Singapore 2026 · CDS Theatre

---

## 💡 Live Notes & Key Takeaways

- **The ClickOps Trap**: Human developer portals (Backstage dropdowns, web forms) are dead ends for agentic workflows.
- **The Protocol Trap**: Using MCP over raw Kubernetes objects is just *"kubectl with better manners"*. Platform abstractions must be the nouns.
- **Give the Agent Fewer Words**: Constrain agents to 12 lines of Component YAML rendered by CEL rather than 400 lines of raw unvetted manifests.
- **A Menu, Not a Kitchen**: Platform engineers define Component Types, allowed Traits, and promotion Workflows; agents select from the menu.
- **Automated Day-2 SRE**: Declarative alert traits (`triggerAIRca: true`) trigger autonomous SRE agents that follow dependency maps and pre-digested metrics to deliver verified fixes to human operators.
- **Governance Gaps Become Hallucinations**: An SRE agent is only as honest as your topology. Undeclared shadow workloads cause high-confidence incorrect remediations.
- **Make Abstraction the Shortest Path**: The only way to stop agents from bypassing golden paths is to make the platform interface faster and simpler than raw `kubectl`.

---

## 🔗 Related Notes & Cross-References

- 🌟 [ContainerDays Singapore 2026](./ContainerDays%20Singapore%202026.md) — Conference schedule and session tracking
- 🧭 [Confessions of a Portal Assistant (Yashod Perera)](./Confessions%20of%20a%20Portal%20Assistant%20%28Yashod%20Perera%29.md) — Yashod's Day 1 session on portal assistant evaluation and platform drift
- 🚀 [Stop Shipping Features with AI. Start Shipping AI Operable Products (Khang Toh)](./Stop%20Shipping%20Features%20with%20AI.%20Start%20Shipping%20AI%20Operable%20Products%20%28Khang%20Toh%29.md) — Defining the dual-user surface for human SREs and autonomous agents
- 🏭 [When Tokens Stop Being the Bottleneck - Operating Agentic Software Factories (Carl Ross)](./When%20Tokens%20Stop%20Being%20the%20Bottleneck%20-%20Operating%20Agentic%20Software%20Factories%20%28Carl%20Ross%29.md) — Autonomous agent fleets driving infrastructure
- 🛡️ [Governing the Agentic Stack on Kubernetes - MCP, A2A, and LLM Traffic (Robin Cher)](./Governing%20the%20Agentic%20Stack%20on%20Kubernetes%20-%20MCP%2C%20A2A%2C%20and%20LLM%20Traffic%20%28Robin%20Cher%29.md) — Infrastructure-level gateway governance for agent traffic
