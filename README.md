# Content Adversarial

This repository manages workflows and multi-agent systems designed to translate peer-reviewed scientific literature into engaging, fact-checked, and brand-aligned short-form video scripts (TikTok, Instagram Reels, YouTube Shorts).

## Core Focus

The workflows focus on promoting conscious, healthy, and responsible food consumption, acting as an educational counterweight to ultra-processed foods and unethical supply chains.

## Project Workflows & Structure

The repository currently contains two distinct workflow implementations:

### tst1 — File-Driven Batch Workflow
A document-driven pipeline that runs in two main phases:
*   **Research & Synthesis:** Sources scientific findings from input articles and drafts breakthroughs and caveats into a structured findings database.
*   **Script Writing:** Converts these findings into conversational, brand-aligned short-form scripts based on static brand briefings and hook guidelines.

### tst2 — Interactive Multi-Agent CLI
An interactive command-line interface that guides the user through a step-by-step content generation flow, orchestrating four specialized agents:
1.  **Content Strategist Agent:** Generates brand-aligned topic ideas tailored to target personas.
2.  **Scientific Sourcing Agent:** Sources peer-reviewed literature for the selected topic.
3.  **Insights Synthesizer Agent:** Extracts key breakthroughs and scientific limitations from the sourced literature.
4.  **Scriptwriter Agent:** Generates multiple short-form script proposals using the synthesized facts.



