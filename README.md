# Wand AI – Challenge 1 : Multi-Agent Task Solver

### 🔍 Overview
A minimal working prototype that accepts a **plain-language business request** (e.g., “Summarize the last three quarters’ financial performance and create a chart”) and executes it through a chain of specialized AI agents:

**Planner → Researcher → Coder → Analyst → Writer**

Each agent has a defined role, passes context to the next, and uses Python tools (pandas + matplotlib) for deterministic results.  
The system avoids hallucination by grounding outputs on uploaded CSV data (`sales.csv`).

---

## Architecture

| Agent | Responsibility |
|--------|----------------|
| **Planner** | Breaks request into subtasks and can ask one clarifying question if needed. |
| **Researcher** | Gathers or summarizes available data; uses uploaded CSV when present. |
| **Coder** | Detects date + amount columns, aggregates by **quarter**, plots a real chart. |
| **Analyst** | Interprets quarterly totals and calculates growth %. |
| **Writer** | Produces a short executive summary combining all prior context. |
| **Orchestrator** | Coordinates execution and maintains shared context (`ctx`). |

---

##  How to Run

### Local (Jupyter)
1. Open **`challenge_1.ipynb`** in Jupyter Lab / Notebook.  
2. Run the first cell to install dependencies:
   ```python
   !pip install -q transformers accelerate torch matplotlib pandas
