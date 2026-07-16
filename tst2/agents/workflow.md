# Workflow

This document outlines the step-by-step interactive CLI workflow for content creation.

---

### Step 1: Content Pillar Sourcing
- **Data Sourcing**: User input (CLI)
- **Required Action**: Ask user for content pillars
- **Resulting Output**: `resources/config.yaml`
- **Input Example**: N/A
- **Output Example**:
  ```yaml
  pillar: "gut microbiote: Digestion, whole foods, prebiotics, nutritional psychiatry, and dietary fiber."
  ```

---

### Step 2: Tone Selection
- **Data Sourcing**: User input (CLI)
- **Required Action**: Ask user for tone preference
- **Resulting Output**: `resources/config.yaml`
- **Input Example**: N/A
- **Output Example**:
  ```yaml
  pillar: "gut microbiote: Digestion, whole foods, prebiotics, nutritional psychiatry, and dietary fiber."
  tone: "informative content, science baked, vertical content, divulagtion, ligthweight"
  ```

---

### Step 3: User Persona Building
- **Data Sourcing**: User input (CLI questionnaire)
- **Required Action**: Ask questions regarding audience, pain points, needs, fears, and aspirations
- **Resulting Output**: `resources/briefing.yaml`
- **Input Example**:
  - Audience: Eco/health conscious buyers
  - Pain Point: Wants to eat ethically/healthily but overwhelmed
  - Needs: Curated catalog & evidence-based content
- **Output Example**:
  ```yaml
  audience: "Eco/health conscious buyers"
  pain_point: "Overwhelmed with where to start"
  needs: "Curated catalog & evidence-based content"
  ```

---

### Step 4: Topic Ideas Generation
- **Data Sourcing**: CLI session state (`pillar`, `tone`, `persona`)
- **Required Action**: Generate 5 topic ideas with user value matching the persona
- **Resulting Output**: Displayed list of 5 ideas
- **Prompt Description**: "Based on the content pillar, tone, and user persona specified in resources/config.yaml and resources/briefing.yaml, generate 5 distinct, high-engagement topic ideas for short-form content. For each idea, provide the topic hook/title and explain its specific value for the user persona."
- **Input Example**: N/A (State from Steps 1-3)
- **Output Example**:
  ```yaml
  - topic: "Stop normalizing bloating"
    value: "Provides a path to peak energy by incorporating dietary fiber to rebuild gut lining."
  ```

---

### Step 5: Topic Selection
- **Data Sourcing**: User input (CLI selection)
- **Required Action**: Ask user to select one topic
- **Resulting Output**: CLI session state (`selected_topic`)
- **Input Example**: `1`
- **Output Example**: `"Stop normalizing bloating"`

---

### Step 6: Scientific Research Sourcing
- **Data Sourcing**: Agent research (academic databases / search engines)
- **Required Action**: Research 3-10 top scientific investigations for the topic and format as YAML
- **Resulting Output**: `resources/articles.yaml`
- **Prompt Description**: "Search academic databases for the top 3-10 most relevant, high-impact, peer-reviewed scientific studies regarding the selected topic: {topic}. For each study, extract the exact title, authors, publication year, publication link/DOI, and 5 core keywords. Output the results strictly as a YAML list of articles without any additional descriptions or summaries."
- **Input Example**: `"Stop normalizing bloating"`
- **Output Example**:
  ```yaml
  articles:
    - title: "A randomised controlled trial of dietary improvement for adults with major depression (the 'SMILES' trial)"
      link: "https://doi.org/10.1186/s12916-017-0791-y"
      authors: "Jacka, F. N., et al."
      year: 2017
      keywords:
        - "dietary intervention"
        - "major depression"
        - "nutritional psychiatry"
        - "clinical trial"
  ```

---

### Step 7: Article Insights and Caveats Extraction
- **Data Sourcing**: Agent research and synthesis from `resources/articles.yaml` and `resources/config.yaml`
- **Required Action**: Research the primary findings for each article, focusing on data relevant to the selected topic/pillar. Extract breakthroughs/insights and study caveats for each article.
- **Resulting Output**: `resources/findings.yaml`
- **Prompt Description**: "Research and analyze the primary findings for each article listed in resources/articles.yaml, focusing on data relevant to the topic described in resources/config.yaml. Output all synthesized results into a findings.yaml file, extracting the breakthroughs_and_insights and study caveats for each article, adhering strictly to the requested YAML schema."
- **Input Example**: N/A (State from Step 6 & config)
- **Output Example**:
  ```yaml
  findings:
    - title: "A randomised controlled trial of dietary improvement for adults with major depression (the 'SMILES' trial)"
      link: "https://doi.org/10.1186/s12916-017-0791-y"
      breakthroughs_and_insights:
        - "In a 12-week randomised controlled trial of adults with moderate to severe depression, adjunctive dietary intervention using a modified Mediterranean diet ('ModiMedDiet') produced significantly greater improvement in depression symptoms (MADRS score) than a social support control condition (p < 0.001, Cohen's d = -1.16)."
      caveats:
        - "Small sample size (67 enrolled, 56 completed: 31 in dietary support and 25 in control), limiting statistical power for secondary outcomes and subgroup analyses."
  ```

---

### Step 8: Cool Fact Selection and Approval
- **Data Sourcing**: Agent synthesis from `resources/findings.yaml` & User input (CLI review)
- **Required Action**: Identify 5 "cool facts" based on the extracted findings and insights. The user can discard, accept, or request more facts to be generated and appended before moving forward.
- **Resulting Output**: `resources/facts.yaml`
- **Prompt Description**: "Based on the findings in resources/findings.yaml, select 5 compelling 'cool facts' suitable for scriptwriting. Present them to the user. Allow the user to accept, discard, or request more facts. Append any requested additions to the list, and output the final approved facts to resources/facts.yaml."
- **Input Example**: N/A (State from Step 7)
- **Output Example**:
  ```yaml
  facts:
    - id: 1
      cool_fact: "Switching to a Mediterranean-style diet for 12 weeks significantly reduced depression symptoms — and 32% of participants actually went into remission, compared to only 8% in the control group."
    - id: 2
      cool_fact: "Specific gut bacteria — Coprococcus and Dialister — were found depleted in people with depression, even after accounting for antidepressant use, suggesting a direct microbial link to mental health."
  ```
