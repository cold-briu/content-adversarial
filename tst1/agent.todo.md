# Agent Todo

## Master Instructions

For each article listed in the checklist below:
1. **Research Main Findings Relevant to Topic**: Research and analyze the primary findings for each article, focusing on data relevant to the topic described in [`topic.json`](./topic.json) (*"The Gut-Brain Axis: Overcoming Brain Fog and Mood Instability Through Nutritional Psychiatry"*).
2. **Strict Factual Accuracy (No Fabrication or Distortion)**: Present strictly factual, objective information as reported in the article. **Do NOT fabricate, stretch, or distort data** to force it to fit the topic narrative. The goal is to provide accurate evidence so another agent can craft a reliable science divulgation script.
3. **Refer to articles.json for Links**: Refer to [`articles.json`](./articles.json) to retrieve the corresponding article metadata and links (`link` field).
4. **Output Directory and File Location**: Output all synthesized results into the YAML file `./output/findings.yaml` inside the `./output/` directory. Create the `./output/` directory if it does not already exist.
5. **Output YAML Schema & Document Structure**: For each article finding, adhere strictly to the following YAML schema and structure:
   - **`title`** (string): Exact article title matching [`articles.json`](./articles.json).
   - **`link`** (string): DOI or URL link matching [`articles.json`](./articles.json).
   - **`breakthroughs_and_insights`** (list of strings): Key discoveries, clinical mechanisms, or novel conclusions established by the research that relate to the topic.
   - **`caveats`** (list of strings): Study limitations, specific sample characteristics, or scope restrictions (e.g., *"research found correlation between meal timing and sugar in blood; caveat: only investigated in males from a specific country"*, animal model vs. human trial, small sample size, correlation vs. causation).

   **Required YAML Schema (`./output/findings.yaml`)**:
   ```yaml
   findings:
     - title: "Exact article title matching articles.json"
       link: "https://doi.org/..."
       breakthroughs_and_insights:
         - "First key discovery, clinical mechanism, or insight relevant to the topic."
         - "Second relevant finding established by the research."
       caveats:
         - "Study limitation or scope restriction (e.g., small sample size, animal vs. human trial)."
   ```
6. **Log Work in `changelog.yaml`**: For any kind of change or work performed, log an entry in [`changelog.yaml`](./changelog.yaml).
   - **Create if Missing**: If `changelog.yaml` is not present, create it in the same directory (`./changelog.yaml`).
   - **Required Log Information**: Include relevant details for each entry such as:
     - **Files Created/Modified**: Paths of any files created or updated.
     - **Blocking Findings**: Explicitly record any blocking issues or null results (e.g., *"no relevant breakthroughs regarding the topic were found"*, *"broken link"*, or inaccessible source).

---

## Articles Checklist

- [x] A randomised controlled trial of dietary improvement for adults with major depression (the 'SMILES' trial)
- [x] The neuroactive potential of the human gut microbiota in quality of life and depression
- [x] Mind-altering microorganisms: the impact of the gut microbiota on brain and behaviour
- [x] Psychobiotics: A Novel Class of Psychotropic
- [x] Gut–brain axis: how the microbiome influences anxiety and depression
- [x] Gut Microbes and the Brain: Paradigm Shift in Neuroscience
- [ ] Interactions between the microbiota, immune and nervous systems in health and disease
- [ ] Nutritional psychiatry: the present state of the evidence
- [ ] Gut microbiota composition in depressive disorder: a systematic review, meta-analysis, and meta-regression
- [ ] From Probiotics to Psychobiotics: Live Beneficial Bacteria Which Act on the Brain-Gut Axis
