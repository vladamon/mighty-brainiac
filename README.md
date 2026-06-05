# Mighty Brainiac

A terminal-native knowledge vault for building an Applied AI Engineering curriculum. Everything is plain Markdown, version-controlled with Git, and operated through Claude Code. No external apps required — Obsidian can be added later with zero migration cost.

---

## What This Is

A self-study system designed to compound over months. You study, drop raw notes into `/inbox`, and Claude processes them into structured concept notes. Every session starts and ends with a single command. Your progress is tracked in Markdown tables that you (and Claude) update as you go.

The vault has two parallel learning tracks:

- **Primary:** Udemy — *Mastering Generative AI and LLMs* by Ed Donner (8 weeks)
- **Parallel:** Anthropic Academy — free courses at [anthropic.skilljar.com](https://anthropic.skilljar.com)

---

## Quick Start

```bash
# Open the vault in your terminal
cd mighty-brainiac

# Start Claude Code
claude

# Resume your last session
> resume
```

That's it. Claude reads `CLAUDE.md`, tells you your active phase, current topic, and exactly what to do next.

---

## Folder Structure

```
mighty-brainiac/
├── CLAUDE.md                            ← The brain: live session state + command manual
│
├── curriculum/
│   ├── roadmap.md                       ← Master progress tracker for all tracks
│   ├── phase-1-foundations.md           ← Phase detail: topics, projects, status
│   ├── phase-2-open-source.md
│   ├── phase-3-rag.md
│   ├── phase-4-training.md
│   ├── phase-5-agents-deployment.md
│   └── anthropic-academy/
│       ├── overview.md                  ← Academy track overview + certificates
│       ├── module-a-claude-api.md       ← Run alongside Phase 1
│       ├── module-b-mcp.md              ← Run alongside Phase 3
│       └── module-c-agents.md           ← Run alongside Phase 5
│
├── concepts/                            ← One file per concept — your reference library
│   └── _template.md                     ← Copy this for every new concept
│
├── inbox/                               ← Raw drop zone — paste notes here, no formatting needed
│
├── projects/                            ← Hands-on coding sandboxes
│
├── sessions/                            ← Daily study logs
│   └── _template.md                     ← Copy this for every study session
│
└── resources/
    ├── courses.md                       ← Course index + completion tracking
    └── reading-list.md                  ← Articles, docs, papers
```

---

## Daily Workflow

### Starting a session

```
> resume
```

Claude reads `CLAUDE.md` and tells you:
- Your active phase and current topic
- What you planned to do next
- Which Anthropic Academy module to run in parallel

### While studying

Drop raw notes into `/inbox/` — Udemy transcript snippets, copy-pasted articles, rough bullets. No formatting required.

```
> process inbox
```

Claude transforms the raw material into structured concept notes in `/concepts/`, links them to your active phase, and flags any open questions it finds.

### Going deeper on a topic

```
> research [topic]
```

Claude creates or enriches a concept note using its own knowledge. All Claude-synthesized content is marked with `[Claude]` so you always know what came from your study materials versus what Claude added.

### Coding practice

```
> create project for [concept]
```

Claude scaffolds a working project in `/projects/` with a README, starter code, and a small challenge for you to solve. This is where passive knowledge becomes active skill.

### Checking your progress

```
> what have I learned about [topic]
```

Claude searches `/concepts/` and `/sessions/` and gives you a summary of everything you've covered on that topic.

### Testing yourself

```
> quiz me on [topic]
```

Claude generates 5 questions from the concept note for that topic. Answer them without looking — this is retrieval practice, the most effective memorization technique.

### Marking a topic complete

```
> mark [topic] done
```

Claude updates the status in the phase file and the roadmap snapshot in `CLAUDE.md`, then suggests what to study next.

### Ending a session

```
> log session
```

Claude writes a session log to `sessions/YYYY-MM-DD.md` (what you covered, what clicked, what needs more work, next steps) and updates the `Current State` block in `CLAUDE.md`. Next session starts exactly where this one ended.

---

## Curriculum

### Primary Track — Udemy (8 Weeks)

| Phase | Name | Weeks | Topics | Projects |
|---|---|---|---|---|
| 1 | Foundations & Frontier APIs | 1–2 | Transformers, LLM params, prompting techniques, APIs, streaming | Brochure generator, multi-modal chatbot |
| 2 | Open Source & Model Selection | 3–4 | HuggingFace, Ollama, model selection | Meeting minutes tool, Python→C++ translator |
| 3 | RAG & Knowledge Systems | 5 | Embeddings, vector DBs, chunking, RAG pipeline | AI knowledge worker |
| 4 | Training & Fine-tuning | 6–7 | Fine-tuning Frontier + OSS, QLoRA | Price prediction (Frontier + fine-tuned) |
| 5 | Agents & Production Deployment | 8 | Multi-agent systems, context management, deployment | Autonomous deal-spotting agent |

Full topic breakdowns with per-topic status tracking are in `curriculum/phase-N-*.md`.

### Parallel Track — Anthropic Academy (Free)

Run each module alongside its Udemy phase for maximum reinforcement — you learn the generic pattern (Udemy) and the Claude-specific implementation (Academy) at the same time.

| Module | Name | Run With | Courses |
|---|---|---|---|
| A | Claude API Mastery | Phase 1 | Building with the Claude API, Claude Code 101, Claude Code in Action |
| B | MCP & Tool Ecosystem | Phase 3 | Intro to MCP (Python), MCP Advanced Topics |
| C | Agents & Cloud Deployment | Phase 5 | Agent skills, Subagents, Claude Agent SDK, Bedrock, Vertex AI |

### Supplementary Topics

Topics not covered by the Udemy course but required for real Applied AI Engineering roles. Research these as you encounter them — use `> research [topic]` to generate a concept note.

| Topic | Why |
|---|---|
| LangGraph | Stateful agents |
| LangSmith / Langfuse | Observability & tracing |
| Ragas | RAG evaluation |
| Context engineering | Structuring context — distinct from prompt engineering |
| Prompt caching | Cuts API costs 80–90% |
| Prompt injection attacks | Critical security skill for every LLM app |
| AI safety & bias basics | Required knowledge for AI engineering roles |
| OpenRouter | Model routing & fallbacks |
| Claude Agent SDK | Extends the Anthropic Academy track |

---

## Concept Notes

Every concept you learn gets its own file in `/concepts/`. Copy `concepts/_template.md` to get started.

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
This is the mandatory section — writing it IS the learning act.

## Key Points
- Key insight 1
- Key insight 2

## Code Blueprint (optional)
Only include when a runnable example genuinely adds clarity.

## Open Questions
- [ ] Something to research next session

## Related Concepts
- [[embeddings]]
- [[rag-pipeline]]
```

**Rules:**
- **Core Idea is mandatory.** You cannot copy-paste it. Writing it from memory is the whole point.
- **Code Blueprint is optional.** Only include it when a minimal working example clarifies the concept. Skip for architectural patterns or mental models.
- **Open Questions drive future sessions.** Claude picks these up when you run `process inbox`.
- **`[Claude]` marker** on any content Claude synthesized — so you always know what came from your own study vs. what Claude added.

---

## Session Logs

Every study session gets a log in `sessions/`. Copy `sessions/_template.md`, name it `YYYY-MM-DD.md`. Claude writes this automatically when you type `log session`.

```markdown
# Session — 2026-06-05

## What I Covered
- Finished concept note on embeddings
- Started chunking strategies

## What Clicked
- Fixed-size chunking loses context at chunk boundaries — that's why semantic chunking exists

## Needs More Work
- [ ] HNSW indexing internals
- [ ] Pinecone vs Chroma in production

## Concepts Created / Updated
- [[embeddings]] — created
- [[vector-databases]] — updated

## Next Session
RAG pipeline end-to-end, then start Project 5
```

---

## Progress Tracking

Status markers used throughout the vault:

| Symbol | Meaning |
|---|---|
| ⬜ | Not started |
| 🔄 | In progress |
| ✅ | Mastered |
| ❓ | Needs review |

Update them with `> mark [topic] done`, or edit the phase files directly.

---

## Upgrade Path

The vault is designed to evolve alongside your skills. Each upgrade is itself an Applied AI Engineering project.

| When | Upgrade | Why |
|---|---|---|
| Now | Use the vault as-is | Zero setup, works immediately |
| ~50 concept notes | Add Obsidian | Graph view + backlinks when navigation becomes the bottleneck |
| After Phase 3 | Build a custom MCP server for semantic vault search | Search notes by meaning, not filename |
| After Phase 5 | Build a lightweight web dashboard | Apply what you learned to your own tool |

---

## Key Files

| File | What it is |
|---|---|
| `CLAUDE.md` | Read this to understand how the vault works. Claude reads it every session. |
| `curriculum/roadmap.md` | Your master progress tracker — all phases, all tracks, all supplementary topics. |
| `concepts/_template.md` | Template for every new concept note. Copy, rename to kebab-case, fill in. |
| `sessions/_template.md` | Template for every study session log. Claude fills this in automatically. |
| `docs/superpowers/specs/2026-06-05-second-brain-design.md` | The full design spec — architecture decisions and rationale. |
