# Confessions of a Portal Assistant: Hard Lessons from Shipping an LLM into a Developer Platform

> **Speaker**: Yashod Perera (Maintainer @ OpenChoreo / CNCF Sandbox · WSO2 LLC)  
> **Event**: [ContainerDays Singapore 2026](./ContainerDays%20Singapore%202026.md)  
> **Date & Time**: Tuesday, October 27, 2026 · 9:30 AM – 10:05 AM SGT  
> **Stage**: CDS Theatre  
> **Platform/Project**: [OpenChoreo](https://github.com/openchoreo) (CNCF Sandbox developer platform for Kubernetes)  
> **Vault Connections**: *The Road Under the Harness (Ng Shangru)* • [Shipping Reliable AI Agents - Building with Langfuse and ClickHouse (Max Deichmann)](./Shipping%20Reliable%20AI%20Agents%20-%20Building%20with%20Langfuse%20and%20ClickHouse%20%28Max%20Deichmann%29.md) • *Do You Trust Your AI - Beyond the Vibes at SGInnovate* • *AI Agent Engineering* • *Trace It, Store It, Ship It - LLM Observability at GovTech SG*

---

## ⚡ TL;DR (Key Takeaways in 60 Seconds)

- **The Core Dilemma**: Internal Developer Portals (IDPs) designed for human ClickOps break down when autonomous AI agents take over. Portals must expose machine-readable platform abstractions, not raw Kubernetes YAML.
- **Why RAG Portals Failed**: Moving from naive RAG chatbots ("portal assistants") to autonomous agents revealed that agents either hallucinate 400 lines of unreviewed Kubernetes YAML or bypass the portal entirely using raw developer `kubeconfig` credentials.
- **The OpenChoreo Architecture**: Introduces two scoped MCP servers: a **Control Plane MCP** (94 strictly governed domain tools rather than raw Kubernetes primitives) and an **Observability MCP** (pre-digested condition summaries rather than raw metric dumps).
- **Abstractions That Survive an LLM**: Giving agents "fewer words" via 12-line CEL-rendered `Component` specs prevents agents from hallucinating unapproved cluster resources.
- **Autonomous SRE Agents**: An alert-triggered agent can autonomously diagnose production incidents by traversing declared topology graphs—provided there are no unmapped governance gaps.

---

## 📸 Stage & Slides

![theatre stage](Attachments/cds26-theatre-stage.jpg)

> **CDS Theatre Kickoff (~09:20 SGT)**: Stage setup at CDS Theatre — *"Good Morning Singapore!"* opening screen.

![yashod perera intro](Attachments/cds26-yashod-perera-intro.jpg)

> **Session Kickoff (~09:30 SGT)**: Yashod Perera (Maintainer @ OpenChoreo, WSO2) introducing *Confessions of a Portal Assistant: Hard Lessons from Shipping an LLM into a Developer Platform*.

![openchoreo in one slide](Attachments/cds26-openchoreo-in-one-slide.jpg)

> **Architecture Overview (~09:31 SGT)**: *OpenChoreo in one slide* — The platform abstraction contract between Platform Engineers and Developers.

![where the assistant lives](Attachments/cds26-where-the-assistant-lives.jpg)

> **System Topology (~09:32 SGT)**: *Where the assistant lives* — How human interfaces and autonomous agents (via MCP servers) interface with the Kubernetes CRD Control Plane.

![openchoreo portal demo](Attachments/cds26-openchoreo-portal-demo.jpg)

> **Live Demo UI (~09:33 SGT)**: OpenChoreo Developer Portal showing the `URL Shortener` project with failing components (`snip-frontend` & `snip-analytics-service` with warning badges in Development).

![tuesday 440pm failing deployment](Attachments/cds26-tuesday-440pm-failing-deployment.jpg)

> **The Universal Problem (~09:34 SGT)**: Yashod introducing the scenario: *"Tuesday, 4:40pm. Why is my deployment failing?"*

![the assistant never looked](Attachments/cds26-the-assistant-never-looked.jpg)

> **The Failure Mode (~09:35 SGT)**: *What was true vs what the assistant did* — RAG lectured the developer with generic documentation while the actual failure (`secret snip-analytics-export not found`) was never looked at.

![recipe 1 the chatbot](Attachments/cds26-recipe-1-the-chatbot.jpg)

> **Recipe 1 / 3 (~09:35 SGT)**: *The chatbot* — The naive weekend pipeline (Docs ➔ Chunk ➔ Vector DB ➔ LLM ➔ Chatbox) and its fatal flaw.

![recipe 2 the tool caller](Attachments/cds26-recipe-2-the-tool-caller.jpg)

> **Recipe 2 / 3 (~09:36 SGT)**: *The tool-caller* — Exposing raw OpenAPI specs as 106 tools to an LLM, causing massive tool confusion and blind cluster targeting.

![recipe 3 the agent](Attachments/cds26-recipe-3-the-agent.jpg)

> **Recipe 3 / 3 (~09:36 SGT)**: *The agent* — Giving an autonomous loop full RBAC write tokens directly against production clusters (*"Let it fix things"*), with zero scoping or auditability.

![we did all three in the open](Attachments/cds26-we-did-all-three-in-the-open.jpg)

> **The Turning Point (~09:36 SGT)**: *"We did all three. In the open."* — The 3 counter-lessons developed through open failure postmortems.

![two failure examples](Attachments/cds26-two-failure-examples.jpg)

> **Two Archetypal Failures (~09:37 SGT)**: *Example 1 (The Lecture)* vs *Example 2 (The Healthy Pod)* — Revealing the difference between pod readiness and true application health.

![not the model the harness](Attachments/cds26-not-the-model-the-harness.jpg)

> **The Root Cause (~09:38 SGT)**: *"Not the model. The harness."* — Accuracy does not come from reasoning models; it comes from the harness context and scoped tool selection.

![lesson1 context is the product](Attachments/cds26-lesson1-context-is-the-product.jpg)

> **Lesson 1 (~09:39 SGT)**: *Context is the product* — Full context window, wrong contents. 106 tools and 112 releases vs 0 bytes of the user's actual deployment!

![ground in platform not docs](Attachments/cds26-ground-in-platform-not-docs.jpg)

> **The Live State Pipeline (~09:40 SGT)**: *Ground in the platform, not the docs* — Injecting active portal context (pinned run/log, component, environment) and scoped observability rather than fuzzy similarity search.

![one case failed deployment](Attachments/cds26-one-case-failed-deployment.jpg)

> **Case Walkthrough (~09:41 SGT)**: *One case: a failed deployment* — How 5 portal context fields and 18 scoped tools produce the exact root cause in two calls with zero token waste.

![fetching isnt enough](Attachments/cds26-fetching-isnt-enough.jpg)

> **Context Engineering (~09:42 SGT)**: *Fetching isn't enough* — Markdown tables over raw JSON (-64% tokens), stripping K8s noise via OutputTransformer middleware, and multi-hop project context.

![the model didnt get smarter](Attachments/cds26-the-model-didnt-get-smarter.jpg)

> **Production Demo UI (~09:44 SGT)**: *The model didn't get smarter. We did.* — Precision root-cause output, explicit out-of-scope boundaries, and auto-generated prompts for coding agents.

![lesson2 trust is earned](Attachments/cds26-lesson2-trust-is-earned.jpg)

> **Lesson 2: Evals (~09:45 SGT)**: *Trust is earned in the failure cases* — The human eval harness, dogfood embarrassment list, and transitioning to automated trajectory evals.

![i dont know but heres how to check](Attachments/cds26-i-dont-know-but-heres-how-to-check.jpg)

> **Calibrated Humility (~09:46 SGT)**: *“I don't know, but here's how to check”* — Before (confident hallucination based on single plane) vs After (multi-plane log correlation with honest cross-project boundaries).

![every change is measured](Attachments/cds26-every-change-is-measured.jpg)

> **Harness Metrics (~09:47 SGT)**: *Every change is measured* — Shipped vs Rejected engineering scorecard; *"Trust isn't the average answer. It's the worst one a user remembers."*

![lesson3 once it could see](Attachments/cds26-lesson3-once-it-could-see.jpg)

> **Lesson 3: Future Agent Road (~09:48 SGT)**: *Once it could see* — The dangerous jump from assistant to agent; drafting fixes with mandatory approval vs skipping to production.

![every result scrubbed audit next](Attachments/cds26-every-result-scrubbed-audit-next.jpg)

> **Security & Governance (~09:50 SGT)**: *Every result scrubbed. Audit is next.* — Automated redaction of secrets/tokens/hostnames, and a unified audit trail across CLI, Portal, and Assistant.

![claude code handoff demo](Attachments/cds26-claude-code-handoff-demo.jpg)

> **Live Remediation Demo (~09:51 SGT)**: *Claude Code Agent Handoff* — Pasting the generated fix prompt into Claude Code to autonomously resolve undeployed dependencies via `openchoreo-cp`.

![you will ship a confident liar](Attachments/cds26-you-will-ship-a-confident-liar.jpg)

> **Closing Slide (~09:54 SGT)**: *"You will ship a confident liar. The question is whether you find out before your users do."* — GitHub repo pointer (`github.com/openchoreo/openchoreo -> agents/`) and session wrap-up.

---

## 📝 Live Notes & Raw Thoughts

### 🏗️ OpenChoreo Golden Paths Model
- **Core Philosophy**: *"Platform teams decide what gets provisioned; developers state intent."* (No raw Kubernetes YAML required from developers).
- **Platform Engineers Define**:
  - **Component Types**: service, web app, scheduled task
  - **Traits**: autoscaling, alerts, storage
  - **Workflows**: how code is built
  - **Environments**: dev, staging, prod
  - **Promotion Paths**: dev → staging → prod
- **Developers Consume (Golden Paths)**:
  - Create a component from an existing type
  - Build via platform workflow
  - Deploy and promote along established path
  - Unified observability: view logs, traces, alerts organized *by component*
- **Why this matters for the AI Assistant**: The assistant wasn't just answering generic Kubernetes questions; it needed to understand *this exact abstraction hierarchy* (components, traits, workflows, environments) instead of reciting generic `kubectl` commands!

### 🧩 Where the Assistant Lives: The MCP Bridge
- **Two Distinct Classes of Consumers**:
  - **People**: Backstage-based Portal, CLI (`occ`), GitOps pipelines.
  - **Agents**: **Portal Assistant** (interactive in this talk) and **SRE Agent** (triggered autonomously on alert).
- **The Protocol Layer**: Agents communicate with platform infrastructure through ***MCP Servers*** managing access to `control plane · observability`.
- **Single Source of Truth (Control Plane CRDs)**:
  - Kubernetes CRDs define the platform contract: `Namespace` · `Project` · `Component` · `Environment` · `ReleaseBinding` · `Workflow`.
- **Three Underlying Planes**:
  - **Data planes**: run actual application workloads
  - **Workflow plane**: manages CI/CD builds
  - **Observability plane**: collects component logs & traces
- **💡 Core Maxim**: 
  > *"Intent in. Orchestration below. Meaning back. Day one is covered by templates. Day two is 'why is my deployment failing?' The assistant was built for day two."*

```mermaid
flowchart TD
    subgraph Consumers["Platform Consumers"]
        subgraph People["People"]
            Portal["Portal<br/>(Backstage-based)"]
            CLI["CLI<br/>(occ)"]
            GitOps["GitOps<br/>(pipelines)"]
        end
        subgraph Agents["Agents"]
            Assist["Portal Assistant<br/><i>(Interactive helper)</i>"]
            SRE["SRE Agent<br/><i>(On alert trigger)</i>"]
        end
    end

    Assist --> MCP["<b>MCP Servers</b><br/>(Control plane · Observability)"]
    SRE --> MCP

    subgraph ControlPlane["Control Plane: Platform Contract & Source of Truth"]
        CRDs["Kubernetes Custom Resources (CRDs)<br/>• Namespace • Project • Component<br/>• Environment • ReleaseBinding • Workflow"]
    end

    People --> ControlPlane
    MCP --> ControlPlane

    subgraph ExecutionPlanes["Execution & Telemetry Planes"]
        Data["Data Planes<br/>(Run workloads)"]
        Workflow["Workflow Plane<br/>(Builds)"]
        Obs["Observability Plane<br/>(Logs, traces, metrics)"]
    end

    ControlPlane --> Data
    ControlPlane --> Workflow
    ControlPlane --> Obs
```

### 🖥️ Live Demo Scenario: The Broken "URL Shortener" Project
- **Project Structure**:
  - `snip-redis` (deployment/service) — ✅ Dev Healthy
  - `snip-frontend` (deployment/web-application) — ⚠️ **Dev Deployment Warning**
  - `snip-api-service` (deployment/service) — ✅ Dev Healthy
  - `snip-analytics-service` (deployment/service) — ⚠️ **Dev Deployment Warning**
  - `snip-postgres` (resource/postgres) — ✅ Dev Healthy
- **The Real-World Dilemma**: *"Tuesday, 4:40pm. Why is my deployment failing?"*
  - The developer is trying to finish their workday, shipping a change to Dev, when suddenly two components light up yellow/red.
  - Developers don't want to parse 50 lines of raw Kubernetes Pod events, shell into containers, or write complex Prometheus/Grafana queries. They look at the portal and ask the chat assistant for an instant, clear answer.
  - The portal exposes rich contextual tabs (`DEFINITION`, `DEPLOY`, `CELL DIAGRAM`, `LOGS`, `TRACES`, `INCIDENTS`, `RCA REPORTS`, `METRICS`).
  - **The Assistant's Actual Mandate**: Synthesize these live signals via MCP into an actionable root-cause answer rather than reciting generic deployment instructions or hallucinating CLI flags.

### ❌ The "Confident Liar" Anatomy: The Assistant Never Looked
- **What the Developer Asked**: *"why is my deployment failing?"*
- **What the Assistant Responded**:
  > *"Great question! Deployments can fail for several reasons. Let me walk you through the deployment lifecycle in OpenChoreo. 1. Build stage... 2. Release stage... 3. Environment promotion... [continues for four more paragraphs]"*
- **What Was Actually True**:
  - `snip-analytics-service · development · secret snip-analytics-export not found`
  - Her deployment was failing simply because a Kubernetes Secret was missing.
- **The Painful Postmortem**:
  - **The assistant never looked.** It relied on static RAG embeddings of the documentation, resulting in a polite, patronizing essay about deployment lifecycles while completely oblivious to the live Kubernetes state right beneath its nose.
  - This is the fundamental turning point: **RAG over docs is useless for operational debugging; live platform context is the product.**

### 🥣 Recipe 1 / 3: The Chatbot (Version 0.01)
- **The Pipeline**:
  `Docs (markdown) ➔ Chunk & Embed ➔ Vector DB (top-k) ➔ LLM (system prompt) ➔ Chat box in the portal`
- **How Teams Build It**: *"A weekend with the docs folder and a framework."*
- **In OpenChoreo**: Exactly this. Version 0.01 of the Portal Assistant.
- **The Catch**: 
  > ⚠️ **"It knows what the docs say, not what the platform is doing."**
- It cannot inspect active Kubernetes Pod events, check if a Secret exists, read dynamic traces, or observe live container exit codes.

### 🛠️ Recipe 2 / 3: The Tool-Caller (The Naive OpenAPI Dump)
- **The Pipeline**:
  `OpenAPI spec (every endpoint) ➔ Generator (one tool each) ➔ 106 tools (including 27 cluster_ duplicates) ➔ LLM picks one`
- **How Teams Build It**: *"Just expose the API."*
- **In OpenChoreo**:
  - Auto-generated **106 tools** from OpenAPI specs by May 2026.
  - Collapsing endpoints by making `scope` an argument reduced the count to **79 tools** (-25%), which was still way too high for reliable LLM tool selection.
- **The Catch**:
  > ⚠️ **"A hundred ways to be wrong, and no idea which cluster it is talking to."**
- **Core Lesson**:
  - Naive 1:1 endpoint-to-tool mapping overwhelms the model's tool-selection context window.
  - The model confuses near-identical cluster endpoints, selects wrong namespaces, and fails to maintain multi-cluster state awareness.

### 🤖 Recipe 3 / 3: The Agent (The Unscoped Superuser Trap)
- **The Pipeline**:
  `Agent loop (reason ➔ call a tool ➔ observe ➔ repeat) ➔ Write token (full RBAC) ➔ Your cluster (production)`
- **How Teams Build It**: *"Let it fix things."*
- **In OpenChoreo**: *"We were tempted within a week."*
- **The Catch**:
  > ⚠️ **"Nobody scoped what it may touch. Nothing is auditable when it is wrong."**
- **The Danger**:
  - Handing an autonomous agent high-privilege credentials or cluster-admin tokens without strict perimeter guardrails.
  - An agent loop with write permissions can recursively mutate resources, alter cluster state unexpectedly, or trigger destructive cascade failures with zero non-repudiable audit logs.

| Recipe | Pipeline Model | How Teams Justify It | The Fatal Catch |
| :--- | :--- | :--- | :--- |
| **1. The Chatbot** | Docs ➔ Embed ➔ Vector DB ➔ Chat | *"A weekend with docs and a framework"* | It knows what the docs say, not what the platform is doing. |
| **2. The Tool-Caller** | OpenAPI ➔ 106 tools ➔ LLM picks | *"Just expose the API"* | A hundred ways to be wrong, and no idea which cluster it is talking to. |
| **3. The Agent** | Reason ➔ Tool ➔ Observe ➔ Write token | *"Let it fix things"* | Nobody scoped what it may touch. Nothing is auditable when it is wrong. |

### 💡 "We Did All Three. In The Open."
> *"Each one starts with something the assistant got wrong in our testing, before a user ever saw it."*

The core engineering playbook that emerged from these three failures:
1. **Lesson 1: Feed the model the right context** (Fixes Recipe 1 — Grounding in live state, not doc RAG).
2. **Lesson 2: Measure when it lies** (Fixes Recipe 2 — Real-world evaluation harnesses over platform knowledge).
3. **Lesson 3: Keep the blast radius small when it acts** (Fixes Recipe 3 — Strict least-privilege scoping, human on the destructive path, non-repudiable audit trails).

### 🔍 Anatomy of Failure: Two Real-World Examples

| Scenario | User Question | Assistant Answer | Ground Truth Reality | The Root Flaw |
| :--- | :--- | :--- | :--- | :--- |
| **Example 1: The Lecture** | *"why is my deployment failing?"* | *"Great question! Let me walk you through the deployment lifecycle in OpenChoreo... [5 paragraphs]"* | **A secret was missing.** | **It never looked.** Static RAG generated general documentation rather than checking live cluster resources. |
| **Example 2: The Healthy Pod** | *"is payments-api ok in production?"* | *"Yes — healthy. The release is Ready and all pods are Running."* | **The logs were full of errors.** The pod was healthy; `payments-api` was NOT OK. | **Superficial K8s status trap.** Pod status `Running` $\neq$ application health. The assistant checked container lifecycle but skipped application logs/traces. |

> 📌 **Key Insight**: Operational truth requires **multi-plane correlation** (Control Plane CRDs + Pod Status + Container Exit Codes + Observability Logs & Traces). Checking any single plane in isolation produces dangerous hallucinations or false senses of security.

### 🎯 The Golden Rule: "Not the model. The harness."
*(Direct alignment with *The Road Under the Harness (Ng Shangru)*)*

> **"Both bad answers had the same root cause. Not the model. The harness."**  
> — *The context it is given, and the set of tools it gets, for each case.*

- **The Reasoning Model Myth**:
  - Teams often assume failures mean they need bigger, slower, more expensive "reasoning" models (o1, deep-thinkers).
  - OpenChoreo did the opposite: **moved from a slow reasoning model to fast non-reasoning ones.**
  - **Result**: *Faster, no less accurate.*
  - **The Epiphany**: **"The accuracy was never in the model."**
- **Where Accuracy Actually Lives**:
  1. **Precise Context Injection**: Dynamically providing the right platform state (logs, traces, CRDs) instead of static documentation.
  2. **Minimal, Scoped Tool Sets**: Providing 3–5 targeted tools per interaction rather than dumping 100+ raw OpenAPI endpoints.

### 📦 Lesson 1: Context is the Product (0 Bytes of What Mattered)
> **"Full window, wrong contents. The fix: her data in, the noise out."**

- **The Anatomy of a Full Context Window**:
  - **System prompt**: *"You are the OpenChoreo assistant..."*
  - **106 tools**: Zero guidance on which tool fits the situation.
  - **Random tool dump**: `list_components` (40 items), `list_environments` (6 items), `get_cluster_info` ({...}), `list_releases` (112 items), `get_project` ({...}).
  - **The verdict**: *"Mostly garbage, assembled by accident."*
- **What the Model Did NOT Have**:
  - **Her deployment: 0 BYTES!**
  - Component, target environment, latest build artifact, container logs, missing Secret.
- **The Core Platform Solution**:
  - Don't let agents crawl 106 endpoints blind. 
  - Feed the specific active page/component context automatically: *Her data in, the platform noise out.*

### ⚡ Ground in the Platform, Not the Docs
- **The Vector Similarity Trap**:
  > ⚠️ *"why is my deployment failing" is semantically similar to every single page about deployments in your documentation.*
  - Traditional RAG simply pulls general deployment documentation, resulting in zero actionable insight into the actual failure.
- **The OpenChoreo Solution Architecture**:
  - **Portal Context Injected Automatically**:
    - The portal interface sends explicit scope: active `namespace`, `project`, `component`, `environment`, `case`, and the specific `pinned run` or `log row`.
  - **Platform Contract**: Queries exact CRDs: active `components`, `release bindings`, and `workflow runs`.
  - **Observability API**: Fetches logs, traces, and events *scoped by component*.
  - **Case-Specific Small Toolsets**: Instead of 106 tools, each case receives a tiny, dedicated tool set.
  - **Unified "Meaning Back" Path**: The assistant reads the exact same semantic data path used by the platform CLI (`occ`).

```mermaid
flowchart LR
    Portal["<b>Portal Context</b><br/>• Namespace, Project<br/>• Component, Environment<br/>• Pinned run / log row"] --> Contract["<b>Platform Contract</b><br/>• Components<br/>• Release bindings<br/>• Workflow runs (CRDs)"]
    Contract --> Obs["<b>Observability API</b><br/>• Logs<br/>• Traces<br/>• Events (by component)"]
    Obs --> Model["<b>Model</b><br/><i>(Sees her deployment!)</i>"]
```

### 🎯 Case Study: A Failed Deployment In Production
> **"Small context. The right tools. One answer."**

1. **Context Injected from the Portal (5 Explicit Fields)**:
   - `caseType`: `runtime_debug`
   - `namespace`: `default`
   - `project`: `url-shortener`
   - `component`: `snip-analytics-service`
   - `environment`: `development`
   - *Result*: Five structured fields. No raw markdown docs, no 40-item component lists.

2. **Scoped Tools for This Case (Dynamic Tool Gating)**:
   - `get_resource_tree`
   - `get_resource_events`
   - `get_resource_logs`
   - `+ 15 more`: focused on logs, traces, topology.
   - *Result*: **18 read-only tools** (deploy tools prioritized), NOT the full 106-tool catalog!

3. **What Comes Back (Instant Precision)**:
   - `Deployment · Degraded`
   - `Pod · CreateContainerConfigError`
   - `secret "snip-analytics-export" not found`
   - *Result*: **Two calls.** Every token in the prompt and response is 100% relevant to her deployment.

### 📊 Fetching Isn't Enough: 3 Tactical Context Engineering Techniques
> *"Fetching data is step one. How that data is shaped before the LLM sees it determines cost, latency, and hallucination rate."*

1. **Markdown, Not JSON (-64% to -71% Token Reduction)**:
   - Raw Kubernetes JSON contains massive syntax bloat: brackets, quotes, braces, indentation, and repeated schema keys.
   - **50 rows of raw JSON logs/events**: **10,981 tokens**.
   - **Same 50 rows converted to a clean Markdown table**: **3,937 tokens** (**-64% reduction**).
   - **Traces**: **-46%** token reduction.
   - **Spans**: **-71%** token reduction.
   - *Architecture Rule*: **More platform abstractions = dramatically fewer LLM tokens.**

2. **Strip in Middleware (`OutputTransformer`)**:
   - Tool execution result ➔ `OutputTransformer` middleware ➔ Filtered payload ➔ LLM.
   - **What gets dropped**: Kubernetes resource UIDs, container hash strings, internal pod replica suffixes, managedFields.
   - **What gets preserved**: Correlation IDs, OpenTelemetry trace IDs, container exit codes, timestamps, error strings.
   - *Crucial Engineering Finding*:
     > ⚠️ *"Telling the model 'Ignore the metadata' in the system prompt DOES NOT WORK. Not sending it in the first place does."*
     > Models still suffer attention degradation and token burn when large hex strings and metadata blocks are present in context.

3. **Project-Wide by Default (Multi-Hop Root Cause Analysis)**:
   - When a component is failing, inspecting only that isolated component is an operational trap.
   - Example: `snip-analytics-service` reports `connection refused`.
   - Querying the broader project topology reveals sibling components and their health states.
   - The root cause is almost always **two hops away** (e.g. an upstream database or authentication service that failed to bind).
   - *Platform Principle*: **The failing component is rarely where the failure started.**

```mermaid
flowchart LR
    ToolResult["Raw K8s / Telemetry Tool Output<br/>(10,981 tokens JSON)"] --> Middleware["<b>OutputTransformer Middleware</b><br/>• Drops UIDs & container hashes<br/>• Keeps Trace & Correlation IDs<br/>• Converts JSON ➔ Markdown Table"]
    Middleware --> ModelContext["<b>Clean Context to LLM</b><br/>(3,937 tokens Markdown: -64%)"]
```

### 🎯 "The Model Didn't Get Smarter. We Did."
> *"Accuracy was never in the model parameters. It was in the harness design."*

- **The Production OpenChoreo Portal Assistant Output**:
  - **User Query**: *"why is my deployment failing?"*
  - **Assistant Answer**:
    > *"The **development** release of **snip-analytics-service** is Degraded: the pod is in **CreateContainerConfigError** because secret **snip-analytics-export** (key api-key, used by EXPORT_API_KEY) does not exist in that environment (event at 16:38:40).*  
    > *I can't see **production** from here, so I'm only reporting on development.*  
    > *Fix: create the secret, then redeploy. Here is a prompt for your coding agent: [Copy fix prompt]"*
- **What Made This Answer High Value**:
  1. **Strict Context Boundaries**: Explicitly states *"I can't see production from here, so I'm only reporting on development"*. Fences the model so the user never falsely assumes production is healthy or unaffected.
  2. **Agent-to-Agent Handoff (`[Copy fix prompt]`)**: Bridges the operational portal assistant to developer coding agents (Claude Code, Cursor, Copilot). It synthesizes the exact failure and parameters into a ready-to-run prompt.
  3. **Exact Sourced Grounding**:
     - `scope`: `portal: ns · project · component · env`
     - `get_resource_tree`: release binding, rendered + live
     - `get_resource_events`: the pod's events
     - `production`: `not in scope` (explicitly unqueried)

### 🧪 Lesson 2: Trust is Earned in the Failure Cases
- **The "Vibes" Eval Trap**:
  - *"The maintainers tried a few questions and it looked fine. We had optimised for the questions we liked to ask."*
  - Asking happy-path questions only confirms confirmation bias.
- **The Real Eval Harness: A Human & An Embarrassment List**:
  - OpenChoreo dogfooding: Maintainers ran their own workloads on the platform. Every time they opened the assistant drawer on a real failure—a failed build, a Degraded deploy, or a cryptic log row—that question was added to the test suite.
  - **The Golden Rule**: **A list, a person, and the rule that the list only grows.**
  - Every prompt update, middleware adjustment, or tool change must be manually re-verified against this embarrassment list before merging.
- **Advancement: Automated Trajectory Evaluation**:
  - Evals must check **the trajectory of tool calls**, not just the final markdown text.
  - A model could stumble onto the right answer through hallucinated tool parameters, wrong cluster targets, or accidental luck. Trajectory evals verify that the model queried the correct scope and tools step-by-step.

### 🛡️ Calibrated Humility: "I Don't Know, But Here's How to Check"
- **Before (Superficial K8s Status Trap)**:
  - *Response*: *"Yes — your payments-api component in production is healthy. The release is Ready and all pods are Running. No action needed."*
  - *Diagnosis*: Complete. Confident. Read one plane. Completely wrong because logs were flooded with 500 errors.
- **After (Multi-Plane Synthesis & Calibrated Humility)**:
  - *Response*: *"The release is Ready and the pods are healthy, but **payments-api is not OK**. In the last 15 minutes the logs show repeated: `ERROR failed to load user: user-service unreachable`. payments-api depends on **user-service**, in another project I can't see. **I don't know why it's unreachable — check user-service directly.**"*
  - *Takeaway*: **Evidence for what it knows. Honest about what it can't see. The answer users trust the most.**

### 📈 Every Change is Measured: The Engineering Scorecard
OpenChoreo evaluated every architectural optimization against real operational metrics:

| Change Attempted | Measured Impact | Engineering Decision | Rationale |
| :--- | :--- | :--- | :--- |
| **Markdown instead of JSON** | **-64% tokens on logs** | **Shipped** ✅ | Massive context savings, zero loss of error context. |
| **Build-log compressor** | **7 s slower**, no better answers | **Rejected** ❌ | Pre-summarizing logs added latency without improving diagnostic precision. |
| **Loop guard** | **No more repeat-call loops** | **Shipped** ✅ | Hard circuit breaker stops infinite agent tool-retry loops. |
| **Reasoning ➔ Fast model** | **Faster**, no less accurate | **Kept** ✅ | Slower reasoning models (o1/thinking) provided no advantage once harness context was clean. |

> 💎 **Guiding Maxim**:  
> *"Trust isn't the average answer. It's the worst one a user remembers."*

### 🚀 Lesson 3: Once It Could See (The Path from Assistant to Agent)
- **The Progression**: OpenChoreo is evolving the Portal Assistant into a **Portal Agent** (moving from explaining problems to taking remediation actions).
- **The Core Dilemma**:
  > *"The assistant found the missing secret, drafted the fix, and asked for your approval. ...or skipped that, and applied it to production."*
- **Blast Radius Architecture**:
  - Strict boundary between read-only observability and write mutations.
  - Remediations must be drafted as proposals with explicit human approval gates before touching production clusters.
  - Non-repudiable audit trails for every agent-initiated change.

### 🔒 Scrubbed Outputs & Unified Audit Trail
> *"Every result scrubbed. Audit is next."*

- **Automated Data Scrubbing**:
  - **Zero Exposure**: Tokens, secret keys, passwords, and internal hostnames are scrubbed from errors and stack traces *before* anyone (developer or LLM) sees them.
  - Hardened regex and token masks operate at the network/middleware boundary.
- **Unified Audit Log (`IN PROGRESS`)**:
  - Tracks all human and agent operations in a single chronologically ordered stream:
    | Time | Actor · Surface | Action | Scope |
    | :--- | :--- | :--- | :--- |
    | `16:38:02` | `yashod · occ` | `component get snip-analytics-service` | `default / url-shortener` |
    | `16:41:07` | `yashod · portal-assistant` | `get_resource_events` | `default / url-shortener / development` |
    | `16:47:02` | `yashod · portal` | `create SecretReference snip-analytics-export` | `default / url-shortener / development` |
  - **Non-Repudiation**: Every tool call made by the assistant is tagged with the user's authentic session identity (`yashod · portal-assistant`), making agent interactions 100% auditable alongside standard CLI and UI operations.

### 🤖 Live Remediation Demo: Portal Assistant ➔ Claude Code CLI
> *"Diagnose in the portal with scoped context. Fix in the IDE with autonomous tools."*

- **The Flow**:
  1. The **Portal Assistant** identifies the undeployed dependency: `snip-frontend` is failing because `snip-analytics-service` is undeployed in Development.
  2. The assistant outputs a structured remediation prompt via `[Copy fix prompt]`.
  3. **The Workflow Pivot**: *"Can use your AI agent to investigate... prompt copied from assistant."* Instead of manually context-switching, debugging YAML, or retyping scopes, the developer directly hands off the investigation to their local terminal coding agent.
  4. The developer switches to VS Code and pastes the prompt directly into **Claude Code** (running in terminal):
     ```text
     > Investigate why snip-frontend is stuck pending in OpenChoreo (ns default, env development).
     Observed:
       snip-frontend cannot resolve its connection to url-shortener/snip-analytics-service:http
       reason: component is undeployed.
     Scope:
       - namespace: default
       - project: url-shortener
       - dependent component: snip-frontend
       - blocking dependency: url-shortener/snip-analytics-service:http
       - environment: development
     Suggested next step:
       - Deploy snip-analytics-service to development through OpenChoreo UI or CLI,
         then confirm its http endpoint becomes available.
     Confirm the dependency is deployed and explain whether any additional endpoint configuration is required.
     ```
  4. Claude Code invokes the OpenChoreo CLI tool: `openchoreo-cp` to deploy the dependency and verify service endpoints!

---

## 🎯 Session Overview & Problem Statement

Adding an AI assistant to an internal developer portal sounds trivial on paper: wire an LLM up to docs and OpenAPI specs, add a chat UI, and ship. In production at **OpenChoreo** (CNCF Sandbox for Kubernetes), this initial naive approach failed immediately:
- **Hallucinated CLI Flags**: The LLM invented non-existent flags for Kubernetes & platform CLI tools.
- **Unseen Clusters**: Answered confidently about infrastructure clusters and namespaces it had zero visibility into.
- **Irrelevant Accuracy**: Delivered textbook explanations of generic Kubernetes concepts while failing to answer the single question developers actually cared about: *"Why is my deployment failing?"*

```mermaid
flowchart TD
    subgraph NaiveApproach["Naive V1: The Confident Liar"]
        User1["Developer: 'Why is my deployment failing?'"] --> RAG1["Static Doc RAG<br/>(Markdown docs & schemas)"]
        RAG1 --> LLM1["LLM Chatbot"]
        LLM1 --> Hallucination["Hallucinated flags & blind answers<br/><i>(Cannot see live pods, traces, or events)</i>"]
    end

    subgraph ProductionApproach["V2: Grounded Live Context & Guardrails"]
        User2["Developer: 'Why is my deployment failing?'"] --> ContextEngine["Context Aggregator Engine"]
        ContextEngine <--> LiveState["Live Platform State<br/>• K8s Events & Pod Status<br/>• Traces & Ingress logs<br/>• Active Deployment Specs"]
        ContextEngine --> Guardrails["Agent Middlewares & Policy Check"]
        Guardrails --> LLM2["Action-Scaped LLM"]
        LLM2 --> GroundedAnswer["Truthful answer + verified action<br/><i>(Or: 'I don't know, check X')</i>"]
    end
```

---

## ⚙️ Key Technical Lessons & Architecture

### 1. Context is the Product (Live State > Static Docs)
- **The RAG Trap**: Static documentation retrieval is insufficient for operational developer platforms. Stale or missing context was the root cause of almost every bad response.
- **Live State Grounding**: Moving from static document embeddings to real-time platform state ingestion:
  - Active Kubernetes component states, ReplicaSet status, and container restart counts.
  - Live deployment events, pod termination logs, and distributed traces.

### 2. Trust is Earned in Failure Cases (Eval Harness)
- **Eval Driven Development**: Built an eval harness directly from real user queries and failure transcripts.
- Measuring domain hallucination on platform-specific knowledge.
- High-value calibrated responses: Teaching the model that *"I don't know, but here is where to check"* is dramatically more valuable than a plausible-sounding hallucination.

### 3. Guardrails Before Capabilities (Action Scoping)
- Moving from **Read-only Q&A** to **Agentic Actions**:
  - Scoping exact permissions down to explicit APIs (least privilege).
  - Keeping a human-in-the-loop (HITL) on any destructive path (rollbacks, pod deletions, scale adjustments).
  - Complete structured auditability for every agent action.

### 🗣️ Live Q&A Discussion: Managing Token Costs
- **My Question to Yashod**: *"How do we manage token costs effectively when shipping platform assistants and agent loops?"*
- **Speaker's Recommendation (Yashod Perera)**:
  - **Deploy an AI Gateway**: Centralize all agent, tool, and assistant LLM traffic through an ***AI Gateway*** layer rather than letting client services call LLM providers directly.
  - **Why the Gateway is Critical for Cost Control**:
    1. **Prompt Caching Upstream**: Common platform definitions, tool schemas (18 tools), and static system instructions are cached at the gateway, avoiding repeated billable tokens.
    2. **Hard Budget Quotas & Rate Limits**: Sets token expenditure caps per team, project, or developer session, preventing runaway agent loops from generating surprise cloud bills.
    3. **Dynamic Model Routing & Tiering**: Automatically routes simple operational tasks (formatting Markdown tables, parsing exit codes) to fast, inexpensive models, while reserving frontier models strictly for complex multi-hop investigations.
    4. **Unified Cost Attribution**: Logs cost-per-incident or cost-per-query directly attributed to the authenticated user or CI/CD workflow.
  - **Direct Vault & Agenda Links**: Directly connects to *Agentic AI Night - Agent Gateways, A2A, & Jev* and perfectly sets up the upcoming Day 1 talk at **12:25 PM**: **Lessons from Operating an Internal LLM Gateway for Production Agentic Applications**!

---

## 💡 Key Takeaways & Questions
- **Core Takeaway**: 
  - *"Not the model. The harness."* High accuracy in developer platforms doesn't require slow reasoning models (o1/thinking); it requires dynamic context grounding (5 platform fields), small scoped toolsets (18 instead of 106), and aggressive context pruning (Markdown tables over JSON drops tokens by 64%).
  - *"Trust isn't the average answer. It's the worst one a user remembers."* Calibrated humility (*"I can't see production from here"* / *"I don't know why it's unreachable, check user-service"*) earns user trust ten times faster than confident, superficial hallucinations.
  - **Closing Punchline**:  
    > 💥 *"You will ship a confident liar. The question is whether you find out before your users do."*
- **Live Q&A Takeaway**: To control token burn and prevent runaway costs, platform teams must front their assistants with an **AI Gateway** for centralized caching, quota enforcement, and multi-tier model routing.
- **Questions to Ask / Follow Up**:
  - In OpenChoreo's upcoming Portal Agent, how are they handling authorization delegation when an agent executes a multi-step remediation across namespaces?
  - Does the `OutputTransformer` middleware handle structured log formats dynamically, or does it require hardcoded schema filters per component type?
  - How are trajectory evals scored when there are multiple valid tool paths to identify the same root cause?

---

## 🌐 Official Resources & Links
- **GitHub Repository**: [github.com/openchoreo/openchoreo](https://github.com/openchoreo/openchoreo) (`agents/` directory for portal assistant & middlewares)
- **Project Site**: [openchoreo.dev](https://openchoreo.dev) (Apache-2.0 · CNCF Sandbox)
- **Speaker**: Yashod Perera (Maintainer @ OpenChoreo / CNCF Sandbox · WSO2)

---

## 🔗 Related Notes & References
- [ContainerDays Singapore 2026](./ContainerDays%20Singapore%202026.md) — Master conference agenda and session log
- *Do You Trust Your AI - Beyond the Vibes at SGInnovate* — Reliability and evals in production AI
- [Shipping Reliable AI Agents - Building with Langfuse and ClickHouse (Max Deichmann)](./Shipping%20Reliable%20AI%20Agents%20-%20Building%20with%20Langfuse%20and%20ClickHouse%20%28Max%20Deichmann%29.md) — Tracing and evals for complex agent loops
