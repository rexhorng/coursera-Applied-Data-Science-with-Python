# AMD (AMD) — Agentic AI Developer-Tool Adoption

**Research date:** 2026-05-25  ·  **Confidence:** High — T1 internal dogfooding of Claude Code, documented by a named AMD senior director

## Executive summary
AMD's AI Group genuinely and heavily uses agentic AI coding tools internally, with Claude Code the standout signal. Senior Director of AI Stella Laurenzo publicly quantified her team's usage (6,852 sessions, 234,760 tool calls) in a GitHub issue, corroborated by reputable tech press — a confirmed (T1) signal, albeit disclosed in the context of a regression complaint. AMD's own open-source Apex repo additionally shows internal tooling that drives Claude Code, OpenAI Codex, and Cursor Agent as interchangeable backends for ROCm GPU-kernel optimization. No credible evidence of internal GitHub Copilot, Amazon Q, Gemini CLI, Devin, or Windsurf use was found.

## Tools in use

### Claude Code (Anthropic)
- **Confidence tier:** T1 (confirmed)
- **Signal type(s):** internal_dogfooding
- **How it's used:** developer workflow / internal automation / autonomous multi-agent orchestration (50+ concurrent terminal agent sessions running 30+ minutes autonomously)
- **What for:** Systems programming in C, MLIR, and GPU drivers; work on the IREE compiler stack (loom, amdgpu, remoting, batteries, web, fuzzing) and an internal multi-agent system named "Bureau"; large autonomous multi-file changes (reportedly ~191,000 lines merged in a single weekend via ~1,498 API requests at peak); kernel-level / hardware-adjacent complex engineering.
- **Teams / scale:** AMD AI Group, represented by Senior Director of AI Stella Laurenzo; closely associated with the AMD-AGI GitHub org. Self-reported scale: 6,852 Claude Code session files analyzed, 234,760 tool calls, 17,871 thinking blocks, 18,000+ user prompts over Jan–Apr 2026; scaled from 1–3 to 5–10+ concurrent sessions across ~10 projects; estimated peak spend ~$42,121/month. Caveat: figures are one director's public analysis scoped to her team, not an official company-wide disclosure.
- **Evidence:**
  - https://github.com/anthropics/claude-code/issues/42796 — Laurenzo's public GitHub issue detailing the team's heavy use and quantified logs (primary source; fetchable).
  - https://www.theregister.com/2026/04/06/anthropic_claude_code_dumber_lazier_amd_ai_director/ — The Register identifies her as AMD AI group director and reports the log analysis (reputable news).
  - https://www.pcgamer.com/software/ai/amds-senior-director-of-ai-thinks-claude-has-regressed-and-that-it-cannot-be-trusted-to-perform-complex-engineering/ — PC Gamer/TechRadar coverage of prior productive kernel-level use (reputable news).
  - https://winbuzzer.com/2026/04/07/amd-ai-director-claude-code-performance-decline-7000-sessions-xcxwbn/ — WinBuzzer detailing the IREE/Bureau workflow and ~191k-line weekend (reputable news).

### OpenAI Codex
- **Confidence tier:** T2 (strong)
- **Signal type(s):** internal_dogfooding
- **How it's used:** internal automation — RL/agent pipeline backend for autonomous GPU kernel optimization
- **What for:** Profiling and optimizing bottleneck GPU kernels for AMD ROCm; generating optimized kernel code graded on compilation, correctness, and speedup (Magpie evaluation) for AMD Instinct hardware (e.g., MI355X).
- **Teams / scale:** AMD-AGI (Advanced Micro Devices) — maintainers of the open-source Apex repository. Scale unknown (selectable backend; no seat/headcount figures disclosed).
- **Evidence:**
  - https://github.com/AMD-AGI/Apex — AMD's own repo listing Codex as a selectable `--agent-backend` for ROCm kernel optimization (primary). Confirms AMD-built tooling drives Codex agentically, but documents capability/option rather than quantified adoption.

### Cursor (Agent mode)
- **Confidence tier:** T3 (weak)
- **Signal type(s):** internal_dogfooding
- **How it's used:** developer workflow — one of three selectable agent backends in AMD's Apex kernel-optimization pipeline
- **What for:** Autonomous/assisted optimization of GPU kernels for AMD ROCm hardware (same task as Apex).
- **Teams / scale:** AMD-AGI (Apex repository). Scale unknown; one optional backend with no usage figures.
- **Evidence:**
  - https://github.com/AMD-AGI/Apex — README documents Cursor Agent as a third backend ("requires a Cursor subscription with agent mode enabled"), selectable via `--agent-backend cursor` (primary). Weak because it is merely a listed option with no evidence anyone at AMD actually selected it.

## What we could NOT confirm
- **GitHub Copilot (T4):** No AMD-specific internal-use evidence — only generic Fortune-100 statistics and listicles.
- **Amazon Q Developer, Gemini CLI, Devin, Windsurf, Antigravity, Cowork (T4):** Only generic comparison/listicle pages, treated as non-evidence.
- **Cursor (T3, weak):** Confirmed only as an optional Apex backend; no evidence of actual adoption breadth.
- **Lisa Su (CEO)** made general statements that AI is embedded in how AMD designs/tests/manufactures chips and that AI-fluent candidates are prioritized in hiring, but named no specific agentic dev tool — not counted as tool-specific evidence.

## Caveats & source-quality notes
- **Complaint framing:** The richest Claude Code disclosure occurred in a complaint about a Feb/Mar 2026 regression, after which the team reportedly pulled back from concurrent autonomous workflows to supervised single-session use. They did not state they abandoned Claude Code entirely. The heavy genuine prior use is well-supported.
- **403 / WebFetch limitation:** The press URLs (The Register, PC Gamer/TechRadar, WinBuzzer) returned HTTP 403 to direct fetch; their content rests on search-result snippets. The primary GitHub issue was fetchable.
- **Self-reported scale:** All scale figures (sessions, tool calls, ~191k lines, spend) are from one director's own log analysis, scoped to her team — directional, not independently audited or company-wide.
- **Ecosystem/product noise excluded:** AMD makes GPUs/ROCm, so many search hits ("Claude Code ports CUDA to ROCm in 30 minutes"; the GEAK repo that calls Anthropic/OpenAI models via LiteLLM API rather than the CLI agents) reflect AMD's ecosystem positioning, not internal dev tooling, and were excluded.
