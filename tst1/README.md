# `tst1` Content Generation Workflow

This directory uses a two-phase workflow to turn peer-reviewed scientific literature into engaging, fact-checked, brand-aligned short-form video scripts (TikTok, Reels, Shorts).

## Workflow Phases

### Phase 1: Research & Synthesis (Research Agent)
Following instructions in `agent.todo.md`:

0. **Workflow Input:** The user provides `articles.json`, which serves as the starting point of the entire workflow.
1. **Source Articles:** Pulls research references and metadata from the provided `articles.json`.
2. **Topic Alignment:** Researches findings relevant to the topic in `topic.json`.
3. **Database Creation:** Synthesizes facts and limitations into `findings.yaml` (categorized by breakthroughs and caveats).
4. **Log:** Tracks progress in `changelog.yaml`.
`
### Phase 2: Script Writing (Writer Agent)
Following instructions in `agent.writer.md`:
1. **Extraction:** Selects 5 key facts from `findings.yaml`.
2. **Writing:** Drafts 5 scripts (between 120–145 words) in a peer-to-peer, conversational tone, incorporating:
   * Brand guidelines from `briefing.md`.
   * Script hooks aligned with `hook-guide.md` (providing 3 hook options per script).
   * Factual attributing phrases (e.g., *"according to research"*) and a final question-inducing closer.
3. **Output:** Saves the compiled scripts to `scripts.yaml`.
4. **Log:** Tracks progress in `changelog.yaml`.
