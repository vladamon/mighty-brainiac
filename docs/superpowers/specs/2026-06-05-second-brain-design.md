# Mighty Brainiac — Second Brain Design Spec
**Date:** 2026-06-05  
**Status:** Approved  
**Goal:** A terminal-native, Markdown-based knowledge system for building an Applied AI Engineering curriculum, usable daily, compounding over months.

---

## 1. Overview

This repo is the knowledge base. No external apps required at this stage. All interaction happens through Claude Code running inside the repo directory. A structured folder hierarchy stores notes, curriculum, projects, and session logs. A root `CLAUDE.md` file acts as the brain — it holds live learning state and the operating manual for Claude.

Obsidian can be layered on top at any point with zero migration cost, since the entire vault is plain Markdown.

---

## 2. Folder Structure

```
mighty-brainiac/
├── CLAUDE.md                            ← Brain: live state + operating manual
│
├── curriculum/
│   ├── roadmap.md                       ← Master roadmap, all phases, progress
│   ├── phase-1-foundations.md           ← Per-phase detail: topics, resources, status
│   ├── phase-2-open-source.md
│   ├── phase-3-rag.md
│   ├── phase-4-training.md
│   ├── phase-5-agents-deployment.md
│   └── anthropic-academy/
│       ├── overview.md                  ← Academy track overview + completion status
│       ├── module-a-claude-api.md
│       ├── module-b-mcp.md
│       └── module-c-agents.md
│
├── concepts/                            ← Atomic concept notes, one file per concept
│   └── (e.g. embeddings.md, rag-pipeline.md)
│
├── inbox/                               ← Raw drop zone — unprocessed material
│   └── (paste Udemy notes, articles, transcripts here)
│
├── projects/                            ← Hands-on coding sandboxes
│   └── (e.g. rag-pipeline-demo/, langchain-agent-test/)
│
├── sessions/                            ← Daily study log, one file per day
│   └── (e.g. 2026-06-05.md)
│
├── resources/
│   ├── courses.md                       ← Course index + completion status
│   └── reading-list.md                  ← Articles, docs, papers
│
└── docs/
    ├── initial_brainstorming.md
    ├── udemy-course-curricullum.md
    └── superpowers/specs/               ← This file lives here
```

---

## 3. CLAUDE.md — The Brain

`CLAUDE.md` serves three roles: **operating manual** (how Claude behaves in this vault), **live state** (current learning position), and **session protocol** (start/end routines).

### Structure

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
| Phase | Topic                          | Status     |
|-------|--------------------------------|------------|
| 1     | Foundations & Frontier APIs    | 🔄 Active  |
| 2     | Open Source & Model Selection  | ⬜ Next    |
| 3     | RAG & Knowledge Systems        | ⬜ Later   |
| 4     | Training & Fine-tuning         | ⬜ Later   |
| 5     | Agents & Production Deployment | ⬜ Later   |
| AA    | Anthropic Academy (parallel)   | 🔄 Active  |

## Commands — How to Use This Vault
- **"resume"**                   → Read this file, tell me where I left off and what's next
- **"process inbox"**            → Transform raw notes in /inbox into structured concept files
- **"quiz me on [topic]"**       → Generate 5 questions from the concept note for [topic]
- **"research [topic]"**         → Deep dive, create or update a concept note
- **"mark [topic] done"**        → Update roadmap, suggest next topic
- **"create project for [concept]"** → Scaffold a coding sandbox in /projects
- **"log session"**              → Write today's session file, update Current State above
- **"what have I learned about [topic]"** → Search concepts/ and sessions/ and summarize

## Conventions
- Concept notes live in /concepts/, named kebab-case (e.g. vector-databases.md)
- Roadmap status: ✅ Done · 🔄 Active · ⬜ Not started · ❓ Needs review
- Raw material always goes to /inbox/ first — never directly into /concepts/
- Every concept note must have a Core Idea written in your own words
- Code Blueprint in concept notes is optional — include only when a runnable example adds genuine clarity
- Claude-synthesized content in concept notes is marked with `[Claude]` so you know what came from your sources vs. what Claude added
```

---

## 4. Concept Note Format

All files in `/concepts/` follow this template. Consistency enables reliable processing, quizzing, and cross-referencing.

```markdown
---
topic: Vector Databases
phase: 3-rag
status: learning          # learning | mastered | needs-review
tags: [rag, embeddings, pinecone, chroma]
source: Udemy - Week 5, Section 3
---

## Core Idea
One paragraph in your own words. Written as if explaining to a colleague.
This section is mandatory — it is the primary learning act.

## Key Points
- Point 1
- Point 2
- Point 3

## Code Blueprint (optional)
Include only when a runnable example adds genuine clarity.

## Open Questions
- [ ] Question that came up while studying this
- [ ] Something to research next session

## Related Concepts
- [[embeddings]]
- [[rag-pipeline]]
- [[semantic-chunking]]
```

**Notes on format:**
- **Core Idea is mandatory.** Writing it forces retrieval practice — the most effective memorisation technique. You cannot fake this section.
- **Code Blueprint is optional.** Include when a minimal working example genuinely clarifies the concept. Skip for architectural patterns, mental models, or process concepts.
- **Open Questions are first-class.** They become the input queue for future sessions and `"process inbox"` commands.
- **`[Claude]` marker** is used anywhere Claude added content not sourced from your study materials.

---

## 5. Curriculum — Primary Track (Udemy)

Course: *Mastering Generative AI and LLMs: An 8-Week Hands-On Journey* by Ed Donner.  
Gap analysis cross-referenced with [roadmap.sh/ai-engineer](https://roadmap.sh/ai-engineer) (community-maintained, 356K GitHub stars).

### Phase 1 — Foundations & Frontier APIs *(Weeks 1–2)*
| Topic | Status |
|---|---|
| Transformer architecture fundamentals | ⬜ |
| How LLMs work (tokens, context window, inference) | ⬜ |
| Frontier model landscape (GPT-4o, Claude, Gemini, DeepSeek) | ⬜ |
| Closed vs open-source models — when to use which | ⬜ |
| OpenAI / Anthropic API integration | ⬜ |
| LLM parameters: temperature, top-k, top-p, sampling | ⬜ |
| Prompt engineering fundamentals | ⬜ |
| Zero-shot, few-shot, and chain-of-thought prompting | ⬜ |
| ReAct prompting pattern | ⬜ |
| System prompting & role/behavior design | ⬜ |
| Structured outputs & constrained generation | ⬜ |
| Multi-modal inputs (text, images, audio) | ⬜ |
| Function calling & tool use | ⬜ |
| Streaming responses | ⬜ |
| **Project 1:** AI brochure generator (web scraping + LLM) | ⬜ |
| **Project 2:** Multi-modal customer support chatbot | ⬜ |

### Phase 2 — Open Source & Model Selection *(Weeks 3–4)*
| Topic | Status |
|---|---|
| HuggingFace ecosystem (Transformers, Hub, Spaces, Inference SDK) | ⬜ |
| Open-source models (Llama, Mistral, Qwen, Gemma) | ⬜ |
| Ollama — running models locally for free dev/testing | ⬜ |
| 10 common GenAI use cases | ⬜ |
| LLM selection criteria for tasks | ⬜ |
| Code generation with LLMs | ⬜ |
| Audio processing with open + closed source models | ⬜ |
| **Project 3:** Meeting minutes tool from audio | ⬜ |
| **Project 4:** Python → C++ code translator (60,000x perf) | ⬜ |

### Phase 3 — RAG & Knowledge Systems *(Week 5)*
| Topic | Status |
|---|---|
| Embeddings & similarity search | ⬜ |
| Sentence Transformers (local embedding models) | ⬜ |
| Indexing embeddings & retrieval process | ⬜ |
| Performing similarity / semantic search | ⬜ |
| Vector databases (Chroma, FAISS, Pinecone, Qdrant, Weaviate) | ⬜ |
| Chunking strategies (fixed, recursive, semantic) | ⬜ |
| RAG pipeline end-to-end | ⬜ |
| RAG with dynamic filters | ⬜ |
| RAG vs fine-tuning — decision framework | ⬜ |
| **Project 5:** AI knowledge worker (company Q&A) | ⬜ |

### Phase 4 — Training & Fine-tuning *(Weeks 6–7)*
| Topic | Status |
|---|---|
| Inference vs training distinction | ⬜ |
| Fine-tuning Frontier models (OpenAI fine-tune API) | ⬜ |
| QLoRA & parameter-efficient fine-tuning | ⬜ |
| Open-source model specialization | ⬜ |
| **Project 6:** Price prediction with Frontier models | ⬜ |
| **Project 7:** Fine-tuned OSS model for price prediction | ⬜ |

### Phase 5 — Agents & Production Deployment *(Week 8)*
| Topic | Status |
|---|---|
| Agentic workflows & tool orchestration | ⬜ |
| Multi-agent systems | ⬜ |
| Context management in agents (compaction, isolation) | ⬜ |
| External memory patterns for agents | ⬜ |
| Gradio for production UIs | ⬜ |
| Cloud deployment | ⬜ |
| **Project 8:** Autonomous deal-spotting multi-agent system | ⬜ |

### Supplementary Topics (course gaps — fill as you encounter them)
| Topic | Why it matters |
|---|---|
| LangGraph | Stateful agents — not covered in course |
| LangSmith / Langfuse | Observability & tracing for LLM apps |
| Ragas | RAG evaluation framework |
| FastAPI for AI services | Production API wrapping |
| Containerization basics | Deployment fundamentals |
| Context engineering | How to structure what goes in context — distinct from prompt engineering |
| Prompt caching | Cuts API costs 80–90% on repeated context; key prod skill |
| Prompt injection attacks | Critical security vulnerability in every LLM-powered app |
| AI safety, bias & fairness basics | Required knowledge for any AI engineering role |
| OpenRouter | Model routing & fallbacks across providers — practical prod skill |
| Claude Agent SDK | Anthropic's agent SDK — directly extends the Academy track |

---

## 6. Curriculum — Parallel Track (Anthropic Academy)

Source: [anthropic.skilljar.com](https://anthropic.skilljar.com)  
Free. No Anthropic account required — Skilljar login only.  
Completion certificates issued per course.

**Note on certification:** As of 2026-06-05, no single "Anthropic Certified Engineer" exam (comparable to AWS/GCP certifications) was confirmed. The Academy issues per-course completion certificates. Verify at anthropic.skilljar.com for any updates.

Run each module alongside its corresponding Udemy phase for maximum reinforcement.

### Module A — Claude API Mastery *(run with Phase 1)*
| Course | Status |
|---|---|
| Building with the Claude API | ⬜ |
| Claude Code 101 | ⬜ |
| Claude Code in Action | ⬜ |

### Module B — MCP & Tool Ecosystem *(run with Phase 3)*
| Course | Status |
|---|---|
| Introduction to Model Context Protocol (Python) | ⬜ |
| MCP: Advanced Topics | ⬜ |

### Module C — Agents & Cloud Deployment *(run with Phase 5)*
| Course | Status |
|---|---|
| Introduction to agent skills | ⬜ |
| Introduction to subagents | ⬜ |
| Claude Agent SDK | ⬜ |
| Claude with Amazon Bedrock | ⬜ |
| Claude with Google Cloud Vertex AI | ⬜ |

---

## 7. Daily Workflow

The core study loop. Simple enough to sustain over months.

### Session Start — `"resume"`
Open terminal, run `claude`, type `resume`. Claude reads `CLAUDE.md`, presents your active phase, current topic, and the exact next action from your last session. Zero ramp-up time.

### During Study — `"process inbox"`
While watching Udemy videos or reading articles, dump raw notes, copy-pasted text, or rough bullets into `/inbox/`. No formatting required. When ready, say `"process inbox"` — Claude transforms raw material into structured concept notes in `/concepts/`, links them to the relevant phase, and surfaces any open questions.

### Going Deeper — `"research [topic]"`
When a concept isn't well-covered by your materials, ask Claude to research it. It creates or enriches a concept note, marking all Claude-synthesized content with `[Claude]` so you know what came from your sources vs. what Claude added.

### Coding Practice — `"create project for [concept]"`
Claude scaffolds a working project in `/projects/` with a README, starter code, and a small challenge for you to solve. Passive knowledge becomes active skill.

### End of Session — `"log session"`
Claude writes `sessions/YYYY-MM-DD.md` with what was covered, what clicked, what needs review, and updates the `Current State` block in `CLAUDE.md`. Next session starts exactly where this one ended.

---

## 8. Session Log Format

```markdown
# Session — 2026-06-05

## What I Covered
- Finished concept note on embeddings
- Started Phase 3, read through chunking strategies

## What Clicked
- The difference between fixed-size and semantic chunking is about context preservation

## Needs More Work
- [ ] HNSW indexing internals
- [ ] When to use Pinecone vs Chroma in production

## Concepts Created / Updated
- [[embeddings]] — created
- [[vector-databases]] — updated

## Next Session
Continue with RAG pipeline end-to-end, then build Project 5
```

---

## 9. Progress Tracking

Tracked entirely in `curriculum/roadmap.md` with status markers:

| Symbol | Meaning |
|---|---|
| ⬜ | Not started |
| 🔄 | In progress |
| ✅ | Mastered |
| ❓ | Needs review |

The `"mark [topic] done"` command updates both the phase file and the roadmap snapshot in `CLAUDE.md`.

---

## 10. Upgrade Path

This system is designed to evolve alongside your skills:

| Stage | Upgrade | Trigger |
|---|---|---|
| Month 1–2 | System as designed | Start here |
| When vault has 50+ concept notes | Add Obsidian for graph view + backlinks | Navigation becomes the bottleneck |
| Phase 3 complete | Build a custom MCP server for semantic vault search | Searching notes by meaning, not filename |
| Phase 5 complete | Build a lightweight web dashboard | Apply what you've learned to your own tool |

Each upgrade is itself an Applied AI Engineering project — you learn the skill by using it to improve your own system.
