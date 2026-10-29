# Stop Shipping Features with AI. Start Shipping AI Operable Products (Khang Toh)

> **Speaker**: **Khang Toh**  
> **Event**: [[ContainerDays Singapore 2026]] (ContainerDays Track)  
> **Date & Time**: Tuesday, October 27, 2026 · 4:10 PM – 4:45 PM SGT  
> **Stage / Room**: **CDS Theatre**  
> **Title**: *"Stop Shipping Features with AI. Start Shipping AI Operable Products"*  
> **Core Themes**: Day-2 Operability · The AI Code Velocity Trap · Dual-User Operability (Humans & Autonomous Agents) · Self-Healing Telemetry · Reconciliation Loops Over Code Generation  
> **Vault Connections**:
> - [[ContainerDays Singapore 2026]]
> - [[When Tokens Stop Being the Bottleneck - Operating Agentic Software Factories (Carl Ross)]] — Software factories creating immense code velocity that outpaces operations
> - [[Fireside Chat with Kelsey Hightower & Geet Bhanawat]] — *"AI is just another workload"*; addressing the real operational bottlenecks
> - [[Shipping Reliable AI Agents - Building with Langfuse and ClickHouse (Max Deichmann)]] — Observability, trace analytics, and agent reliability
> - [[AI-Generated Code == Code You Can Trust - AISG & Sonar at EDB]] — Static analysis and trust boundaries for AI code
> - *AI Agent Engineering*

---

## ⚡ TL;DR (Key Takeaways in 60 Seconds)

- **The AI Velocity Trap**: LLM coding agents generate features in minutes, but velocity without Day-2 operability produces unmaintainable, fragile production systems.
- **The Dual-User Dilemma**: Software now has two primary users: **Human SREs** (requiring dashboards, mental models, and bounded blast radiuses) and **Autonomous Agents** (requiring structured JSON/MCP diagnostics, deterministic state reconciliation, and safe actuators).
- **DORA Metrics Inversion**: AI accelerates deployment frequency and reduces lead time, but **Change Failure Rate spikes and MTTR worsens** due to "LGTM Engineering" (humans blindly approving 1,000-line agent PRs).
- **The 7 Primitives of AI Operability**: Outcome Intent, Journey Context, Workflow Map, Recovery Path, Policy Boundary, Safe Actions, and Feedback Loops.
- **fdeploy Reference Platform**: 5-pillar architecture (CodeFactory, CodeWiki, Brains, Automation, SlackOps) paired with OpenHands Agent Server sandboxes, demonstrated via an **8-minute autonomous incident remediation loop**.

---

## 📸 Stage & Session Slides

![khang toh stop shipping features with ai operable products intro](Attachments/cds26-khang-toh-stop-shipping-features-with-ai-operable-products-intro.jpg)

> **Stage Kickoff (~16:10 SGT)**: *Stop Shipping Features with AI. Start Shipping AI Operable Products* presented by Khang Toh at the CDS Theatre during ContainerDays & AI Context Singapore 2026.

![khang toh about fdeploy fagent fidentity fgateway](Attachments/cds26-khang-toh-about-fdeploy-fagent-fidentity-fgateway.jpg)

> **Speaker & Platform Context**: **About fdeploy** — *Applied AI engineering, deployed inside your operation. Bring agentic engineering under enterprise control.* Structured around three pillars: **FAgent** (connecting coding tools on desktops & sandboxes), **FIdentity** (trusted identity for people & agents via enterprise SSO), and **FGateway** (model access, routing, usage/cost attribution).

![khang toh stop shipping features operability stack](Attachments/cds26-khang-toh-stop-shipping-features-operability-stack.jpg)

> **The Architectural Convergence (2000 $\to$ 2026)**: Synthesizing SDLC, DevOps, SRE, Operability, and Agentic Engineering.

![khang toh 2000 2026 eras waterfall to agentic](Attachments/cds26-khang-toh-2000-2026-eras-waterfall-to-agentic.jpg)

> **The 5 Eras (2000–2026)**: *Not nostalgia. A pattern.* Tracing the evolution from Waterfall (Pre-2000) $\to$ Agile/XP (2001–2009) $\to$ DevOps/CI-CD (2009–2015) $\to$ SRE/Observability (2015–2022) $\to$ AI-native dev (2023–2026).

![khang toh pattern shrink gap dev operating](Attachments/cds26-khang-toh-pattern-shrink-gap-dev-operating.jpg)

> **The Unbroken Pattern**: *Shrink the gap between dev and operating — Every movement moved the feedback loop closer to the work: [LEARN + PLAN] $\to$ [BUILD] $\to$ [SHIP] $\to$ [OPERATE]. "We did not just automate away toil."*

![khang toh every cycle loop faster ops did not disappear](Attachments/cds26-khang-toh-every-cycle-loop-faster-ops-did-not-disappear.jpg)

> **The Invariable Law**: *"Every cycle - the loop got faster. But Ops did not disappear. Every era shortened the distance between writing software and knowing whether it worked."*

![khang toh agentic engineering harness around it](Attachments/cds26-khang-toh-agentic-engineering-harness-around-it.jpg)

> **The 2026 Reality**: *2026: AI changes the way we build — The developer is no longer only human. Agentic Engineering works because of the harness around it: context, tools, verification, gates, policy, feedback. The model writes. The harness decides whether the goal was met.*

![khang toh from vibe coding to harness and loop engineering](Attachments/cds26-khang-toh-from-vibe-coding-to-harness-and-loop-engineering.jpg)

> **The Engineering Evolution**: Beyond *Prompt Engineering* and *Vibe Coding* $\to$ the rise of **Harness Engineering** and **Loop Engineering**.

![khang toh lgtm engineering 1000 line pr human lunch](Attachments/cds26-khang-toh-lgtm-engineering-1000-line-pr-human-lunch.jpg)

> **The Industry Pathology**: *NOT JOKE! REAL PROBLEM! — LGTM Engineering: The art of approving a 1000-line PR you did not read, written by an agent, reviewed by another agent... merged by a human who just wants to go to lunch.*

![khang toh ops is still real production doesnt care human or agent](Attachments/cds26-khang-toh-ops-is-still-real-production-doesnt-care-human-or-agent.jpg)

> **Production Reality**: *Ops is still a real thing. Production does not care whether the change came from human or agent. We still need telemetry, ownership, rollback, incident response, and recovery.*

![khang toh ai moved the bottleneck dora metrics table](Attachments/cds26-khang-toh-ai-moved-the-bottleneck-dora-metrics-table.jpg)

> **The DORA Metrics Inversion**: *2026: AI moved the bottleneck — AI compressed lead time. The bottleneck moved downstream, from writing code to verification and operability. High deployment frequency with rising change failure rate is not victory.*

![khang toh ai generates code tests prs releases speed](Attachments/cds26-khang-toh-ai-generates-code-tests-prs-releases-speed.jpg)

> **Machine Velocity Across the Pipeline**: AI generates code in seconds, tests in minutes, continual pull requests, agent-managed infrastructure, and higher release frequencies. *The downstream inquiry: Can we understand, support, recover and improve what we ship?*

![khang toh where does your factory lane end missing layer](Attachments/cds26-khang-toh-where-does-your-factory-lane-end-missing-layer.jpg)

> **The Factory Boundary**: *Everyone's building the factory that delivers the software. But where does your factory lane end? The missing layer is not another agent. It is product operability.*

![khang toh user surface vs operating surface rodin](Attachments/cds26-khang-toh-user-surface-vs-operating-surface-rodin.jpg)

> **The Fundamental Duality (Rodin's Thinker)**: *Most products expose a user surface. AI Operable Products expose the operating surface for humans + AI.*

![khang toh user surface vs ai operable surface comparison](Attachments/cds26-khang-toh-user-surface-vs-ai-operable-surface-comparison.jpg)

> **Surface Comparison**: *User Surface (Built for Humans)* vs *AI Operable Surface (Built for Humans + AI)*.

![khang toh ai operable product 7 primitives](Attachments/cds26-khang-toh-ai-operable-product-7-primitives.jpg)

> **The Operational Blueprint**: *AI Operable Product — 7 Primitives*: Outcome Intent, Journey Context, Workflow Map, Recovery Path, Policy Boundary, Safe Actions, and Feedback Loop.

![khang toh payments 2026 expects in seconds flow](Attachments/cds26-khang-toh-payments-2026-expects-in-seconds-flow.jpg)

> **Case Study · Real-Time Payments**: *Payments in 2026 expects in seconds. Customers expect to know whether the money arrived, whether it is available, and what happens next.* (Initiate $\to$ Validate $\to$ Route $\to$ Process $\to$ Confirm).

![khang toh fednow instant payments architecture](Attachments/cds26-khang-toh-fednow-instant-payments-architecture.jpg)

> **High-Velocity Architecture**: FedNow reserve bank settlement network connecting Sender FI, Service Providers, and Receiver FI within seconds.

![khang toh 30 minute impact 3000 attempts exposure](Attachments/cds26-khang-toh-30-minute-impact-3000-attempts-exposure.jpg)

> **The Cost of Downtime**: *The impact of a 30-minute degraded route or service: 100 failures/min $\times$ 30 min = 3,000 attempts exposed. Exposure is not a ticket count.*

![khang toh old vs ai operable definition of done](Attachments/cds26-khang-toh-old-vs-ai-operable-definition-of-done.jpg)

> **The Paradigm Shift**: *" 'It works' used to be an implementation milestone. The software factory needs AI Operable Primitives."* Comparing the *OLD Definition of Done* against the *AI Operable Definition of Done*.

![khang toh ai operable product claude code skill](Attachments/cds26-khang-toh-ai-operable-product-claude-code-skill.jpg)

> **Live Tooling · Claude Code Skill**: Running `ai-operable-product` inside Claude Code CLI (`v2.1.300`), reconstructing production state across distributed MCP evidence sources and evaluating journeys against the 7 primitives.

![khang toh agentic digital factory build run operate phases](Attachments/cds26-khang-toh-agentic-digital-factory-build-run-operate-phases.jpg)

> **The Agentic Digital Factory**: 3 continuous lifecycle phases — **Build** (automated feature synthesis, Jira PRDs, technical docs), **Run** (continuous deployment across GCP, MongoDB, real-time observability & SLO tracking), and **Operate** (agent-led ops, incident triage, SlackOps chat actions, automated recipe execution inside sandbox guardrails).

![khang toh agentic digital factory 5 pillars architecture](Attachments/cds26-khang-toh-agentic-digital-factory-5-pillars-architecture.jpg)

> **The 5 Pillars of the Agentic Digital Factory**: CodeFactory (Build Product / Agentic Feature Engine), CodeWiki (Knowledge Product / Live Architecture Graph), Brains (AI Core / Reasoning & Context RAG), Automation (Automation Product / Event-Driven Workflow Engine), and SlackOps (Operations Product / Human-in-the-Loop ChatOps) — underpinned by Sandbox & Guardrails.

![khang toh codewiki live architecture graph](Attachments/cds26-khang-toh-codewiki-live-architecture-graph.jpg)

> **CodeWiki · Knowledge Product**: Live architecture graph indexing system topology, cross-service dependencies, and API specifications across 64 repositories.

![khang toh codefactory autonomous feature creation](Attachments/cds26-khang-toh-codefactory-autonomous-feature-creation.jpg)

> **CodeFactory · Build Product**: Autonomous feature creation based on Jira, automated PR code reviews, and proactive repository maintenance.

![khang toh agentic digital factory system architecture topology](Attachments/cds26-khang-toh-agentic-digital-factory-system-architecture-topology.jpg)

> **Agentic Digital Factory System Architecture**: Deep topology spanning React 19 / TypeScript 5.9 / Vite 7 SPA, Nginx Web Gateway, FastAPI / Python 3.13 API Service, Semantic Router with BGE CPU embeddings, PostgreSQL + pgvector, Kotlin 2.2 / Ktor 3 / JVM 21 Runtime Control Plane, OpenHands Agent Server v1.27.1, and Docker / Kubernetes runtime backend.

![khang toh brains multi agent orchestrator ui](Attachments/cds26-khang-toh-brains-multi-agent-orchestrator-ui.jpg)

> **Brains UI · Multi-Agent Orchestrator**: Audience-scoped knowledge layer available to humans and Wayang sessions with Context RAG across 28 authorized knowledge spaces, 86 admitted sources, and granular policies (`Restrictive` for Product Docs and Engineering Playbook, `Balanced` for Customer Support).

![khang toh automations operational blueprints ui](Attachments/cds26-khang-toh-automations-operational-blueprints-ui.jpg)

> **Automations UI · Operational Blueprints & Recipes**: Turning events from Jira, GitHub, Slack, Confluence, and MongoDB into governed agent sessions (1,248 total runs, 97.6% success rate, 256 queue pressure) executing tasks like *CodeWiki daily refresh* (5m 15s), *Slack weekly digest* (2m 45s), and *MR review reminders*.

![khang toh slackops incident anomaly detection](Attachments/cds26-khang-toh-slackops-incident-anomaly-detection.jpg)

> **SlackOps · Incident Anomaly Detection**: `ticket-ops-agent` detects an anomaly (+300% ticket velocity threshold exceeded on Zendesk/Freshdesk for QR Checkout service, payments stuck on `PENDING`), automatically creates the incident channel `#inc-qr-payments`, and alerts the on-call engineer (Alex Kim).

![khang toh slackops autonomous rca mongodb collscan](Attachments/cds26-khang-toh-slackops-autonomous-rca-mongodb-collscan.jpg)

> **SlackOps · Autonomous Root Cause Analysis (RCA)**: `product-agent` maps the entire QR checkout dependency graph and pinpoints 94% of latency to `payment-wallet-api` executing an unindexed MongoDB collection scan (`COLLSCAN` examining 2.8M docs per query on `db.pocket_mapping.find({ user_id: ..., status: "active" })`).

![khang toh slackops slo latency breach alert](Attachments/cds26-khang-toh-slackops-slo-latency-breach-alert.jpg)

> **SlackOps · Telemetry Correlation**: `obs-agent` confirms active SLO latency breach on `payment-wallet-api` endpoint `check_pocket_balance()` (p95 at 2,100ms vs SLA 150ms; p99 at 3,450ms vs SLA 200ms).

![khang toh slackops prebuilt index mr match](Attachments/cds26-khang-toh-slackops-prebuilt-index-mr-match.jpg)

> **SlackOps · Automated Remediation Match**: `ops-agent` cross-references the RCA with repository MRs and discovers that the scheduled 3:00 AM Atlas Advisor automation already created GitLab MR #402 (`db.pocket_mapping.createIndex({ user_id: 1, status: 1, created_at: -1 }, { background: true })`), marked `[READY TO MERGE]`.

![khang toh slackops human approval mr merged complete](Attachments/cds26-khang-toh-slackops-human-approval-mr-merged-complete.jpg)

> **SlackOps · Human Approval & Background Migration**: On-call engineer Alex Kim reviews and confirms MR #402; GitLab Integration merges into `main` and triggers background database index build on MongoDB Atlas Cluster 01 (`Index status: BUILD_COMPLETE`).

![khang toh thank you contact qr code](Attachments/cds26-khang-toh-thank-you-contact-qr-code.jpg)

> **Closing & Resources**: Khang Toh (`fdeploy.ai`, LinkedIn `/in/khangtoh`), featuring `labs.formative.ai/ai-operable-product` Claude and ChatGPT skills.

---

## 📌 Context & Problem Statement: The AI Velocity Trap

With modern LLM coding agents, copilots, and software factories (like those discussed in [[When Tokens Stop Being the Bottleneck - Operating Agentic Software Factories (Carl Ross)]]), teams can generate features at an unprecedented rate. However, **shipping code is not the same as shipping an operable product**.

```mermaid
flowchart LR
    subgraph TheVelocityTrap["The AI Velocity Trap"]
        VibeCode["High-Speed AI Code Generation<br/>(PRs / Features drafted in minutes)"]
        MergeSprawl["Unprecedented Feature Sprawl<br/>(Complex distributed state)"]
        BlackBoxCrash["Production Outages & Drift<br/>(Neither humans nor AI understand system state)"]
    end

    subgraph TheOperableProduct["The AI Operable Paradigm"]
        Reconcile["Continuous Reconciliation Loops<br/>(Desired State vs Actual State)"]
        AgentTelemetry["Agent-Parsable Telemetry<br/>(Structured machine-readable logs & traces)"]
        BlastRadius["Contained Blast Radiuses<br/>(Self-healing primitives & granular rollbacks)"]
    end

    VibeCode --> MergeSprawl --> BlackBoxCrash
    TheVelocityTrap -.->|Shift Focus To| TheOperableProduct
```

### The Shift from Code Generation to Day-2 Operability
- **The Core Dilemma**: Anyone can generate a feature with AI in 10 minutes. But who diagnoses it at 3:00 AM on Saturday? 
- **The Dual-User Problem**: Tomorrow's software has **two classes of operational users**:
  1. **Human SREs / Operators**: Who need intuitive mental models, clean dashboards, and clear blast-radius boundaries.
  2. **Autonomous Agents / Healing Loops**: Who need machine-actionable APIs, deterministic state reconciliation, structured JSON/MCP diagnostics, and safe rollback actuators.
- When products are engineered solely for human UI clicks or generated without operability in mind, AI agents cannot repair them, and humans are overwhelmed by the volume of machine-generated code.

---

## ⚙️ Core Architectural Principles of AI Operable Products

```mermaid
flowchart TD
    subgraph OperabilityPillars["Pillars of AI Operable Systems"]
        Pillar1["<b>1. Declarative Self-Healing</b><br/>Kubernetes-style controllers over imperatively generated scripts"]
        Pillar2["<b>2. Dual-Channel Observability</b><br/>Human dashboards + LLM/Agent actionable diagnostic traces"]
        Pillar3["<b>3. Semantic Blast Radius</b><br/>Guaranteed rollback checkpoints, feature gates, and circuit breakers"]
        Pillar4["<b>4. Machine-Readable Contracts</b><br/>Strict OpenAPI/MCP schemas for every operational interface"]
    end
```

---

## 🏛️ The Evolutionary Pattern: 2000 to 2026

Khang Toh walked the room through 26 years of software engineering history to demonstrate that the current AI wave is not an unprecedented rupture, but rather the fifth iteration of an unbroken historical pattern: **shrinking the distance between writing software and knowing whether it worked**.

```mermaid
flowchart LR
    E1["<b>1. Pre-2000: Waterfall</b><br/>• Phase gates<br/>• Requirements first<br/><i>'Finish the phase'</i>"]
    E2["<b>2. 2001–2009: Agile / XP</b><br/>• Sprints & user stories<br/>• TDD / Pair programming<br/><i>'Ship small'</i>"]
    E3["<b>3. 2009–2015: DevOps / CI-CD</b><br/>• Build-test-deploy automation<br/>• Continuous delivery<br/><i>'Deploy continuously'</i>"]
    E4["<b>4. 2015–2022: SRE / Platform</b><br/>• SLOs & error budgets<br/>• Distributed tracing<br/><i>'Observe production'</i>"]
    E5["<b>5. 2023–2026: AI-Native Dev</b><br/>• Autonomous coding agents<br/>• Software factories<br/><i>'Direct agents'</i>"]

    E1 --> E2 --> E3 --> E4 --> E5
```

### The 5 Eras of Modern Software Delivery

| Era | Timeline | Dominant Movement | Primary Mechanisms | Cultural Mandate | How the Feedback Loop Shortened |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **1** | **Pre-2000** | **Waterfall** | Phase gates, sign-offs, rigid specs, quarterly releases | *"Finish the phase"* | Months to years between writing requirements and seeing software run in production. |
| **2** | **2001–2009** | **Agile / XP** | 2-week sprints, user stories, Test-Driven Development (TDD), pair programming | *"Ship small"* | Shortened validation from months to 2-week sprint boundaries. |
| **3** | **2009–2015** | **DevOps / CI-CD** | Automated unit tests, container builds (Docker), continuous integration & delivery | *"Deploy continuously"* | Shortened verification from weeks to minutes via automated build/test pipelines. |
| **4** | **2015–2022** | **SRE / Platform / Observability** | Service Level Objectives (SLOs), distributed tracing, OpenTelemetry, error budgets, blameless postmortems | *"Observe production"* | Moved feedback directly into live runtime behavior—measuring production health in seconds. |
| **5** | **2023–2026** | **AI-Native Dev & Agentic Engineering** | Autonomous coding agents (Claude Code, Cursor, Codex), LLM software factories, automated PR synthesis | *"Direct agents"* | Code authoring compressed from hours to seconds—agents write virtually all new code. |

---

## 🔄 The Invariable Pattern: Shrinking the Gap Between Dev & Operating

```mermaid
flowchart LR
    LP["<b>LEARN + PLAN</b><br/>Requirements, code, change"]
    B["<b>BUILD</b><br/>CI, tests, packages"]
    S["<b>SHIP</b><br/>Release, deploy"]
    O["<b>OPERATE</b><br/>Metrics, traces, incidents"]

    LP --> B --> S --> O
    O -.->|Continuous Real-Time Feedback| LP
```

> **The Core Thesis**: *"Every movement moved the feedback loop closer to the work. We did not just automate away toil. Every cycle — the loop got faster. But Ops did not disappear. Every era shortened the distance between writing software and knowing whether it worked."*

### Why Ops Does Not Disappear in the Agentic Era
1. **The Asymmetry of Generation vs Operability**:
   - In 2026, an agent can draft an entire microservice in 45 seconds.
   - But if that microservice misbehaves in production, crashes under load, or leaks data, someone (or something) still has to triage, reconcile, and restore it.
2. **The "Who Fixes It at 3:00 AM?" Litmus Test**:
   - Shipping features with AI is easy.
   - Operating those features requires Day-2 operational primitives: semantic health checks, structured audit trails, blast-radius containment, and self-healing reconciliation loops.
3. **Connecting to Kelsey Hightower's Law**:
   - Directly echoes Kelsey's statement from earlier today ([[Fireside Chat with Kelsey Hightower & Geet Bhanawat]]): *"Technology is not going to save you... fix the underlying thing. AI is just another workload."*

---

## 🛡️ Enterprise Agentic Infrastructure: Inside fdeploy

Khang Toh introduced **fdeploy** as a reference control plane designed to bring applied AI and agentic engineering under enterprise operational governance:

```mermaid
flowchart TD
    subgraph EnterpriseGovernance["fdeploy: Enterprise Agentic Control Plane"]
        subgraph P1["FAgent"]
            AgentTools["Coding Tools Engineers Already Use<br/>(Claude Code, Cursor, CLI, Sandboxes)"]
        end
        subgraph P2["FIdentity"]
            Auth["Trusted Identity for People & Agents<br/>(Enterprise SSO, mTLS, SPIFFE)"]
        end
        subgraph P3["FGateway"]
            Gate["Model Access, Request Routing,<br/>Token Metering & Cost Attribution"]
        end
    end

    Devs["Developers & Platform Engineers"] --> P1
    P1 --> P2
    P2 --> P3
    P3 --> LLM["Enterprise Models & Sovereign Inference Clusters"]
```

### The 3 Pillars of fdeploy

1. **FAgent (Tool & Sandbox Integration)**:
   - Integrates the coding tools engineers already use on local developer desktops and in secure Kubernetes/microVM sandboxes.
   - Bridges disparate agent interfaces without forcing engineers to adopt proprietary IDEs or isolated web portals.
2. **FIdentity (Federated Agent Identity)**:
   - Solves the critical security question: *Who is running this agent?*
   - Establishes cryptographically verified identities for both human engineers and autonomous agents using enterprise SSO and sign-in.
   - Prevents unauthenticated rogue agents from assuming unauthorized privileges or accessing sensitive repositories.
3. **FGateway (Model Routing & Cost Attribution)**:
   - Centralizes enterprise model access with intelligent routing, latency budgeting, and fallback logic.
   - Attributes token usage, operational costs, and audit logs directly to specific teams, projects, and autonomous agent jobs (connecting directly to [[Lessons from Operating an Internal LLM Gateway for Production Agentic Applications (Zhong Liang Ong & Yek Khan)]]).

---

## 🪢 2026: The Rise of Harness Engineering & Loop Engineering

Khang Toh highlighted a seismic shift in how software engineering is conceptualized in 2026:

```mermaid
flowchart TD
    subgraph TheHarness["The Agent Harness (System Wrapper)"]
        Context["<b>Context</b><br/>Repo graphs, schema, runtime state"]
        Tools["<b>Tools</b><br/>Sandboxed MCP execution, compiler, linter"]
        Verification["<b>Verification</b><br/>Automated tests, property checks"]
        Gates["<b>Gates</b><br/>Security approvals, policy boundary checks"]
        Policy["<b>Policy</b><br/>Token budgets, forbidden paths, least-privilege"]
        Feedback["<b>Feedback</b><br/>Compiler errors, test diffs, trace logs"]
    end

    Model["<b>Frontier LLM / Agent Core</b><br/>(Generates token proposals)"]

    Model --> TheHarness
    TheHarness --> Model
```

> **The Fundamental Axiom**:  
> *"The developer is no longer only human.*  
> *The model writes. The harness decides whether the goal was met."*

### Moving Beyond Vibe Coding
- **Prompt Engineering (2023)**: Tweaking text instructions, zero-shot system prompts, and formatting hints.
- **Vibe Coding (2024–2025)**: Developers casually typing English descriptions into IDEs, accepting suggestions by intuition without deep verification.
- **Harness Engineering & Loop Engineering (2026)**:
  - Engineering the deterministic outer harness: the sandbox execution environment, the automated test harness, the feedback loop routing, and the verification gates.
  - The model provides probabilistic candidate diffs; the harness rigorously filters, evaluates, and verifies them against ground truth before anything reaches a repository.
  - *(Connects directly to *The Road Under the Harness (Ng Shangru)* and *AI Agent Engineering*!)*

---

## 🚨 The "LGTM Engineering" Pathology

Khang Toh called out the greatest unspoken operational failure of AI-generated codebases: **LGTM Engineering**.

> **"NOT JOKE! REAL PROBLEM!"**  
> **LGTM Engineering**: *"The art of approving a 1000-line PR you did not read, written by an agent, reviewed by another agent... merged by a human who just wants to go to lunch."*

### Why the Review Layer Collapses Under Agentic Velocity
1. **The Review Bottleneck**: Humans read code at roughly 200–400 lines per hour. Agents write 1,000 lines in 30 seconds.
2. **False Sense of Security**: When an AI review bot (e.g., automated PR summary agent) posts a plausible-sounding green checkmark, the human approver suffers cognitive fatigue and merges the PR without understanding the architectural implications.
3. **Ghost Code in Production**: When code that no single human has deeply read or understood enters production, the cognitive link between intent and implementation is severed.

---

## 📊 2026: AI Moved the Bottleneck (The DORA Metrics Inversion)

AI has drastically compressed lead time. However, by solving the code synthesis bottleneck, it has simply pushed the real bottleneck downstream: **into verification and operability**.

| DORA Metric | Trend in Agentic Era | Why it Happens | Strategic Implication |
| :--- | :---: | :--- | :--- |
| **Deployment Frequency** | **UP** ⬆️ | AI helps generate and ship code changes at unprecedented speed. | Raw deployment volume increases exponentially. |
| **Lead Time** | **LESS** ⬇️ | The plan $\to$ write $\to$ build loop is compressed from days to minutes. | Code reaches the merge gate faster than ever before. |
| **Change Failure Rate** | **UP** ⬆️ | Production incidents caused by subtle AI-generated hallucinations, edge cases, and architectural drift rise sharply. | Systems become fragile and prone to cascading failures. |
| **MTTR (Mean Time to Restore)** | **WORSE** ⚠️ | **Harder to explain "why" when no human owns the reasoning** behind the original diff. | Triage takes dramatically longer because engineers must reverse-engineer agent logic during an outage. |
| **TOIL** | **MOVED** 🔄 | Toil has shifted from *writing boilerplate* to *reviewing, auditing, and proving trust*. | Engineers spend all their mental bandwidth validating machine output rather than solving domain problems. |

> **The Executive Warning**:  
> *"High deployment frequency with rising change failure rate is not victory."*

---

## 🛠️ Production Reality: Ops is Still a Real Thing

> *"Production does not care whether the change came from a human or an agent."*

Whether written by a junior developer, an SRE principal, or an autonomous LLM swarm, production infrastructure behaves according to immutable laws of physics and systems engineering:

```mermaid
flowchart LR
    Change["Code Change / Deployment"] --> Prod["Production Workload"]
    Prod --> M1["<b>Telemetry</b><br/>Metrics, traces, structured logs"]
    Prod --> M2["<b>Ownership</b><br/>Who authored & who is accountable?"]
    Prod --> M3["<b>Rollback</b><br/>Instant safe retreat to known good state"]
    Prod --> M4["<b>Incident Response</b><br/>Automated runbooks & alert triage"]
    Prod --> M5["<b>Recovery</b><br/>Reconciling actual state to desired state"]
```

1. **Telemetry**: We must provide rich, machine-parsable traces so both human operators and diagnostic agent loops can parse causal error graphs.
2. **Ownership**: Every automated agent execution must trace back to a verifiable human identity and team ownership record.
3. **Rollback**: Fast, deterministic rollback mechanisms (git reverts, container rollbacks, feature flag kills) must exist before code hits production.
4. **Incident Response & Recovery**: Operating products requires active reconciliation loops rather than static fire-and-forget code drops.

---

## 🏭 Where Does Your Factory Lane End? The Missing Layer

Everyone in 2026 is racing to build the upstream factory that delivers software (connecting directly to [[When Tokens Stop Being the Bottleneck - Operating Agentic Software Factories (Carl Ross)]]):

```mermaid
flowchart LR
    P["<b>PLAN</b>"] --> Sp["<b>SPEC</b>"] --> B["<b>BUILD</b>"] --> V["<b>VERIFY</b>"] --> D["<b>DEPLOY</b>"]
    D -->|SHIP| Prod["<b>PRODUCTION</b><br/>• Customer journeys?<br/>• Business outcomes?<br/>• Failures & reconciliation?<br/>• Support & recovery?<br/>• Learning & improvement?"]
```

> **The Fundamental Warning**:  
> *"Everyone's building the factory that delivers the software. But where does your factory lane end?*  
> **The missing layer is not another agent. It is product operability."**

- **The Upstream Mirage**: Generating code in seconds, tests in minutes, continual pull requests, and automated infra configs gives the illusion of immense productivity.
- **The Downstream Question**: *Can we understand, support, recover, and improve what we ship?*
- If the factory abruptly ends at the `SHIP` line, production becomes an unmonitored graveyard of AI-generated complexity.

---

## 🎭 User Surface vs. AI Operable Surface

> *"Most products expose a user surface. AI Operable Products expose the operating surface for humans + AI."*

```mermaid
flowchart TD
    subgraph Traditional["User Surface (Built for Humans)"]
        US1["Screens & Web/Mobile Interfaces"]
        US2["End-User CRUD APIs"]
        US3["Direct User Interactions"]
        US4["Customer Workflows"]
        US5["Standard Happy Paths"]
    end

    subgraph Operable["AI Operable Surface (Built for Humans + AI)"]
        OS1["<b>Intent</b>: Business outcome goals"]
        OS2["<b>Journey Context</b>: End-to-end scope"]
        OS3["<b>Workflow Semantics</b>: Ordering & logic"]
        OS4["<b>Recovery Paths</b>: Failure handling & fallback"]
        OS5["<b>Policy Boundaries</b>: Authority & guardrails"]
        OS6["<b>Safe Actions</b>: Reversible & sandboxed"]
        OS7["<b>Feedback Loops</b>: Continuous outcome reporting"]
    end
```

| Dimension | 👤 User Surface (Built for Humans) | 🤖 AI Operable Surface (Built for Humans + AI) |
| :--- | :--- | :--- |
| **Primary Audience** | Human end-users clicking buttons or consuming public endpoints. | Both human SREs and autonomous AI agents operating the system. |
| **Core Abstraction** | Screens, UI components, forms, and standard happy-path workflows. | Structured intents, semantic dependencies, and recovery graphs. |
| **Failure Handling** | Generic error dialogs or static HTTP 500 status codes. | Explicit **Recovery Paths**, automated fallback actions, and state rollbacks. |
| **Authority & Scope** | Session cookies and end-user OAuth tokens. | Machine-verifiable **Policy Boundaries** dictating least-privilege authority. |
| **Action Safety** | Unrestricted CRUD operations requiring manual DBA/SRE repair on mistake. | Categorized **Safe Actions**: explicitly classified as *reversible*, *sandboxed*, or *human-confirmed*. |
| **Evolution** | Static dashboards built from business data warehouses. | Closed **Feedback Loops** feeding outcome validation into operational telemetry. |

---

## 🧩 The 7 Primitives of an AI Operable Product

To turn high-speed AI code generation into sustainable enterprise operations, products must implement the **7 Core Primitives**:

```mermaid
flowchart TD
    P1["<b>01 Outcome Intent</b><br/>Define business goal, not button clicks"]
    P2["<b>02 Journey Context</b><br/>End-to-end customer journey map"]
    P3["<b>03 Workflow Map</b><br/>Sequence, dependencies & ordering"]
    P4["<b>04 Recovery Path</b><br/>Failure & escalation handling"]
    P5["<b>05 Policy Boundary</b><br/>Hard guardrails & authority limits"]
    P6["<b>06 Safe Actions</b><br/>Reversible vs sandboxed vs human approval"]
    P7["<b>07 Feedback Loop</b><br/>Telemetry feeding outcome improvement"]

    P1 --> P2 --> P3 --> P4
    P4 --> P5 --> P6 --> P7
```

### 1. Outcome Intent (Business Outcome Goals)
- **Definition**: Defines the specific business outcome a workflow must produce, rather than merely specifying which UI button to click or endpoint to call.
- **Current Industry State**: *No standard exists today*. Most companies build this in reverse through static dashboards queried from business data warehouses long after production incidents occur.

### 2. Journey Context (End-to-End Scope)
- **Definition**: Maps where the current action sits within the overarching customer or user journey.
- **Current Industry State**: *Partial / Skills*. Exists partially in developer system prompts or localized agent tool descriptions, but lacks cohesive cross-service lineage.

### 3. Workflow Map (Dependencies & Ordering)
- **Definition**: Establishes explicit sequence, causal dependencies, and ordering required to reach the target goal.
- **Current Industry State**: *Partial (PRDs / Diagrams)*. Exists as static architecture diagrams in Figma or Confluence rather than runtime-enforceable machine contracts.

### 4. Recovery Path (Failure & Escalation Handling)
- **Definition**: Specifies what happens when a step fails mid-execution, what automated fallback action to execute, and how to safely hand off to a human engineer.
- **Why It Matters**: Prevents agentic swarms from entering infinite retry loops, compounding database corruption, or silently halting without alerts.

### 5. Policy Boundary (Authority & Hard Guardrails)
- **Definition**: Dictates what an agent is strictly forbidden from doing and specifies who possesses the authority to modify or override constraints.
- **Why It Matters**: Hard boundaries cannot be prompt-engineered away by clever jailbreaks; they are enforced deterministically at the kernel/gateway level.

### 6. Safe Actions (Sandboxing & Human Confirmation)
- **Definition**: Categorizes every possible operational action into:
  1. **Reversible**: Can be executed autonomously without human gatekeeping (e.g., clearing a local cache).
  2. **Sandboxed**: Executed inside ephemeral microVMs/containers with zero host blast radius.
  3. **Human-in-the-Loop Required**: Destructive or irreversible state changes (e.g., dropping a table, modifying production routing).

### 7. Feedback Loop (Continuous Outcome Reporting)
- **Definition**: Feeds outcome validation directly into operational telemetry so autonomous agents and platform engineers continuously improve system accuracy.
- **The Ultimate Payoff**: Closes the loop between Day-1 code synthesis and Day-2 self-healing operability.

---

## 💳 Real-World Case Study: Real-Time Payments in 2026 (FedNow)

To illustrate why operability is non-negotiable in the AI era, Khang Toh examined modern high-velocity financial payment networks (e.g., **FedNow / Real-Time Payments**):

```mermaid
sequenceDiagram
    autonumber
    participant C as Customer (Sender)
    participant S_FI as Sender Bank
    participant FN as FedNow Service (Reserve Banks)
    participant R_FI as Receiver Bank
    participant R as Receiver (Customer)

    C->>S_FI: 1. Initiate & authorize payment instruction
    S_FI->>S_FI: 2. Validate funds, account limits & controls
    S_FI->>FN: 3. Partner Route: submit payment message
    FN->>FN: 4. Interbank Settlement (Master/Correspondent Accts)
    FN->>R_FI: 5. Network Process: credit notification
    R_FI->>R: 6. Make funds immediately available (< seconds)
    R_FI-->>FN: 7. Acknowledgment
    FN-->>S_FI: 8. Confirmation
    S_FI-->>C: 9. Confirm: update ledger & notify sender
```

### The Anatomy of a 30-Minute Outage
In a real-time payment network where customers expect money to arrive and be available in seconds:
- **100 intermittent payment failures per minute** occur on an impacted route.
- It takes **30 minutes** for monitoring systems and operators to identify the degraded route and suspend new submissions.
- **Result**: **3,000 customer payment attempts are exposed to the disruption**.
- **The Operational Epigram**:  
  > *"100 attempts per minute for 30 minutes.*  
  > **Exposure is not a ticket count."**
- In modern software, customer friction happens in seconds. If an autonomous agent shipped the code that caused the routing glitch, but the system lacked **Journey Context** and **Recovery Paths**, the support queue is flooded before SREs even open their laptops.

---

## 🎯 The "Definition of Done" Evolution

Khang Toh argued that software engineering must redefine what it means for a task to be complete:

> *" 'It works' used to be an implementation milestone.*  
> **The software factory needs AI Operable Primitives."**

```mermaid
flowchart LR
    Old["<b>OLD Definition of Done</b><br/>(Implementation Milestones)"]
    New["<b>AI Operable Definition of Done</b><br/>(Operational Guarantees)"]

    Old -->|Must Evolve Into| New
```

| ❌ OLD Definition of Done (Implementation Only) | ✅ AI Operable Definition of Done (Operational Reality) |
| :--- | :--- |
| **Code compiles** | Outcome **measurable** *(Did the business goal succeed?)* |
| **Tests pass** | Journey **observable** *(Can we trace end-to-end user state?)* |
| **PR merged** | Failure **explainable** *(Can we determine why it broke?)* |
| **CI + Deployment succeeds** | Recovery **designed** *(Is there an automated rollback/fallback path?)* |
| **Feature flag enabled** | Actions **governed** *(Are blast radiuses bounded & policies enforced?)* |
| — | Support **enabled** *(Can frontline operators triage the issue?)* |
| — | Learning **feeds back** *(Does outcome telemetry improve future agents?)* |

---

## 🤖 Practical Implementation: The `ai-operable-product` Claude Skill

Khang Toh showcased a working, open-source reference tool designed as a native **Claude Skill** running inside the **Claude Code CLI** (`v2.1.300`):

```bash
# Invoking the AI Operable Product skill inside Claude Code
> How can I use AI Operable Product?

# Claude Code inspects the local skill directory:
# .claude/skills/ai-operable-product/SKILL.md
```

### The Inspection Protocol
The skill enforces strict operational discipline before allowing AI agents to diagnose production issues:
1. **Refuses Open-Ended Prompts**: The skill explicitly refuses to run without a named business journey (e.g. `Digital Lending - Personal Loan Application` or `Treasury - Real-Time Interbank Settlement`).
2. **Discovers Connected Evidence Sources**: Builds a dynamic capability map across connected Model Context Protocol (MCP) servers, databases, logs, and APM tools without requiring hardcoded database credentials.
3. **Traces Correlation Identifiers**: Follows transaction IDs, application IDs, and distributed trace IDs across disparate microservices.
4. **Reconstructs Product State**: Keeps *expected state*, *implemented state*, and *actual production state* completely separate to locate drift.
5. **Scores the 7 Primitives**: Systematically grades the journey against the AI-Operable Done criteria: `PASS`, `PARTIAL`, `FAIL`, or `UNKNOWN`.
6. **Delivers Prioritized Remediation**: Outputs a structured diagnostic report with confidence bounds, highlighted unknowns, and safe-action recommendations.

---

## 🏭 The Agentic Digital Factory Architecture

Khang Toh unveiled the reference architecture of the **Agentic Digital Factory**, illustrating how an enterprise bridges autonomous code generation with resilient Day-2 production operations.

```mermaid
flowchart LR
    subgraph BuildPhase["1. BUILD PHASE (CodeFactory)"]
        Jira["Jira PRD / Tickets"] --> Synth["Automated Feature Synthesis"]
        Synth --> PR["Auto PR & Code Review"]
    end

    subgraph RunPhase["2. RUN PHASE (Deployment & Infra)"]
        CI["Continuous Delivery"] --> Cloud["GCP & MongoDB Deployment"]
        Cloud --> SLO["Real-Time SLOs & Observability"]
    end

    subgraph OperatePhase["3. OPERATE PHASE (SlackOps & Automation)"]
        Alert["Incident Signals"] --> Triage["Agent-Led Ops & Triage"]
        Triage --> Recipe["Automated Recipe Execution"]
        Recipe --> Human["SlackOps Human-in-the-Loop"]
    end

    BuildPhase --> RunPhase --> OperatePhase
    OperatePhase -.->|Continuous Feedback Loop| BuildPhase
```

### The 3 Lifecycle Phases
1. **Build Phase (CodeFactory)**:
   - Automated feature synthesis tied directly to Jira tickets, PRDs, specs, and living architectural documentation.
   - Code authoring, automated PR generation, comprehensive unit/integration test synthesis, and multi-agent peer reviews.
2. **Run Phase (Continuous Delivery & Infrastructure)**:
   - Automated deployment across cloud providers (GCP, MongoDB clusters) with instant rollbacks.
   - Live telemetry, structured OpenTelemetry tracing, and real-time Service Level Objective (SLO) tracking.
3. **Operate Phase (SlackOps & Guarded Automation)**:
   - Agent-led operations, causal incident triage, SlackOps chat interactions, and automated recipe execution inside sandbox guardrails.

---

### 🏛️ The 5 Pillars of the Agentic Digital Factory

The factory is organized into five specialized, decoupled product layers, all anchored by a foundational guardrail fabric:

```mermaid
flowchart TD
    subgraph FivePillars["The 5 Core Pillars"]
        direction TB
        subgraph Col1["Build & Knowledge"]
            CF["<b>CodeFactory</b><br/><i>Build Product / Agentic Feature Engine</i><br/>• Autonomous feature creation (Jira)<br/>• Automated code reviews<br/>• Proactive repository maintenance"]
            CW["<b>CodeWiki</b><br/><i>Knowledge Product / Live Architecture Graph</i><br/>• Indexes system topology & RPC schemas<br/>• Cross-service dependency maps<br/>• 64+ repositories dynamically tracked"]
        end

        subgraph Col2["Core Intelligence"]
            Brains["<b>Brains</b><br/><i>AI Core / Reasoning & Context RAG</i><br/>• Multi-agent orchestrator<br/>• Composable domain hierarchies<br/>• Unified Context RAG across all layers"]
        end

        subgraph Col3["Operations & Workflows"]
            Auto["<b>Automation</b><br/><i>Automation Product / Workflow Engine</i><br/>• Executes operational blueprints & recipes<br/>• Scheduled maintenance tasks<br/>• Dynamic scale adjustment hooks"]
            SO["<b>SlackOps</b><br/><i>Operations Product / Human-in-the-Loop</i><br/>• Real-time business & product signals<br/>• Interactive command execution<br/>• One-click human approval gates"]
        end
    end

    subgraph Foundation["Foundational Layer: Sandbox & Guardrails"]
        SG["Strict Permissions • Validation Rules • Isolated MicroVM/Container Boundaries • Least-Privilege Execution"]
    end

    Col1 --> Foundation
    Col2 --> Foundation
    Col3 --> Foundation
```

| Pillar | Category | Core Responsibilities & Capabilities |
| :--- | :--- | :--- |
| **CodeFactory** | **Build Product**<br>*(Agentic Feature Engine)* | Autonomous feature creation based on Jira tickets; automated PR generation; automated multi-agent code reviews; proactive repository health and tech debt maintenance. |
| **CodeWiki** | **Knowledge Product**<br>*(Live Architecture Graph)* | Continuously indexes system topology, cross-service dependencies, and API specifications across repositories (e.g. 64+ microservice repos). Eliminates stale documentation by keeping a living, queriable knowledge graph. |
| **Brains** | **AI Core**<br>*(Reasoning & Context RAG)* | Multi-agent reasoning orchestrator executing Context RAG across all context layers (code, schemas, live metrics, policies); composable to mirror product domains and organizational structures. |
| **Automation** | **Automation Product**<br>*(Event-Driven Workflow Engine)* | Executes operational blueprints, runbook recipes, scheduled background tasks, and dynamic autoscaling hooks strictly inside sandbox guardrails. |
| **SlackOps** | **Operations Product**<br>*(Human-in-the-Loop ChatOps)* | Surfaces real-time business and product signals directly into team channels; supports interactive slash commands, multi-agent status queries, and one-click human approvals. |
| **Sandbox & Guardrails** | **Foundational Substrate** | Enforces fine-grained permissions, deterministic validation rules, network egress policies, and isolated container execution boundaries across all agent activities. |

---

### 🖥️ Deep Dive: The Pillars in Production

#### 1. Brains: Audience-Scoped Knowledge for Humans & Wayang Sessions
- **Live Fleet Scale**: 28 authorized knowledge spaces, 86 admitted sources, and 5 active runs observing live production state.
- **Granular Access Policies**:
  - `Product Documentation` (Audience: *Internal*, Policy: *Restrictive*)
  - `Customer Support` (Audience: *Support Agents*, Policy: *Balanced*)
  - `Engineering Playbook` (Audience: *Engineers*, Policy: *Restrictive*)
- **Purpose**: Creates an evidence-based, continuously verified knowledge substrate so agents never hallucinate outdated architecture or unauthorized APIs.

#### 2. Automations: Turning Cloud Events into Governed Agent Sessions
- **Operational Health (30-Day Metrics)**:
  - **1,248 Total Runs** with a **97.6% Success Rate** (1,217 successful, 31 failed, 18 skipped).
  - Average execution duration: **2.8 minutes**; Queue pressure: **256**.
- **Automated Recipes in Flight**:
  - *CodeWiki Daily Refresh* (Active, runs in 5m 15s): Re-indexes ASTs, cross-service RPC contracts, and knowledge graph edges.
  - *Slack Weekly Digest* (Active, runs in 2m 45s): Aggregates cross-team alerts and updates for engineering channels.
  - *MR Review Reminder* (Paused, runs in 1m 10s): Prompts human and AI reviewers on lingering merge requests.

#### 3. SlackOps in Action: The QR Checkout Anomaly & Autonomous RCA
Khang Toh demonstrated a real-time production incident triage loop that showed how an AI Operable Product radically compresses Mean Time to Restore (MTTR) from hours to minutes:

```mermaid
sequenceDiagram
    autonumber
    participant Support as Zendesk / Freshdesk
    participant TicketAgent as ticket-ops-agent (AI Bot)
    participant Slack as #inc-qr-payments
    participant Dev as Alex Kim (On-Call Dev)
    participant ObsAgent as obs-agent (AI Bot)
    participant ProductAgent as product-agent (AI Bot)
    participant OpsAgent as ops-agent (AI Bot)
    participant GitLab as GitLab Integration (App)
    participant Mongo as Atlas Cluster 01 (MongoDB)

    Support->>TicketAgent: 10:14 AM: Ticket velocity spike (+300% / 15 tickets in 5m)
    TicketAgent->>Slack: ⚠️ Anomaly Alert: QR Payment stuck on "PENDING"
    TicketAgent->>Slack: Auto-creates channel #inc-qr-payments
    Dev->>Slack: 10:15 AM: "Acknowledged. Joining thread to investigate..."
    ObsAgent->>Slack: 10:16 AM: 🔔 Correlated SLO Latency Breach Alert
    Note over ObsAgent,Slack: payment-wallet-api: check_pocket_balance()<br/>p95: 2,100ms (SLA: 150ms) • p99: 3,450ms (SLA: 200ms)
    ProductAgent->>Slack: 10:18 AM: ✅ RCA & Journey Context Completed
    Note over ProductAgent,Slack: 94% latency localized in MongoDB execution<br/>db.pocket_mapping.find({ user_id, status: 'active' })<br/>Diagnostic: Unindexed COLLSCAN (examining 2.8M docs/query)
    OpsAgent->>Slack: 10:19 AM: ⚡ Pre-Built Index MR Match Found!
    Note over OpsAgent,Slack: 3:00 AM Atlas Advisor already created MR #402<br/>createIndex({ user_id: 1, status: 1, created_at: -1 }, { background: true })
    Dev->>Slack: 10:21 AM: "Reviewed MR #402! Confirmed background compound index. Merging now! 🚀"
    GitLab->>Mongo: 10:22 AM: MR #402 merged to main -> Atlas migration pipeline
    GitLab->>Slack: ✅ MR #402 Merged into main. Index status: BUILD_COMPLETE.
```

1. **Step 1: Automated Anomaly Detection (`ticket-ops-agent` @ 10:14 AM)**:
   - Monitors customer support ticketing velocity across Zendesk and Freshdesk.
   - Detects a **+300% ticket spike** (15 tickets in 5 minutes) on the QR Checkout service.
   - Root symptom: *QR Payment stuck on "PENDING"*.
   - Instantly spawns a dedicated incident channel `#inc-qr-payments` and alerts the on-call engineer.
2. **Step 2: Human Acknowledgment (`Alex Kim` @ 10:15 AM)**:
   - Human on-call dev joins the thread: *"Acknowledged. Joining thread to investigate payment checkout latency..."*
3. **Step 3: Correlated Telemetry SLO Breach (`obs-agent` @ 10:16 AM)**:
   - Correlates support signals with APM metrics. Confirms active latency SLO breach on `payment-wallet-api` endpoint `check_pocket_balance()`:
     - **p95 Latency**: `2,100ms` (SLA: `150ms`)
     - **p99 Latency**: `3,450ms` (SLA: `200ms`)
4. **Step 4: Autonomous RCA & Journey Context (`product-agent` @ 10:18 AM)**:
   - Traces the entire customer journey across microservice dependencies.
   - Discovers that **94% of transaction latency** is localized in `payment-wallet-api` MongoDB execution.
   - Pinpoints the exact query pattern:
     ```javascript
     db.pocket_mapping.find({ user_id: ..., status: "active" })
     ```
   - Identifies the precise database diagnostic: **Unindexed `COLLSCAN` examining 2.8M documents per query**!
5. **Step 5: Automated Remediation Discovery (`ops-agent` @ 10:19 AM)**:
   - Cross-references the RCA with open and pre-generated pull requests.
   - Discovers that a scheduled 3:00 AM Atlas Advisor automation had already prepared GitLab MR #402:
     ```javascript
     db.pocket_mapping.createIndex(
       { user_id: 1, status: 1, created_at: -1 },
       { background: true }
     )
     ```
   - Flags MR #402 directly in Slack as `[READY TO MERGE]`.
6. **Step 6: Human Approval & Blast-Radius Check (`Alex Kim` @ 10:21 AM)**:
   - Human engineer verifies the index parameters: *"Reviewed MR #402! Confirmed it creates background compound index for pocket_mapping collection on our impacted journey. Merging now! 🚀"*
7. **Step 7: Autonomous Deployment & Verification (`GitLab Integration` @ 10:22 AM)**:
   - MR #402 merged into `main`.
   - Triggers background database migration on MongoDB Atlas Cluster 01.
   - Reports live completion: `Index status: BUILD_COMPLETE`.
- **The Operability Difference**:
  - **Total Resolution Time**: **8 minutes (10:14 AM to 10:22 AM)** from user friction detection to production remediation!
  - Contrast this with traditional SRE workflows where engineers spend 45–90 minutes manually correlating disconnected logs, reproducing queries, and testing index syntax during an active outage.

---

### 🌐 System Architecture & Topology: Under the Hood

Khang Toh shared the concrete technology stack powering the production Agentic Digital Factory:

```mermaid
flowchart TD
    subgraph ClientTier["Client / Presentation Layer"]
        Browser["<b>Browser SPA</b><br/>React 19 • TypeScript 5.9 • Vite 7<br/><i>HTTPS + WebSocket Streaming</i>"]
    end

    subgraph IngressTier["Public Ingress Layer"]
        Nginx["<b>Public Web Gateway</b><br/>Nginx Reverse Proxy / SSL Termination"]
    end

    subgraph ProductTier["Product & Routing Layer"]
        FastAPI["<b>API Service & Worker</b><br/>FastAPI • Uvicorn • Python 3.13 (asyncio)"]
        Router["<b>Semantic Router</b><br/>FastAPI • FastEmbed • BGE (CPU)"]
        Postgres[("<b>PostgreSQL + pgvector</b><br/>Product State • Queues • Projections • Vectors")]
    end

    subgraph PrivateNetwork["Private Service Network"]
        ControlPlane["<b>Runtime Control Plane</b><br/>Kotlin 2.2 • Ktor 3 • JVM 21"]
        OpenHands["<b>OpenHands Agent Server (v1.27.1)</b><br/>Per-Session Isolated Coding Sandbox"]
        RuntimeBackend["<b>Runtime Backend</b><br/>Docker Engine / Kubernetes<br/>(docker-java • fabric8)"]
    end

    Browser <-->|HTTPS / WS| Nginx
    Nginx <--> FastAPI
    FastAPI <--> Router
    FastAPI <--> Postgres
    Router <--> Postgres
    FastAPI <-->|RPC / Events| ControlPlane
    ControlPlane <-->|Session Sandbox API| OpenHands
    OpenHands <--> RuntimeBackend
```

#### Detailed Component Breakdown
1. **Frontend Client Layer**:
   - **React 19**, **TypeScript 5.9**, **Vite 7** Single Page Application (SPA).
   - Real-time bidirectional streaming over WebSockets for live agent execution traces, token streams, and interactive approvals.
2. **Web Gateway & Ingress**:
   - **Nginx** reverse proxy managing rate limiting, SSL termination, and WebSocket connection upgrades.
3. **Product & API Service**:
   - **Python 3.13** running **FastAPI** on **Uvicorn** with non-blocking `asyncio` concurrency.
   - Orchestrates feature creation workflows, Jira integration, and SlackOps event dispatching.
4. **Semantic Routing & Context Retrieval**:
   - **Semantic Router** powered by **FastEmbed** with **BGE embeddings** running efficiently on CPU without requiring GPU overhead.
   - Routes intent directly to domain-specific agent loops and CodeWiki subgraphs.
5. **Durable Persistence & Vector Store**:
   - **PostgreSQL** paired with the **`pgvector`** extension.
   - Stores transactional product state, asynchronous task queues, CQRS materialized projections, and vector embeddings for code search.
6. **Runtime Control Plane**:
   - Built with **Kotlin 2.2** on **Ktor 3** running on **JVM 21**.
   - Acts as the deterministic coordinator governing agent sandboxes, resource allocation, and lifecycle management.
7. **Agent Execution Sandbox (OpenHands v1.27.1)**:
   - Deploys **OpenHands Agent Server** (`v1.27.1`) to provide per-session, hermetically isolated coding sandboxes.
   - Prevents untrusted agent code from accessing host infrastructure or leaking cross-tenant credentials.
8. **Runtime Backend**:
   - Orchestrates underlying container workloads across **Docker Engine** and **Kubernetes** using **`docker-java`** and **`fabric8`** client libraries.

---

## 💡 Live Notes & Quotes

- *"Stop Shipping Features with AI. Start Shipping AI Operable Products."*
- *"Everyone's building the factory that delivers the software. But where does your factory lane end?"*
- *"The missing layer is not another agent. It is product operability."*
- *"Most products expose a user surface. AI Operable Products expose the operating surface for humans + AI."*
- *"2000–2026: The eras this room lived through. Not nostalgia. A pattern."*
- *"From 'finish the phase' $\to$ 'ship small' $\to$ 'deploy continuously' $\to$ 'observe production' $\to$ 'direct agents.'"*
- *"We did not just automate away toil."*
- *"Every cycle - the loop got faster. But Ops did not disappear."*
- *"Every era shortened the distance between writing software and knowing whether it worked."*
- *"The model writes. The harness decides whether the goal was met."*
- *"LGTM Engineering: The art of approving a 1000-line PR you did not read, written by an agent, reviewed by another agent... merged by a human who just wants to go to lunch."*
- *"Production does not care whether the change came from human or agent."*
- *"High deployment frequency with rising change failure rate is not victory."*

---

## 👤 Speaker Profile & Reference Links

- **Speaker**: **Khang Toh**
- **Company / Platform**: [fdeploy.ai](https://fdeploy.ai) — Applied AI engineering deployed inside enterprise operations; governing agents, identity, and model gateways.
- **LinkedIn**: [linkedin.com/in/khangtoh](https://www.linkedin.com/in/khangtoh)
- **Reference Tooling & Claude Skill**: [labs.formative.ai/ai-operable-product](https://labs.formative.ai/ai-operable-product)
  - Open-source Claude Code and ChatGPT skill enforcing the **7 Primitives of AI Operable Products** across MCP connected sources.

---

## 🔗 Related Notes & Cross-References

- 🌟 [[ContainerDays Singapore 2026]] — Master conference schedule and session index
- 🏭 [[When Tokens Stop Being the Bottleneck - Operating Agentic Software Factories (Carl Ross)]] — The upstream software factory generating high-velocity code
- 💬 [[Fireside Chat with Kelsey Hightower & Geet Bhanawat]] — Kelsey on finding the real bottleneck and fixing the underlying system
- 📊 [[Shipping Reliable AI Agents - Building with Langfuse and ClickHouse (Max Deichmann)]] — Deep agent tracing and observability
