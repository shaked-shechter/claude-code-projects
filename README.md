# claude-code-projects

## PaperOrchestra skills (installed in `.claude/skills/`)

A skill pack that runs the **PaperOrchestra** pipeline (Song, Song, Pfister & Yoon,
Google Cloud AI Research, [arXiv:2604.05018](https://arxiv.org/pdf/2604.05018)):
it turns an idea, an experiment log, a LaTeX template and conference guidelines
into a LaTeX paper and a PDF.

- Source: [Ar9av/PaperOrchestra](https://github.com/Ar9av/PaperOrchestra) at commit
  `6a319132932ee031e2d759b0f7f5075cf77bd1cf` (MIT, see `.claude/skills/PAPERORCHESTRA_LICENSE`).
- Change from upstream: script and file paths of the form `skills/<name>/...` were
  rewritten to `.claude/skills/<name>/...` so they resolve from the repository root.

### How to use it (computer or phone)

Open a Claude Code session on this repository: in the terminal, in the desktop app,
at claude.ai/code, or in the Claude mobile app (Code tab). The skills load
automatically. Then ask, for example:

> Run paper-orchestra on my idea and experiment log

or call it by name: `/paper-orchestra`.

Put your inputs in `workspace/inputs/`:

| File | Required |
|---|---|
| `idea.md` | yes |
| `experimental_log.md` | yes |
| `template.tex` | yes |
| `conference_guidelines.md` | yes |
| `figures/` | optional |

An example input set is in the upstream repo under `examples/minimal/inputs/`.

### Skills included

| Skill | Role |
|---|---|
| `paper-orchestra` | Orchestrator: runs the whole pipeline |
| `outline-agent` | Step 1: outline JSON |
| `plotting-agent` | Step 2: plots and diagrams |
| `literature-review-agent` | Step 3: verified citations, Intro and Related Work |
| `section-writing-agent` | Step 4: remaining sections and tables |
| `content-refinement-agent` | Step 5: simulated peer review and revisions |
| `paper-autoraters` | Evaluation of a finished paper |
| `paper-writing-bench` | Builds benchmark inputs from an existing paper |
| `agent-research-aggregator` | Collects experiment logs from agent runs into inputs |
| `shared/` | References used by the skills above (not a skill) |

### Optional API keys

Literature search works with the agent's own web search. A free Semantic Scholar
key (`SEMANTIC_SCHOLAR_API_KEY`) raises rate limits; Exa, Tavily, Serply and
Keenable keys are optional extras.

### Using it in regular Claude chats (claude.ai, desktop and mobile apps)

`dist/paper-orchestra-skill.zip` packs all the skills above into one skill.
Download it and upload it once at claude.ai → Settings → Capabilities → Skills →
Upload skill. After that it is available in every chat on every device signed in
to the account.
