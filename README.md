## 🚀 Latest Upgrade: From Static Charts to a Dynamic Operations Research UI

Crystalline AI has evolved from static Python/Matplotlib proof-of-concept charts into an interactive Flask-based analytical application for graph reasoning, risk triage, and executive decision support.

The current demo dynamically parses synthetic SOP-style operational documents, builds relationship graphs, and exposes multiple live analytical views through a web UI. The goal is not automatic decision-making. The goal is to help human experts see hidden structure, bottlenecks, causal exposure, and intervention priorities faster.

**Technology stack:** Python, Flask, NetworkX, vis.js, Matplotlib, graph analytics, causal DAG concepts, Operations Research triage, and human-in-the-loop review.

**Scope:** Synthetic/demo data only. The system illustrates a reusable method for regulated and enterprise workflows; it does not make claims about any real agency matter, company, case, policy, market, or investigation.
<img width="975" height="839" alt="image" src="https://github.com/user-attachments/assets/f4fc45d8-8d80-4412-9d44-82709db003a7" />

---

## Dynamic Analytical Modules

### 1. 💎 Crystalline Triage Graph — Automated Bottleneck Detection

**Problem:** Audit teams and risk managers cannot manually inspect every complex SOP, dependency, and workflow relationship. Hidden risk often lives in shared dependencies, overly complex workflows, and cross-document bottlenecks.

**Solution:** Built a dynamic graph visualization that uses force-directed clustering to map relationships among operational documents, entities, and shared dependencies. The system applies Operations Research triage rules to flag high-complexity workflows, shared bottlenecks, and relationship paths that deserve human review.

**Impact:** Converts a messy operational knowledge base into a prioritized review map. Instead of asking experts to inspect everything, the graph identifies where limited review time should go first.
<img width="975" height="788" alt="image" src="https://github.com/user-attachments/assets/8528640c-63cc-46da-b3f1-cdee67c65ba4" />

**What the viewer can see:**
- Red nodes: high-complexity or high-risk workflow documents.
- Amber nodes: shared dependency bottlenecks.
- Dashed/high-risk edges: relationships that may transmit operational friction or risk.
- Interactive graph layout: users can inspect clusters, dependencies, and priority targets.

---

### 2. 🏢 Ideal Org Structure Map — AI Community Detection

**Problem:** Formal organizational charts often do not match how work actually flows. Teams may be organized by legacy departments while daily dependencies cross multiple silos.

**Solution:** Applied community-detection logic to SOP dependency graphs to identify natural clusters of highly connected workflows. The output groups related processes into proposed “operational pods” based on actual dependency structure rather than administrative assumptions.

**Impact:** Gives leaders a data-backed way to discuss restructuring, handoff reduction, and cross-functional workflow design.
<img width="975" height="635" alt="image" src="https://github.com/user-attachments/assets/e9f5e548-917f-4ac0-b385-1ce11c3f908f" />
<img width="975" height="313" alt="image" src="https://github.com/user-attachments/assets/f23b1d6b-91d7-4e63-972a-e39a4d008d29" />

**What the viewer can see:**
- Color-coded workflow communities.
- Highly connected SOP clusters.
- Cross-silo dependencies that may cause coordination friction.
- Candidate “agile org pods” based on real workflow structure.

---

### 3. 🚨 Critical Path Method Map — Dependency Vulnerability Detection

**Problem:** In complex operations, a single fragile sequence of dependencies can create cascading delay or failure, but that path is difficult to see from tables or documents alone.

**Solution:** Modeled SOP dependencies as a directed graph and identified the longest/highest-exposure dependency chain. The UI highlights the critical path so reviewers can see which sequence of tasks needs redundancy, backup capacity, or policy attention.

**Impact:** Helps operations leaders identify where one weak link could disrupt the broader workflow.
<img width="975" height="736" alt="image" src="https://github.com/user-attachments/assets/feffb7d1-15f2-4e3c-987d-9525c8ebdaf3" />

**What the viewer can see:**
- Critical dependency path highlighted in high contrast.
- Supporting dependencies shown in lower contrast.
- Specific SOP sequence most vulnerable to cascading delay.
- Candidate points for redundancy or intervention.

---

### 4. 🔗 Causal AI & Counterfactual Stress Testing

**Problem:** Predictive AI can show correlation, but risk leaders often need intervention answers: “What happens if this process fails?” or “How much stress can the system tolerate?”

**Solution:** Built a DAG-style counterfactual simulation layer that lets a user select a root node, inject a synthetic failure or stress level, and observe downstream ripple effects. A dynamic sensitivity chart shows how vulnerability scales as the root-cause failure probability increases.

**Impact:** Moves the demo from passive prediction toward active scenario testing. It gives risk reviewers a way to reason about thresholds, downstream exposure, and human review priorities before a real incident occurs.
<img width="975" height="461" alt="image" src="https://github.com/user-attachments/assets/f9a59c6a-1769-4a5d-952d-0cb20e0c6d08" />
<img width="975" height="414" alt="image" src="https://github.com/user-attachments/assets/015998b1-04ac-47c6-ac94-a7b1cd3f68f7" />

**What the viewer can see:**
- Selectable intervention target.
- Downstream impact report.
- Directed causal/risk graph.
- Dose-response sensitivity curve from low to high stress.

---

### 5. 📊 Executive Risk & ROI Dashboard

**Problem:** Graph metrics such as betweenness centrality, dependency length, and causal edge weights are useful to data scientists, but too abstract for executive budget or policy decisions.

**Solution:** Built an executive dashboard that translates graph mathematics into decision-oriented views:
- **Vulnerability Tornado Chart:** ranks the most important systemic bottlenecks.
- **Intervention ROI Waterfall:** estimates how much systemic risk falls after fixing top vulnerabilities.
- **Cross-Domain Contagion Heatmap:** shows where risk may transmit across workflow domains.

**Impact:** Bridges data science and leadership action. The dashboard explains which interventions give the largest risk reduction and why those items should be prioritized.
<img width="585" height="1350" alt="image" src="https://github.com/user-attachments/assets/027fab76-8ff8-4816-a6fa-e510274e9329" />

**What the viewer can see:**
- Ranked bottlenecks for review or investment.
- Stepwise risk reduction from selected interventions.
- Cross-domain risk transmission patterns.
- Plain-English interpretation of graph analytics.

---

## Interview Summary

This project demonstrates the migration from static analytics to a dynamic AI decision-support application:

> I migrated Crystalline AI from static synthetic Python chart scripts into a live Flask-based graph analytics application. The upgraded system uses NetworkX and vis.js to provide dynamic triage graphs, community detection, critical path analysis, causal stress testing, and executive risk dashboards. The work demonstrates responsible AI design: synthetic data, visible assumptions, reproducible workflows, audit-friendly outputs, and human review before consequential decisions.
<img width="975" height="598" alt="image" src="https://github.com/user-attachments/assets/151e5e58-3f38-4344-8e7c-0269d5e0a16f" />
