# Crystalline-AI
Turning complex, messy systems into ordered, optimized, self-improving ones — with a human always in the loop. Human-AI codesign
> One big model guesses. A crystalline agent team checks, connects, optimizes, and explains.

<img width="773" height="665" alt="image" src="https://github.com/user-attachments/assets/95be034d-df20-4721-86c8-e3567eb264ea" />

*All demos use synthetic / dummy data only. They illustrate the method, not any real matter. The system flags candidates for human review; it does not decide outcomes.*

---

## The core idea

Most real systems start like **raw rock**: they work, but they are disordered, redundant, and inefficient. The goal is to turn them into **crystal** — the same material, but with an ordered, optimized structure that is stronger and more efficient.

Crystalline AI does this with three ideas working together:

| Idea | Role | Plain English |
|---|---|---|
| **Multi-agent architecture** | the structure | A team of small specialized agents, each doing one job, instead of one large black-box model |
| **Operations Research** | the goal | Defines what "best" means and finds the most efficient path under real constraints (time, budget, reviewers) |
| **Autoresearch loop** | the improvement | The system measures itself against the goal, tries improvements, and iterates — guided, logged, and human-reviewed |

**The progression:** raw system → set a goal (OR) → improve in a loop (autoresearch) → ordered, optimized "crystal."

---

## The structure is a graph — and a causal DAG

Crystalline AI is not a list of steps. Its structure **is a directed graph**:

- **Each agent is a node.** Each hand-off is a directed edge. The flow has no loops within a pass — it is a **Directed Acyclic Graph (DAG)**, which makes it ordered, traceable, and easy to audit.
- **The reasoning layer is also a DAG.** The Relationship agent builds a graph of entities; the Causal agent uses a **causal DAG** (cause → effect, with the do() operator) to test whether a relationship is credible, not just correlated.
- **Why this matters:** a graph structure lets the system express *relationships* a flat pipeline can't — which agent depends on which, which evidence supports which finding, and what causes what. The graph describes; Operations Research optimizes; causal DAG tests credibility; the human decides.

> In short: the *architecture* is a DAG of agents, and the *reasoning* uses causal DAGs. Graph structure is what makes the whole system ordered ("crystalline") instead of tangled ("rock").

---

## Why this exists (the problem)

A working system is not the same as an optimized one. Teams ship something that runs, then it stays "good enough" forever — because improving it by hand is slow, and no one defines *what* "better" precisely means.

Crystalline AI addresses both gaps:
- **Operations Research** makes the goal explicit and measurable.
- **The autoresearch loop** improves toward that goal automatically, with every step auditable.
- **The multi-agent structure** keeps it modular, testable, and trustworthy.

---

## How to solve a problem (the method)

This repo follows a repeatable problem-solving loop, inspired by first-principles design:

1. **Understand the system** — map how it actually works, end to end, before changing anything.
2. **Divide and conquer** — break the problem into logic nodes (retrieval, validation, anomaly, relationships, optimization, synthesis). Each node is one job.
3. **Set the goal (Operations Research)** — define the objective and the constraints. What are we maximizing? What are the limits (time, cost, reviewer hours)?
4. **Run the loop (autoresearch)** — try an approach, measure it against the goal, keep what works, discard what doesn't, iterate.
5. **Human feedback gate** — an expert reviews consequential results; corrections become tests and "golden examples" for the next loop.
6. **Scale only what proves out** — more users and more complexity only after the loop shows real, measured value.

> Inspiration, not claims: this mirrors how nature organizes specialized roles (ant colonies, wolf packs) and how disciplined engineering improves in fast, stable cycles. The metaphors explain the structure — the substance is the architecture, the OR goal, and the measured loop.

---

## The self-improving loop (the heart of it)

```
   Complex system (raw rock)
            │
            ▼
   Operations Research  ──►  defines the GOAL + constraints
            │                (what "best" means)
            ▼
   ┌──────────────────────────────────┐
   │   AUTORESEARCH LOOP               │
   │   try → measure vs goal → learn   │ ◄── repeats
   │   → keep what works → improve     │
   └──────────────────────────────────┘
            │
            ▼
   Human review gate  ──►  expert validates, corrects
            │              (corrections become tests)
            ▼
   Ordered, optimized system (crystal)
```

The loop is **guided** (OR sets a clear target), **measured** (every attempt is scored against the goal), **auditable** (every step is logged), and **human-checked** (an expert approves consequential changes). It is not an open-ended autonomous agent — it is a disciplined, goal-directed improvement cycle.

---

## The agent team (the structure)

A coordinated team of small, specialized agents — each with one job, each passing a structured, auditable hand-off packet to the next.

```
        Management agent  (plans, assigns, coordinates)
                │
   ┌────────┬────────┬────────┬────────┐
 Retrieval Validation Anomaly Relationship Optimization
  (scout)  (inspector)(worker)  (graph)      (OR)
   └────────┴────────┴────────┴────────┘
                │
        Synthesis + evaluation  (merge, check, cite)
                │
        Human review gate  (expert decides)
```

| Agent | Job | Good model fit |
|---|---|---|
| Management | plans, assigns, coordinates, routes conflicts | medium LLM or rules + planner |
| Retrieval (scout) | finds evidence, captures citations | small embedding model (MiniLM, E5, BGE) + hybrid search |
| Validation (inspector) | checks rules, schema, data quality | rules + RoBERTa/DeBERTa classifier |
| Anomaly (worker) | finds outliers, spikes, missingness | Isolation Forest, random forest, XGBoost, clustering |
| Relationship (graph) | maps connections, finds gaps (GraphRAG) | NER model + graph engine (NetworkX, Neo4j) |
| Optimization (OR) | prioritizes what humans review first, under limits | OR-Tools, linear/integer programming |
| Synthesis + evaluation | merges, checks, cites, flags | stronger LLM in a harness |
| Human gate | final decision on anything consequential | the expert |

**Right-sized models:** use the smallest reliable model that does the job; reserve large models for the few tasks that need them.

---

## Structured hand-off packet (auditable, not a black box)

Each agent returns a structured packet so the whole system is inspectable:

```yaml
packet_id: "case_review_2026_001_retrieval"
agent_role: "scout"
task_id: "structured_disclosure_risk_review"
risk_tier: "medium"
output_summary:
  finding: "Three related entities appear across multiple filings."
  confidence: 0.82
  status: "needs_human_review"
sources_used:
  - {source_id: "DOC-001", citation: "page 4, table 2"}
assumptions:
  - "Entity names matched using normalized names and aliases."
limitations:
  - "Alias matching may miss abbreviated names."
handoff_to_next_agent:
  next_agent: "relationship_agent"
human_review:
  required: true
  reason: "Relationship finding may affect regulated review."
```

It records what was searched, what was found, what was *not* found, the assumptions, the confidence, and why a human should review. That is what makes the loop trustworthy.

---

## Demos (synthetic data)

- **Graph detection + Operations Research triage** — graph rules flag relationship issues (peer outliers, shared-auditor clusters, cross-filing mismatches); OR picks which flagged items a human reviews first within a limited budget. (`or_with_charts.py`)

<img width="895" height="676" alt="image" src="https://github.com/user-attachments/assets/46489ba5-e8e7-4a1f-9f32-30b3b4d57b77" />


- **Causal AI with DAGs** — discovery, intervention, and counterfactual what-if (PCMCI, do-calculus) — tests whether a relationship is credible, not just correlated.
<img width="1121" height="687" alt="image" src="https://github.com/user-attachments/assets/9fa4a7d6-1ac6-4c6e-9384-e81d1b6fcb70" />



```bash
pip install networkx matplotlib
python or_with_charts.py
```

---
## The name

A rock and a crystal can contain similar material, but the crystal is stronger because its structure is ordered. Crystalline AI turns a working-but-messy AI workflow into an ordered, modular, testable system.

> The model is the brain.  
> The architecture is the nervous system.  
> Operations Research helps set the priority.  
> The feedback loop helps the system improve.  
> The human expert holds the wheel.

---

## Why this matters for regulated / federal work

The same pattern fits structured disclosure, risk analysis, and oversight:
- **Graph** describes relationships across records.
- **Operations Research** spends scarce expert time on the highest-risk items.
- **Causal AI** tests whether a flag is a real signal or coincidence.
- **The loop** improves the system toward a measured goal.
- **The human** decides anything consequential.

Built-in controls: permission-aware retrieval, data classification, audit logs, citation checks, run-to-run comparison, and a human review gate.

## 🚀 Latest Update: Operations Research & Causal AI Dashboards

We have drastically expanded **Crystalline AI** from a standard GraphRAG knowledge base into a dynamic, mathematical **Operations Research and Risk Engine**. 

By applying Graph Theory, Community Detection, and do-calculus to standard messy text documents (SOPs), Crystalline AI now acts as an automated consultant for organizational design and risk management.

### 📊 New Modules & Capabilities

#### 1. 💎 Crystalline Triage Graph (Automated Bottleneck Detection)
Applies a **Barnes-Hut physics clustering algorithm** to dynamically group highly coupled operational data into distinct visual "hives."
* **Systemic Triage:** Instantly flags hyper-complex workflows (Red Nodes) and shared structural bottlenecks (Amber Nodes).
* **Visualizing Friction:** High-risk relationships (complex docs relying on shared vulnerable entities) are isolated with red dashed lines, showing teams exactly where to allocate audit hours.
<img width="778" height="506" alt="image" src="https://github.com/user-attachments/assets/5153e5b7-a665-4963-b78a-a9a170871052" />



#### 2. 🏢 Ideal Org Structure Map (AI Community Detection)
Answers the question: *"Based on how our processes actually interact, how should our teams be structured?"*
* Utilizes **NetworkX Greedy Modularity (Louvain-based algorithm)** to map the hidden structure of enterprise workflows.
* Automatically clusters highly interconnected SOPs into isolated, color-coded "Agile Org Pods."
* Provides a data-backed blueprint for departmental restructuring, minimizing inter-departmental communication overhead and silos.
<img width="656" height="452" alt="image" src="https://github.com/user-attachments/assets/645eb763-0dc3-46d9-89fb-d8b51c7797ca" />


#### 3. 🚨 Critical Path Method (CPM) Vulnerability Map
Architects a Directed Acyclic Graph (DAG) analysis to calculate the longest operational dependency chain within the knowledge base.
* Visualizes the **"Critical Path"** using weighted, high-contrast red paths.
* Isolates the exact sequence of operational documents most susceptible to cascading delays, empowering leaders to proactively fortify fragile workflows.


#### 4. 🔗 Causal AI & Counterfactual Stress Testing
* **Mathematical Ripple Effects:** Select any single point of failure (SOP) and run a "What-If" (`do-calculus`) simulation to see exactly which downstream processes will collapse.
* **Sensitivity Analysis:** Generates dynamic Dose-Response charts detailing how total system vulnerability scales as a root-cause document's failure likelihood increases from 0% to 100%.

#### 5. 📊 Executive Risk & ROI Dashboard
While the network graphs provide deep operational context for engineers, the Executive Dashboard translates graph mathematics into high-level business intelligence:
* **Vulnerability Tornado Chart:** Translates *Betweenness Centrality* scores into a ranked list of the most dangerous systemic bottlenecks.
* **Intervention ROI Waterfall:** Quantifies the exact systemic risk reduction (Return on Investment) achieved by fixing the top 3 most vulnerable SOPs.
* **Cross-Domain Contagion Heatmap:** Maps causal influence weights into a matrix, revealing hidden friction and risk transmission between different departments (e.g., IT vs. Lab Ops).

<img width="409" height="943" alt="image" src="https://github.com/user-attachments/assets/47df49bf-8eb8-4934-a497-e8999f0f6bfd" />


<img width="1147" height="558" alt="image" src="https://github.com/user-attachments/assets/9448554c-5a4c-4bd3-af18-557e838f1533" />


### 🛠️ How to Run the New UI
The new visualization engine is built on Flask, NetworkX, Matplotlib, and vis.js.

```bash
# Install dependencies
pip install flask networkx matplotlib waitress httpx

# Run the Crystalline Server
python web_crystal.py



## Related repositories

Crystalline AI brings together components demonstrated in these repos:

- **[ai-knowledge-workbench-GRAPHrag](https://github.com/daviddata-cloud/ai-knowledge-workbench-GRAPHrag)** — the GraphRAG retrieval + knowledge layer (private wiki, live web search, gap detection, multi-agent reasoning).
- 
- **[causal-ai-dag](https://github.com/daviddata-cloud/causal-ai-dag)** — the causal reasoning layer (DAG discovery, intervention, counterfactual what-if; PCMCI, do-calculus).
---
## Honest scope

This repository is an educational proof-of-concept reference pattern using synthetic or public demo data. It is not a deployed product, not legal, investment, enforcement, medical, or policy guidance, and not a claim about any real case, agency matter, company, market, or investigation.

Causal discovery, optimization, and multi-agent evaluation depend on assumptions that must be checked against real data and domain expertise. Where the method cannot decide, the uncertainty should remain visible for human review.

The goal is not automatic decision-making. The goal is to make evidence, assumptions, limitations, and review points clearer for human experts.

---
## License

MIT
---
