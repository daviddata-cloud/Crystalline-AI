
# Crystalline AI

**Turning complex, messy systems into ordered, optimized, self-improving ones — with a human always in the loop. Human-AI co-design.**

> One big model guesses. A crystalline agent team checks, connects, optimizes, and explains.

Crystalline AI dynamically parses synthetic operational text (such as internal Standard Operating Procedures) and mathematically maps their relationships, vulnerabilities, and bottlenecks in a live Flask application. It then applies graph analytics, Operations Research, and causal methods to turn a tangled knowledge base into a prioritized, auditable operations view.

*All demos use synthetic data only. They illustrate the method, not any real matter. The system flags candidates for human review; it does not decide outcomes. Any ROI, risk, or savings figures are illustrative on synthetic data, not real measured results.*

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

- **Each agent is a node.** Each hand-off is a directed edge. The flow has no loops within a pass — a **Directed Acyclic Graph (DAG)** — which makes it ordered, traceable, and easy to audit.
- **The reasoning layer is also a DAG.** The Relationship agent builds a graph of entities; the Causal agent uses a causal DAG (cause → effect, with the do() operator) to test whether a relationship is credible, not just correlated.
- **Why it matters:** graph structure expresses relationships a flat pipeline can't — which agent depends on which, which evidence supports which finding, and what causes what. Graph describes; Operations Research optimizes; causal DAG tests credibility; the human decides.

In short: the *architecture* is a DAG of agents, and the *reasoning* uses causal DAGs. Graph structure is what makes the system ordered ("crystalline") instead of tangled ("rock").

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

The loop is **guided** (OR sets a clear target), **measured** (every attempt is scored against the goal), **auditable** (every step is logged), and **human-checked** (an expert approves consequential changes). It is a disciplined, goal-directed improvement cycle — not an open-ended autonomous agent.

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

It records what was searched, what was found, what was *not* found, the assumptions, the confidence, and why a human should review.

---

## Modules and capabilities

Crystalline AI parses synthetic SOP documents into relationship graphs, then applies these modules. Every module is illustrative on synthetic data and routes results to a human reviewer.

### 1. Crystalline Triage Graph — automated bottleneck detection
- **Problem:** Audit and risk teams have limited time and cannot manually review hundreds of interdependent SOPs, and often don't know where the hidden structural risks are.
- **Solution:** A force-directed clustering algorithm (Barnes-Hut physics) maps document relationships and applies Operations Research triage rules to flag overly complex workflows (red nodes) and shared, high-dependency bottlenecks (amber nodes).
- **Impact:** Turns a tangled knowledge base into a prioritized operations view, directing limited expert hours to the highest-risk structural vulnerabilities.
<img width="796" height="776" alt="image" src="https://github.com/user-attachments/assets/83bf069b-fa22-4e8c-a91e-9f6e72ca8a57" />


*Figure 1. Crystalline Triage Graph — automated bottleneck detection (live, synthetic data). Red = flagged high-complexity documents; amber = shared high-dependency clusters; blue = normal docs; gray = entities. Red dashed lines isolate high-risk relationships, directing limited audit hours to the highest-risk vulnerabilities.*

### 2. Ideal Org Structure Map — AI community detection
- **Problem:** Legacy org structures often misalign with how work actually flows, causing friction, delayed hand-offs, and overhead.
- **Solution:** NetworkX greedy modularity (Louvain-based community detection) traces actual SOP dependencies and clusters them into optimized, cross-functional "agile pods."
- **Impact:** Gives leadership a data-backed view of how teams could be grouped around real workflow reality, reducing silos.

<img width="975" height="313" alt="image" src="https://github.com/user-attachments/assets/70d24b68-ac4b-4389-bb00-b7fba73d3f2a" />

*Figure 2. Ideal Org Structure Map — AI community detection (live, synthetic data). Louvain-based community detection traces SOP dependencies and clusters them into optimized cross-functional "agile pods" (green and pink).*

### 3. Critical Path (CPM) Vulnerability Map
- **Problem:** In complex systems, it is hard to see which sequence of tasks, if delayed, will cascade into system-wide failure.
- **Solution:** A Directed Acyclic Graph (DAG) algorithm computes the longest dependency chain and highlights this "critical path" in high-contrast routes.
- **Impact:** Shows where redundancy and backup resources should go to prevent a single point of failure from halting the system.

<img width="975" height="736" alt="image" src="https://github.com/user-attachments/assets/72dd41f7-daba-43ec-a8dd-526c0a012ff9" />

*Figure 3. Critical Path (CPM) Vulnerability Map (live, synthetic data). The longest dependency chain is highlighted in red, isolating the sequence of documents most susceptible to cascading delays.*

### 4. Causal AI & Counterfactual Stress Testing
- **Problem:** Predictive AI shows correlation, not intervention. It can't answer "what happens if we change this policy?" or "how much stress can the system take?"
- **Solution:** A do-calculus simulation engine lets a user select a node, inject a failure, and compute the downstream ripple effect, plus a dose-response sensitivity view across severity levels.
- **Impact:** Moves from passive prediction to strategic simulation — stress-test policies and set mathematical safety thresholds before a crisis.

<img width="975" height="461" alt="image" src="https://github.com/user-attachments/assets/884ca6dd-9c59-41ea-a2b2-c530a2ae9917" />

*Figure 4. Causal AI — Directed Acyclic Graph with "what-if" simulation (live, synthetic data). Selecting a node and injecting a failure propagates the downstream ripple effect through the causal DAG (do-calculus), producing a collateral-impact report. Edge weights are learned from synthetic data.*

<img width="975" height="414" alt="image" src="https://github.com/user-attachments/assets/6e83614d-8513-4ae5-baee-f3535feded67" />

*Figure 5. Counterfactual Stress Test — do-calculus (live, synthetic data). A system-wide or single-target intervention forces do(node = 0) and traces propagation, showing which downstream processes are affected and which are isolated.*

### 5. Executive Risk & ROI Dashboard
- **Problem:** Graph metrics like betweenness centrality and causal edge weights are too abstract for non-technical leadership.
- **Solution:** A dashboard translates graph math into business intelligence: a **Vulnerability Tornado** chart (ranked systemic bottlenecks from betweenness centrality), an **Intervention ROI Waterfall** (illustrative risk reduction from fixing top bottlenecks), and a **Cross-Domain Contagion Heatmap** (risk transmission between departments).
- **Impact:** Bridges data science and leadership, making graph analytics usable for prioritization decisions. *(All figures illustrative on synthetic data.)*

<img width="585" height="1350" alt="image" src="https://github.com/user-attachments/assets/86a08939-4817-4161-84de-d10d4e065bd3" />

*Figure 6. Executive Risk & ROI Dashboard (synthetic data). Vulnerability Tornado (betweenness-centrality bottlenecks), Intervention ROI Waterfall (risk reduction from fixing top SOPs), and Cross-Domain Contagion Heatmap (risk transmission between departments). All figures illustrative on synthetic data.*

---

## Run it

```bash
# Core demos (graph detection + Operations Research triage)
pip install networkx matplotlib
python or_with_charts.py

# Interactive UI (Flask + NetworkX + Matplotlib + vis.js)
pip install flask networkx matplotlib waitress httpx
python web_crystal.py
```

---

## Why this matters for regulated / federal work

The same pattern fits structured disclosure, risk analysis, and oversight:
- **Graph** describes relationships across records.
- **Operations Research** spends scarce expert time on the highest-risk items.
- **Causal AI** tests whether a flag is a real signal or coincidence.
- **The loop** improves the system toward a measured goal.
- **The human** decides anything consequential.

Built-in controls: permission-aware retrieval, data classification, audit logs, citation checks, run-to-run comparison, and a human review gate.

---

## The name

A rock and a crystal can contain similar material, but the crystal is stronger because its structure is ordered. Crystalline AI turns a working-but-messy AI workflow into an ordered, modular, testable system.

> The model is the brain. The architecture is the nervous system. Operations Research sets the priority. The feedback loop helps the system improve. The human expert holds the wheel.

---

## Related repositories

- **[ai-knowledge-workbench-GRAPHrag](https://github.com/daviddata-cloud/ai-knowledge-workbench-GRAPHrag)** — the GraphRAG retrieval + knowledge layer (private wiki, live web search, gap detection, multi-agent reasoning).
- **[causal-ai-dag](https://github.com/daviddata-cloud/causal-ai-dag)** — the causal reasoning layer (DAG discovery, intervention, counterfactual what-if; PCMCI, do-calculus).

---

## Honest scope

This repository is an educational proof-of-concept reference pattern using synthetic or public demo data. It is not a deployed product, and not legal, investment, enforcement, medical, or policy guidance, and not a claim about any real case, agency, company, market, or investigation. Causal discovery, optimization, and multi-agent evaluation depend on assumptions that must be checked against real data and domain expertise. Where the method cannot decide, the uncertainty stays visible for human review. The goal is not automatic decision-making — it is to make evidence, assumptions, limitations, and review points clearer for human experts.

## License
MIT

## 🚀 Latest Upgrade: From Static Charts to a Dynamic Operations Research UI

Crystalline AI has evolved from static Python/Matplotlib proof-of-concept charts into an interactive Flask-based analytical application for graph reasoning, risk triage, and executive decision support.

The current demo dynamically parses synthetic SOP-style operational documents, builds relationship graphs, and exposes multiple live analytical views through a web UI. The goal is not automatic decision-making. The goal is to help human experts see hidden structure, bottlenecks, causal exposure, and intervention priorities faster.

**Technology stack:** Python, Flask, NetworkX, vis.js, Matplotlib, graph analytics, causal DAG concepts, Operations Research triage, and human-in-the-loop review.

**Scope:** Synthetic/demo data only. The system illustrates a reusable method for regulated and enterprise workflows; it does not make claims about any real agency matter, company, case, policy, market, or investigation.
<img width="975" height="839" alt="image" src="https://github.com/user-attachments/assets/f4fc45d8-8d80-4412-9d44-82709db003a7" />

---
