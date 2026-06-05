# Mighty Brainiac — Second Brain Vault Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use `superpowers:subagent-driven-development` (recommended) or `superpowers:executing-plans` to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build a terminal-native Markdown knowledge vault for an Applied AI Engineering curriculum — structured folder hierarchy, CLAUDE.md as the active brain, phase files, templates, and resource tracking — ready to use from session one.

**Architecture:** Plain Markdown files in a purpose-driven folder hierarchy. No code, no dependencies, no build step. CLAUDE.md at the repo root acts as Claude's operating manual and live session state. Git tracks all changes. Every file is Obsidian-compatible for a future upgrade with zero migration cost.

**Tech Stack:** Markdown, Git, Claude Code

---

## File Map

| File | Purpose |
|---|---|
| `CLAUDE.md` | Brain: operating manual + live session state |
| `curriculum/roadmap.md` | Master roadmap: all phases + Anthropic Academy + supplementary |
| `curriculum/phase-1-foundations.md` | Phase 1 topic table, projects, resources |
| `curriculum/phase-2-open-source.md` | Phase 2 topic table, projects, resources |
| `curriculum/phase-3-rag.md` | Phase 3 topic table, projects, resources |
| `curriculum/phase-4-training.md` | Phase 4 topic table, projects, resources |
| `curriculum/phase-5-agents-deployment.md` | Phase 5 topic table, projects, resources |
| `curriculum/anthropic-academy/overview.md` | Academy track overview + all completion status |
| `curriculum/anthropic-academy/module-a-claude-api.md` | Module A detail |
| `curriculum/anthropic-academy/module-b-mcp.md` | Module B detail |
| `curriculum/anthropic-academy/module-c-agents.md` | Module C detail |
| `concepts/_template.md` | Concept note template — copy for every new concept |
| `sessions/_template.md` | Session log template — copy for every study session |
| `resources/courses.md` | Course index: Udemy + Academy completion tracking |
| `resources/reading-list.md` | Articles, docs, papers |
| `inbox/.gitkeep` | Keeps inbox/ tracked by git when empty |
| `projects/.gitkeep` | Keeps projects/ tracked by git when empty |

---

## Task 1: Initialize Directory Structure and Git

**Files:**
- Create: `inbox/.gitkeep`
- Create: `projects/.gitkeep`
- Create: `concepts/.gitkeep` (replaced later by `_template.md`)
- Create: `sessions/.gitkeep` (replaced later by `_template.md`)
- Create: `curriculum/anthropic-academy/.gitkeep`
- Create: `resources/.gitkeep`

- [ ] **Step 1: Verify the repo is not yet initialized**

```bash
ls /Users/vladimir.cutkovic/Documents/code/mighty-brainiac
```
Expected: only `docs/` and `.remember/` — no `CLAUDE.md`, no `curriculum/`

- [ ] **Step 2: Create all directories with gitkeep placeholders**

```bash
mkdir -p curriculum/anthropic-academy concepts inbox projects sessions resources
touch inbox/.gitkeep projects/.gitkeep concepts/.gitkeep sessions/.gitkeep resources/.gitkeep curriculum/anthropic-academy/.gitkeep
```

- [ ] **Step 3: Initialize git**

```bash
git init
git add .
git commit -m "chore: initialize vault directory structure"
```

Expected: `Initialized empty Git repository` then commit confirmation.

- [ ] **Step 4: Verify structure**

```bash
find . -not -path './.git/*' -not -path './.remember/*' | sort
```

Expected output includes: `./concepts/.gitkeep`, `./curriculum/anthropic-academy/.gitkeep`, `./inbox/.gitkeep`, `./projects/.gitkeep`, `./sessions/.gitkeep`, `./resources/.gitkeep`

---

## Task 2: Concept Note Template

**Files:**
- Create: `concepts/_template.md`
- Delete: `concepts/.gitkeep`

- [ ] **Step 1: Verify the template doesn't exist yet**

```bash
ls concepts/
```
Expected: only `.gitkeep`

- [ ] **Step 2: Create the template**

Create `concepts/_template.md` with this exact content:

```markdown
---
topic: TOPIC_NAME
phase: PHASE_ID
status: learning
tags: []
source:
---

## Core Idea
One paragraph in your own words. Written as if explaining to a colleague.
This section is mandatory — it is the primary learning act.

## Key Points
-

## Code Blueprint (optional)
Include only when a runnable example adds genuine clarity.

## Open Questions
- [ ]

## Related Concepts
-
```

- [ ] **Step 3: Verify the template has all required frontmatter fields**

```bash
grep -c "^topic:\|^phase:\|^status:\|^tags:\|^source:" concepts/_template.md
```
Expected: `5`

- [ ] **Step 4: Verify the template has all required sections**

```bash
grep -c "^## Core Idea\|^## Key Points\|^## Open Questions\|^## Related Concepts" concepts/_template.md
```
Expected: `4`

- [ ] **Step 5: Remove gitkeep and commit**

```bash
rm concepts/.gitkeep
git add concepts/
git commit -m "feat: add concept note template"
```

---

## Task 3: Session Log Template

**Files:**
- Create: `sessions/_template.md`
- Delete: `sessions/.gitkeep`

- [ ] **Step 1: Verify the template doesn't exist yet**

```bash
ls sessions/
```
Expected: only `.gitkeep`

- [ ] **Step 2: Create the template**

Create `sessions/_template.md` with this exact content:

```markdown
# Session — YYYY-MM-DD

## What I Covered
-

## What Clicked
-

## Needs More Work
- [ ]

## Concepts Created / Updated
-

## Next Session

```

- [ ] **Step 3: Verify required sections exist**

```bash
grep -c "^## What I Covered\|^## What Clicked\|^## Needs More Work\|^## Concepts Created\|^## Next Session" sessions/_template.md
```
Expected: `5`

- [ ] **Step 4: Remove gitkeep and commit**

```bash
rm sessions/.gitkeep
git add sessions/
git commit -m "feat: add session log template"
```

---

## Task 4: Write CLAUDE.md

**Files:**
- Create: `CLAUDE.md`

- [ ] **Step 1: Verify CLAUDE.md doesn't exist yet**

```bash
ls CLAUDE.md 2>&1
```
Expected: `ls: cannot access 'CLAUDE.md': No such file or directory`

- [ ] **Step 2: Create CLAUDE.md**

Create `CLAUDE.md` with this exact content:

```markdown
# Mighty Brainiac — AI Engineering Curriculum

## Who I Am
Vladimir, aspiring Applied AI Engineer. Goal: job-ready in ~3 months.
Primary resource: Udemy "Mastering Generative AI and LLMs" (Ed Donner, 8 weeks).
Parallel track: Anthropic Academy (Claude API + MCP + Agents certification path).

## Current State
- **Active Phase:** Phase 1 — Foundations & Frontier APIs
- **Current Topic:** (update each session)
- **Last Session:** (date)
- **Next Action:** (update each session)

## Roadmap Snapshot
| Phase | Topic                          | Status       |
|-------|--------------------------------|--------------|
| 1     | Foundations & Frontier APIs    | 🔄 Active    |
| 2     | Open Source & Model Selection  | ⬜ Not started |
| 3     | RAG & Knowledge Systems        | ⬜ Not started |
| 4     | Training & Fine-tuning         | ⬜ Not started |
| 5     | Agents & Production Deployment | ⬜ Not started |
| AA    | Anthropic Academy (parallel)   | 🔄 Active    |

## Commands — How to Use This Vault
- **"resume"**                        → Read this file, tell me where I left off and what's next
- **"process inbox"**                 → Transform raw notes in /inbox into structured concept files
- **"quiz me on [topic]"**            → Generate 5 questions from the concept note for [topic]
- **"research [topic]"**              → Deep dive, create or update a concept note
- **"mark [topic] done"**             → Update roadmap, suggest next topic
- **"create project for [concept]"**  → Scaffold a coding sandbox in /projects
- **"log session"**                   → Write today's session file, update Current State above
- **"what have I learned about [topic]"** → Search concepts/ and sessions/ and summarize

## Conventions
- Concept notes live in /concepts/, named kebab-case (e.g. vector-databases.md)
- Copy concepts/_template.md for every new concept note
- Copy sessions/_template.md for every new session log, name it YYYY-MM-DD.md
- Roadmap status: ✅ Done · 🔄 Active · ⬜ Not started · ❓ Needs review
- Raw material always goes to /inbox/ first — never directly into /concepts/
- Every concept note must have a Core Idea written in your own words
- Code Blueprint in concept notes is optional — include only when a runnable example adds genuine clarity
- Claude-synthesized content in concept notes is marked with `[Claude]` so you know what came from your sources vs. what Claude added

## Session Protocol
**Start:** Type "resume" — Claude reads this file and tells you exactly where to pick up.
**End:** Type "log session" — Claude writes the session file and updates Current State above.
```

- [ ] **Step 3: Verify all required sections exist**

```bash
grep -c "^## Who I Am\|^## Current State\|^## Roadmap Snapshot\|^## Commands\|^## Conventions\|^## Session Protocol" CLAUDE.md
```
Expected: `6`

- [ ] **Step 4: Commit**

```bash
git add CLAUDE.md
git commit -m "feat: add CLAUDE.md — vault brain and operating manual"
```

---

## Task 5: Write Master Roadmap

**Files:**
- Create: `curriculum/roadmap.md`

- [ ] **Step 1: Verify it doesn't exist**

```bash
ls curriculum/roadmap.md 2>&1
```
Expected: `No such file or directory`

- [ ] **Step 2: Create curriculum/roadmap.md**

```markdown
# Applied AI Engineering — Master Roadmap

**Goal:** Job-ready Applied AI Engineer in ~3 months
**Primary Course:** Mastering Generative AI and LLMs (Ed Donner, 8 weeks, Udemy)
**Parallel Track:** Anthropic Academy — [anthropic.skilljar.com](https://anthropic.skilljar.com) (free)
**Reference:** [roadmap.sh/ai-engineer](https://roadmap.sh/ai-engineer)

---

## Primary Track

| Phase | Name | Udemy Weeks | Status | Detail |
|---|---|---|---|---|
| 1 | Foundations & Frontier APIs | 1–2 | 🔄 Active | [phase-1-foundations.md](phase-1-foundations.md) |
| 2 | Open Source & Model Selection | 3–4 | ⬜ | [phase-2-open-source.md](phase-2-open-source.md) |
| 3 | RAG & Knowledge Systems | 5 | ⬜ | [phase-3-rag.md](phase-3-rag.md) |
| 4 | Training & Fine-tuning | 6–7 | ⬜ | [phase-4-training.md](phase-4-training.md) |
| 5 | Agents & Production Deployment | 8 | ⬜ | [phase-5-agents-deployment.md](phase-5-agents-deployment.md) |

## Anthropic Academy Track (Parallel)

| Module | Name | Run With | Status | Detail |
|---|---|---|---|---|
| A | Claude API Mastery | Phase 1 | 🔄 Active | [module-a-claude-api.md](anthropic-academy/module-a-claude-api.md) |
| B | MCP & Tool Ecosystem | Phase 3 | ⬜ | [module-b-mcp.md](anthropic-academy/module-b-mcp.md) |
| C | Agents & Cloud Deployment | Phase 5 | ⬜ | [module-c-agents.md](anthropic-academy/module-c-agents.md) |

## Supplementary Topics

Fill these in as you encounter gaps during the primary track.

| Topic | Status | Concept Note | Why It Matters |
|---|---|---|---|
| LangGraph | ⬜ | — | Stateful agents — not covered in course |
| LangSmith / Langfuse | ⬜ | — | Observability & tracing for LLM apps |
| Ragas | ⬜ | — | RAG evaluation framework |
| FastAPI for AI services | ⬜ | — | Production API wrapping |
| Containerization basics | ⬜ | — | Deployment fundamentals |
| Context engineering | ⬜ | — | How to structure context — distinct from prompt engineering |
| Prompt caching | ⬜ | — | Cuts API costs 80–90% on repeated context |
| Prompt injection attacks | ⬜ | — | Critical security vulnerability in every LLM app |
| AI safety, bias & fairness basics | ⬜ | — | Required knowledge for any AI engineering role |
| OpenRouter | ⬜ | — | Model routing & fallbacks across providers |
| Claude Agent SDK | ⬜ | — | Anthropic's agent SDK — extends the Academy track |
```

- [ ] **Step 3: Verify all 5 primary phases are in the file**

```bash
grep -c "phase-1-foundations\|phase-2-open-source\|phase-3-rag\|phase-4-training\|phase-5-agents" curriculum/roadmap.md
```
Expected: `5`

- [ ] **Step 4: Commit**

```bash
git add curriculum/roadmap.md
git commit -m "feat: add master roadmap with primary and Academy tracks"
```

---

## Task 6: Phase 1 Detail File

**Files:**
- Create: `curriculum/phase-1-foundations.md`

- [ ] **Step 1: Create the file**

```markdown
# Phase 1 — Foundations & Frontier APIs

**Udemy Weeks:** 1–2
**Status:** 🔄 Active
**Parallel Academy Module:** [Module A — Claude API Mastery](anthropic-academy/module-a-claude-api.md)

## Overview
Build the foundational mental model for how LLMs work, master the major Frontier APIs, and develop core prompt engineering skills. Covers transformer architecture, LLM parameters, all major prompting techniques, multi-modal inputs, function calling, and streaming. Two projects ground everything in working code.

## Topics

| Topic | Status | Concept Note |
|---|---|---|
| Transformer architecture fundamentals | ⬜ | — |
| How LLMs work (tokens, context window, inference) | ⬜ | — |
| Frontier model landscape (GPT-4o, Claude, Gemini, DeepSeek) | ⬜ | — |
| Closed vs open-source models — when to use which | ⬜ | — |
| OpenAI / Anthropic API integration | ⬜ | — |
| LLM parameters: temperature, top-k, top-p, sampling | ⬜ | — |
| Prompt engineering fundamentals | ⬜ | — |
| Zero-shot, few-shot, and chain-of-thought prompting | ⬜ | — |
| ReAct prompting pattern | ⬜ | — |
| System prompting & role/behavior design | ⬜ | — |
| Structured outputs & constrained generation | ⬜ | — |
| Multi-modal inputs (text, images, audio) | ⬜ | — |
| Function calling & tool use | ⬜ | — |
| Streaming responses | ⬜ | — |

## Projects

| Project | Status | Folder |
|---|---|---|
| Project 1: AI brochure generator (web scraping + LLM) | ⬜ | — |
| Project 2: Multi-modal customer support chatbot (UI + function calling) | ⬜ | — |

## Resources
- Course: Udemy — Weeks 1–2 (Ed Donner)
- Parallel: [Module A — Claude API Mastery](anthropic-academy/module-a-claude-api.md)

## Session Notes
(link to relevant session files as you study this phase)
```

- [ ] **Step 2: Verify topic count**

```bash
grep -c "^| " curriculum/phase-1-foundations.md
```
Expected: `18` or more (14 topics + 2 projects + header rows)

- [ ] **Step 3: Commit**

```bash
git add curriculum/phase-1-foundations.md
git commit -m "feat: add Phase 1 detail file — Foundations & Frontier APIs"
```

---

## Task 7: Phase 2 Detail File

**Files:**
- Create: `curriculum/phase-2-open-source.md`

- [ ] **Step 1: Create the file**

```markdown
# Phase 2 — Open Source & Model Selection

**Udemy Weeks:** 3–4
**Status:** ⬜ Not started
**Parallel Academy Module:** None (Academy modules align with Phases 1, 3, 5)

## Overview
Expand beyond closed-source APIs into the open-source ecosystem. Learn to use HuggingFace, run models locally with Ollama, and develop a systematic framework for choosing the right model for any given task. Two projects — a meeting minutes tool and a code translator — build real multi-modal and code-generation skills.

## Topics

| Topic | Status | Concept Note |
|---|---|---|
| HuggingFace ecosystem (Transformers, Hub, Spaces, Inference SDK) | ⬜ | — |
| Open-source models (Llama, Mistral, Qwen, Gemma) | ⬜ | — |
| Ollama — running models locally for free dev/testing | ⬜ | — |
| 10 common GenAI use cases | ⬜ | — |
| LLM selection criteria for tasks | ⬜ | — |
| Code generation with LLMs | ⬜ | — |
| Audio processing with open + closed source models | ⬜ | — |

## Projects

| Project | Status | Folder |
|---|---|---|
| Project 3: Meeting minutes tool from audio (open + closed source) | ⬜ | — |
| Project 4: Python → C++ code translator (60,000x performance) | ⬜ | — |

## Resources
- Course: Udemy — Weeks 3–4 (Ed Donner)
- HuggingFace docs: huggingface.co/docs
- Ollama: ollama.ai

## Session Notes
(link to relevant session files as you study this phase)
```

- [ ] **Step 2: Verify required sections**

```bash
grep -c "^## Overview\|^## Topics\|^## Projects\|^## Resources\|^## Session Notes" curriculum/phase-2-open-source.md
```
Expected: `5`

- [ ] **Step 3: Commit**

```bash
git add curriculum/phase-2-open-source.md
git commit -m "feat: add Phase 2 detail file — Open Source & Model Selection"
```

---

## Task 8: Phase 3 Detail File

**Files:**
- Create: `curriculum/phase-3-rag.md`

- [ ] **Step 1: Create the file**

```markdown
# Phase 3 — RAG & Knowledge Systems

**Udemy Weeks:** 5
**Status:** ⬜ Not started
**Parallel Academy Module:** [Module B — MCP & Tool Ecosystem](anthropic-academy/module-b-mcp.md)

## Overview
The most directly employable skill set in applied AI engineering. Master embeddings, vector databases, and the full RAG pipeline from chunking strategy to retrieval. Learn when to use RAG vs fine-tuning — a decision framework that appears in every AI engineering interview. The project builds a full knowledge-worker product similar to real market solutions.

## Topics

| Topic | Status | Concept Note |
|---|---|---|
| Embeddings & similarity search | ⬜ | — |
| Sentence Transformers (local embedding models) | ⬜ | — |
| Indexing embeddings & retrieval process | ⬜ | — |
| Performing similarity / semantic search | ⬜ | — |
| Vector databases (Chroma, FAISS, Pinecone, Qdrant, Weaviate) | ⬜ | — |
| Chunking strategies (fixed, recursive, semantic) | ⬜ | — |
| RAG pipeline end-to-end | ⬜ | — |
| RAG with dynamic filters | ⬜ | — |
| RAG vs fine-tuning — decision framework | ⬜ | — |

## Projects

| Project | Status | Folder |
|---|---|---|
| Project 5: AI knowledge worker — company Q&A over internal docs | ⬜ | — |

## Resources
- Course: Udemy — Week 5 (Ed Donner)
- Parallel: [Module B — MCP & Tool Ecosystem](anthropic-academy/module-b-mcp.md)
- LangChain RAG docs, Chroma docs, Pinecone docs

## Session Notes
(link to relevant session files as you study this phase)
```

- [ ] **Step 2: Verify required sections**

```bash
grep -c "^## Overview\|^## Topics\|^## Projects\|^## Resources\|^## Session Notes" curriculum/phase-3-rag.md
```
Expected: `5`

- [ ] **Step 3: Commit**

```bash
git add curriculum/phase-3-rag.md
git commit -m "feat: add Phase 3 detail file — RAG & Knowledge Systems"
```

---

## Task 9: Phase 4 Detail File

**Files:**
- Create: `curriculum/phase-4-training.md`

- [ ] **Step 1: Create the file**

```markdown
# Phase 4 — Training & Fine-tuning

**Udemy Weeks:** 6–7
**Status:** ⬜ Not started
**Parallel Academy Module:** None (Academy modules align with Phases 1, 3, 5)

## Overview
Cross the line from inference (calling models) to training (shaping them). Fine-tune both Frontier models via API and open-source models locally using QLoRA. This phase marks a significant skills milestone — most engineers stop at inference; fine-tuning separates applied AI engineers from API consumers.

## Topics

| Topic | Status | Concept Note |
|---|---|---|
| Inference vs training distinction | ⬜ | — |
| Fine-tuning Frontier models (OpenAI fine-tune API) | ⬜ | — |
| QLoRA & parameter-efficient fine-tuning | ⬜ | — |
| Open-source model specialization | ⬜ | — |

## Projects

| Project | Status | Folder |
|---|---|---|
| Project 6: Capstone A — Price prediction with Frontier models | ⬜ | — |
| Project 7: Capstone B — Fine-tuned OSS model to compete with Frontier | ⬜ | — |

## Resources
- Course: Udemy — Weeks 6–7 (Ed Donner)
- HuggingFace PEFT docs (for QLoRA)
- OpenAI Fine-tuning docs

## Session Notes
(link to relevant session files as you study this phase)
```

- [ ] **Step 2: Verify required sections**

```bash
grep -c "^## Overview\|^## Topics\|^## Projects\|^## Resources\|^## Session Notes" curriculum/phase-4-training.md
```
Expected: `5`

- [ ] **Step 3: Commit**

```bash
git add curriculum/phase-4-training.md
git commit -m "feat: add Phase 4 detail file — Training & Fine-tuning"
```

---

## Task 10: Phase 5 Detail File

**Files:**
- Create: `curriculum/phase-5-agents-deployment.md`

- [ ] **Step 1: Create the file**

```markdown
# Phase 5 — Agents & Production Deployment

**Udemy Weeks:** 8
**Status:** ⬜ Not started
**Parallel Academy Module:** [Module C — Agents & Cloud Deployment](anthropic-academy/module-c-agents.md)

## Overview
Bring everything together into production-grade, agentic AI systems. Build multi-agent architectures where models collaborate autonomously. Learn to manage context at scale, handle external memory, and deploy with polished UIs. The capstone project is a fully autonomous, multi-agent system deployed to production.

## Topics

| Topic | Status | Concept Note |
|---|---|---|
| Agentic workflows & tool orchestration | ⬜ | — |
| Multi-agent systems | ⬜ | — |
| Context management in agents (compaction, isolation) | ⬜ | — |
| External memory patterns for agents | ⬜ | — |
| Gradio for production UIs | ⬜ | — |
| Cloud deployment | ⬜ | — |

## Projects

| Project | Status | Folder |
|---|---|---|
| Project 8: Capstone C — Autonomous deal-spotting multi-agent system | ⬜ | — |

## Resources
- Course: Udemy — Week 8 (Ed Donner)
- Parallel: [Module C — Agents & Cloud Deployment](anthropic-academy/module-c-agents.md)
- Gradio docs, LangGraph docs

## Session Notes
(link to relevant session files as you study this phase)
```

- [ ] **Step 2: Verify required sections**

```bash
grep -c "^## Overview\|^## Topics\|^## Projects\|^## Resources\|^## Session Notes" curriculum/phase-5-agents-deployment.md
```
Expected: `5`

- [ ] **Step 3: Commit**

```bash
git add curriculum/phase-5-agents-deployment.md
git commit -m "feat: add Phase 5 detail file — Agents & Production Deployment"
```

---

## Task 11: Anthropic Academy Files

**Files:**
- Create: `curriculum/anthropic-academy/overview.md`
- Create: `curriculum/anthropic-academy/module-a-claude-api.md`
- Create: `curriculum/anthropic-academy/module-b-mcp.md`
- Create: `curriculum/anthropic-academy/module-c-agents.md`
- Delete: `curriculum/anthropic-academy/.gitkeep`

- [ ] **Step 1: Create overview.md**

```markdown
# Anthropic Academy — Track Overview

**Source:** [anthropic.skilljar.com](https://anthropic.skilljar.com)
**Cost:** Free. Skilljar login only — no Anthropic account required.
**Certificates:** Issued per course on completion.

**Note on certification:** As of 2026-06-05, no single "Anthropic Certified Engineer" exam
(comparable to AWS/GCP) was confirmed. The Academy issues per-course completion certificates.
Verify at anthropic.skilljar.com for updates.

## Strategy

Run each module in parallel with its corresponding Udemy phase. This creates direct comparison
between Claude-specific patterns and the provider-agnostic approach in the Udemy course —
turning vendor differences into insights rather than confusion.

## Completion Status

| Module | Name | Run With | Status |
|---|---|---|---|
| A | Claude API Mastery | Phase 1 | 🔄 Active |
| B | MCP & Tool Ecosystem | Phase 3 | ⬜ |
| C | Agents & Cloud Deployment | Phase 5 | ⬜ |

## Certificates Earned

| Course | Date | Certificate |
|---|---|---|
| (none yet) | — | — |
```

- [ ] **Step 2: Create module-a-claude-api.md**

```markdown
# Module A — Claude API Mastery

**Run With:** Phase 1 — Foundations & Frontier APIs
**Status:** 🔄 Active
**Source:** [anthropic.skilljar.com](https://anthropic.skilljar.com)

## Courses

| Course | Status | Completed | Certificate |
|---|---|---|---|
| Building with the Claude API | ⬜ | — | — |
| Claude Code 101 | ⬜ | — | — |
| Claude Code in Action | ⬜ | — | — |

## Key Topics Covered
- Claude Messages API structure (vs OpenAI chat completions)
- Tool use / function calling in Claude
- Streaming with the Claude API
- Claude Code workflows and slash commands
- Integrating Claude Code into development workflows

## Notes
(add notes as you complete each course)
```

- [ ] **Step 3: Create module-b-mcp.md**

```markdown
# Module B — MCP & Tool Ecosystem

**Run With:** Phase 3 — RAG & Knowledge Systems
**Status:** ⬜ Not started
**Source:** [anthropic.skilljar.com](https://anthropic.skilljar.com)

## Courses

| Course | Status | Completed | Certificate |
|---|---|---|---|
| Introduction to Model Context Protocol (Python) | ⬜ | — | — |
| MCP: Advanced Topics | ⬜ | — | — |

## Key Topics Covered
- MCP architecture: host, client, server roles
- Building an MCP server in Python
- Building an MCP client
- Transport layer (stdio, HTTP/SSE)
- Production patterns: sampling, notifications
- Connecting to local and remote servers

## Notes
(add notes as you complete each course)
```

- [ ] **Step 4: Create module-c-agents.md**

```markdown
# Module C — Agents & Cloud Deployment

**Run With:** Phase 5 — Agents & Production Deployment
**Status:** ⬜ Not started
**Source:** [anthropic.skilljar.com](https://anthropic.skilljar.com)

## Courses

| Course | Status | Completed | Certificate |
|---|---|---|---|
| Introduction to agent skills | ⬜ | — | — |
| Introduction to subagents | ⬜ | — | — |
| Claude Agent SDK | ⬜ | — | — |
| Claude with Amazon Bedrock | ⬜ | — | — |
| Claude with Google Cloud Vertex AI | ⬜ | — | — |

## Key Topics Covered
- Building reusable agent skills in Markdown
- Subagent patterns: managing context, delegating tasks
- Claude Agent SDK for programmatic agent orchestration
- Deploying Claude on AWS Bedrock
- Deploying Claude on Google Vertex AI

## Notes
(add notes as you complete each course)
```

- [ ] **Step 5: Verify all four Academy files exist**

```bash
ls curriculum/anthropic-academy/
```
Expected: `module-a-claude-api.md  module-b-mcp.md  module-c-agents.md  overview.md` (and `.gitkeep` still there)

- [ ] **Step 6: Remove gitkeep and commit**

```bash
rm curriculum/anthropic-academy/.gitkeep
git add curriculum/anthropic-academy/
git commit -m "feat: add Anthropic Academy track files (overview + 3 modules)"
```

---

## Task 12: Resources Files

**Files:**
- Create: `resources/courses.md`
- Create: `resources/reading-list.md`
- Delete: `resources/.gitkeep`

- [ ] **Step 1: Create resources/courses.md**

```markdown
# Course Index

## Primary Course

**Mastering Generative AI and LLMs: An 8-Week Hands-On Journey**
- Instructor: Ed Donner
- Platform: Udemy
- Duration: 8 weeks
- Status: 🔄 Active

| Week | Topic | Status |
|---|---|---|
| 1 | Foundations, Transformers, first projects | ⬜ |
| 2 | Frontier APIs, customer service chatbot | ⬜ |
| 3 | Open-source models, HuggingFace | ⬜ |
| 4 | LLM selection, code generation | ⬜ |
| 5 | RAG, vector embeddings | ⬜ |
| 6 | Fine-tuning Frontier models | ⬜ |
| 7 | Advanced training, QLoRA | ⬜ |
| 8 | Deployment, agents | ⬜ |

## Anthropic Academy

See [curriculum/anthropic-academy/overview.md](../curriculum/anthropic-academy/overview.md) for full tracking.

**Quick status:**
- Module A (Claude API): 🔄 Active
- Module B (MCP): ⬜
- Module C (Agents): ⬜

## Other Courses / Resources
(add here as you discover them)
```

- [ ] **Step 2: Create resources/reading-list.md**

```markdown
# Reading List

Articles, documentation, papers, and blog posts worth keeping.

## Official Documentation
| Resource | URL | Notes |
|---|---|---|
| Anthropic API docs | https://docs.anthropic.com | Claude API reference |
| OpenAI API docs | https://platform.openai.com/docs | GPT API reference |
| HuggingFace docs | https://huggingface.co/docs | Transformers, Hub, PEFT |
| LangChain docs | https://python.langchain.com | RAG, agents, chains |
| roadmap.sh/ai-engineer | https://roadmap.sh/ai-engineer | Community skill map |

## Articles & Blog Posts
(add as you read them — format: title, link, one-line note, date read)

## Papers
(add as you encounter them)
```

- [ ] **Step 3: Verify both files exist**

```bash
ls resources/
```
Expected: `courses.md  reading-list.md` (and `.gitkeep`)

- [ ] **Step 4: Remove gitkeep and commit**

```bash
rm resources/.gitkeep
git add resources/
git commit -m "feat: add resources index — courses and reading list"
```

---

## Task 13: Final Validation and First Study Session

**Files:**
- No new files — validation only, then first real use

- [ ] **Step 1: Verify complete vault structure**

```bash
find . -not -path './.git/*' -not -path './.remember/*' -not -path './docs/*' | sort
```

Expected output:
```
.
./CLAUDE.md
./concepts
./concepts/_template.md
./curriculum
./curriculum/anthropic-academy
./curriculum/anthropic-academy/module-a-claude-api.md
./curriculum/anthropic-academy/module-b-mcp.md
./curriculum/anthropic-academy/module-c-agents.md
./curriculum/anthropic-academy/overview.md
./curriculum/phase-1-foundations.md
./curriculum/phase-2-open-source.md
./curriculum/phase-3-rag.md
./curriculum/phase-4-training.md
./curriculum/phase-5-agents-deployment.md
./curriculum/roadmap.md
./inbox
./inbox/.gitkeep
./projects
./projects/.gitkeep
./resources
./resources/courses.md
./resources/reading-list.md
./sessions
./sessions/_template.md
```

- [ ] **Step 2: Verify CLAUDE.md has all 6 sections**

```bash
grep -c "^## Who I Am\|^## Current State\|^## Roadmap Snapshot\|^## Commands\|^## Conventions\|^## Session Protocol" CLAUDE.md
```
Expected: `6`

- [ ] **Step 3: Verify git log shows clean incremental commits**

```bash
git log --oneline
```

Expected (most recent first):
```
feat: add resources index — courses and reading list
feat: add Anthropic Academy track files (overview + 3 modules)
feat: add Phase 5 detail file — Agents & Production Deployment
feat: add Phase 4 detail file — Training & Fine-tuning
feat: add Phase 3 detail file — RAG & Knowledge Systems
feat: add Phase 2 detail file — Open Source & Model Selection
feat: add Phase 1 detail file — Foundations & Frontier APIs
feat: add master roadmap with primary and Academy tracks
feat: add CLAUDE.md — vault brain and operating manual
feat: add session log template
feat: add concept note template
chore: initialize vault directory structure
```

- [ ] **Step 4: Test the "resume" command**

Run `claude` in the vault directory and type:
```
resume
```

Expected: Claude reads `CLAUDE.md` and responds with your active phase (Phase 1), what to study next (start Transformer architecture fundamentals), and suggests starting Module A on the Anthropic Academy in parallel.

- [ ] **Step 5: Final commit tagging vault as ready**

```bash
git add .
git commit -m "chore: vault complete and validated — ready for first study session"
```

---

## Self-Review Notes

**Spec coverage check:**
- ✅ Section 1 (Overview) — covered by overall structure and Task 1
- ✅ Section 2 (Folder structure) — covered by Tasks 1, 6–12
- ✅ Section 3 (CLAUDE.md) — covered by Task 4
- ✅ Section 4 (Concept note format) — covered by Task 2
- ✅ Section 5 (Primary curriculum, all 5 phases + supplementary) — covered by Tasks 5–10
- ✅ Section 6 (Anthropic Academy, all 3 modules) — covered by Task 11
- ✅ Section 7 (Daily workflow) — covered by Task 4 (commands in CLAUDE.md) + Task 13 (live test)
- ✅ Section 8 (Session log format) — covered by Task 3
- ✅ Section 9 (Progress tracking) — covered by Task 4 (conventions) + Tasks 5–10 (status tables)
- ✅ Section 10 (Upgrade path) — not a buildable task; documented in spec; referenced in Task 4 conventions
