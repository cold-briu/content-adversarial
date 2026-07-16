# Tst2

An interactive CLI tool for science-backed short-form content creation. It orchestrates specialized AI agents (Content Strategist, Scientific Sourcing, Insights Synthesizer, and Scriptwriter) alongside a Python CLI interface to guide users from initial topic ideation to research-backed script proposals.

## Project Status

No implementation has been made so far; the system design is currently in progress.

## Execution Design

The CLI execution flow is fully described in **workflow.md** (located in the **agents** folder). This document details the step-by-step interactive workflow, defining the precise actions, inputs, and outputs required at each stage of the process.

## Folder Structure

- **agents**: Contains the execution workflow definition and maps agent roles to required skills.
- **resources**: Stores configuration files, brand guidelines, fetched scientific articles, and intermediate generation states.
- **output**: Reserved for storing final generated content scripts.

