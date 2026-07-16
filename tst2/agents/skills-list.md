# Agent Roles and Skills List (Summarized)

This document maps the interactive content creation workflow in [workflow.md](file:///home/sandusky/repos/content-adversarial/tst2/agents/workflow.md) to specialized agent roles, core skills, and data contracts. The CLI itself is a Python application that orchestrates the flow and manages user inputs directly, rather than an LLM-based agent.

---

## 1. Roles and Workflow Mapping

| Agent/Component | Workflow Steps | Primary Inputs / Outputs |
| :--- | :--- | :--- |
| **Python CLI Application** | Steps 1, 2, 3, 4, 6, 9 | User inputs, brand guidelines / orchestrates file updates and LLM calls |
| **Content Strategist Agent** | Step 5 | Persona and Brand state / 5 topic ideas |
| **Scientific Sourcing Agent** | Step 7 | Selected topic / `articles.yaml` (metadata) |
| **Insights Synthesizer Agent** | Steps 8, 9 | Sourced articles / `findings.yaml`, `facts.yaml` (drafts) |

---

## 2. Core Skills & Responsibilities

### A. Python CLI Application (Orchestrator)
* **Objective:** Serve as the interactive interface and execution coordinator (no LLM logic required for structure).
* **Key Responsibilities:**
  * Collect user input for pillars, tone, and personas (Steps 1, 2, 3).
  * Pull and load brand guidelines, tone constraints, and core values (Step 4).
  * Render topic selection menus and handle choices (Step 6).
  * Trigger LLM calls to the agents.
  * Facilitate interactive review/approval loops for facts (Step 9) and update `facts.yaml`.

### B. Content Strategist Agent (LLM)
* **Objective:** Generate persona-aligned, brand-compliant, engaging topic ideas.
* **Core Skills:**
  * **Persona & Brand Alignment:** Translate persona needs & pain points into relevant topics while respecting brand values and voice constraints.
  * **Hook Design:** Craft high-CTR hooks fitting the requested brand tone and style.

### C. Scientific Sourcing Agent (LLM / Tool-Enabled)
* **Objective:** Search and fetch peer-reviewed literature metadata.
* **Core Skills:**
  * **Academic Search & Tools:** Formulate queries and use search tools to locate high-quality, peer-reviewed sources.
  * **Metadata Extraction:** Extract structured study info (title, authors, year, link) to `articles.yaml`.

### D. Research Insights Synthesizer Agent (LLM)
* **Objective:** Extract findings/limitations and translate them into digestible facts.
* **Core Skills:**
  * **Literature Synthesis:** Extract scientific breakthroughs and study caveats (limitations, sample sizes).
  * **Factual Translation:** Convert dense studies into clear, conversational, and scientifically honest "cool facts" (`findings.yaml` & `facts.yaml`).

---

## 3. Data Interface Schema Reference

- **`resources/config.yaml`**: Key-value pairs for `pillar` (string) and `tone` (string).
- **`resources/briefing.yaml`**: Target audience details (`audience`, `pain_point`, `needs`).
- **`resources/brand.yaml`**: Brand values (`brand_values`) list and tone/voice guidelines (`tone_guidelines`).
- **`resources/articles.yaml`**: List of fetched research articles containing `title`, `link`, `authors`, `year`, and `keywords`.
- **`resources/findings.yaml`**: In-depth breakdown per article showing `breakthroughs_and_insights` and `caveats` (limitations).
- **`resources/facts.yaml`**: User-approved list of structured `cool_fact` entries keyed by `id`.
