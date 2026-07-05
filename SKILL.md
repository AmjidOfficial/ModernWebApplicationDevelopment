---
name: create-skill-from-conversation
related: agent-customization
scope: workspace
author: GitHub Copilot (draft)
created: 2026-05-23
---

# Skill: Create a SKILL.md from a conversation

Purpose
- Provide a repeatable method for extracting a workflow from a conversation and turning it into a reusable `SKILL.md` that an agent can run.

When to use
- The user guided a multi-step workflow in chat and wants that pattern captured as a skill.
- You need a checklist-style automation to reproduce the same extraction across conversations.

Inputs to extract
- The step-by-step process described in the conversation.
- Decision points or conditional branches used when choosing next actions.
- Any explicit quality criteria, completion checks, or acceptance conditions.
- Files, paths, or artifacts mentioned in the conversation.

Step-by-step process
1. Read the full conversation history and attached files.
2. Identify the workflow's ordered steps (tasks, sub-tasks).
3. Extract decision points (if X then Y, else Z) and list them explicitly.
4. Capture quality criteria and success checks for each step.
5. Draft the SKILL.md content using this template and include metadata.
6. Save the draft into the workspace (recommended: `SKILLs/` or root `SKILL.md`).
7. Ask clarifying questions for any ambiguous or missing pieces.
8. Iterate until acceptance, then finalize and commit the skill.

Decision points and branching
- For each step, include short if/else rules (example: "If repo contains tests then run tests; else skip").
- Prefer simple boolean checks and enumerate alternatives.

Quality criteria / Completion checks
- Steps are concrete and verifiable (e.g., file created, tests pass, file contains header).
- The skill produces at least one artifact (new file or updated file) when applicable.
- Ambiguities produce a small set of clarifying questions rather than guesses.

Examples of clarifying questions
- "Should the SKILL.md be workspace-scoped or personal?"
- "Which folder should the skill save outputs to? (root / SKILLs/ .vscode/)"
- "Any required linting or formatting rules to enforce?"

Example prompts to run this skill
- "Create a SKILL.md from our conversation about adding a CI job."
- "Extract the deployment workflow from this chat and save a SKILL.md in .vscode/skills/."

Suggested file location and naming
- Workspace-scoped skills: `SKILLs/<skill-name>.md` or root `SKILL.md`.
- Personal skills: store under your user prompts folder.

Iteration notes
- Save a draft first, ask clarifying Qs, then finalize.
- Record version or change-log lines in the header when finalizing.

Next recommended customizations
- Add example input/output pairs for the skill.
- Provide test cases or canned conversation excerpts the skill should handle.
