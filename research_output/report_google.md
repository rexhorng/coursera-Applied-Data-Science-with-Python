# Alphabet / Google (GOOGL) — Agentic AI Developer-Tool Adoption

**Research date:** 2026-05-25  ·  **Confidence:** High for internal Gemini-stack dogfooding (two T1 signals); vendor_maker products are well-documented but their internal use is not separately evidenced

## Executive summary
Google plays two distinct roles. It is the dominant **vendor_maker** of agentic/AI coding tools it builds and sells (Gemini CLI, Antigravity, Jules, Gemini Code Assist), and it is a heavy **internal dogfooder** of its own Gemini-powered stack — the monorepo AI codegen behind Pichai's ">25% of new code" earnings stat (T1), DeepMind's AlphaEvolve (T1), and the Cider/Critique IDE+review tools and Goose/Gemini-for-Google assistant (both T2). Critically, reporting indicates Google engineers are restricted to in-house tools and discouraged/prohibited from unapproved third-party agents, so **no internal dogfooding of third-party tools (Copilot, Cursor, Claude Code, Codex) was evidenced** — the reporting suggests the opposite.

## Tools in use

> Note on signal separation: the first four tools below are **internal_dogfooding** (what Google's own engineers/infra use). The four after are **vendor_maker** products Google builds and sells; their internal dogfooding is NOT separately evidenced and is rated T4.

### Internal Gemini-powered code generation (monorepo / Cider; Pichai earnings stat)
- **Confidence tier:** T1 (confirmed)
- **Signal type(s):** internal_dogfooding, vendor_maker
- **How it's used:** developer workflow / IDE, internal automation
- **What for:** AI-generated new code that is then reviewed and accepted by engineers across Google's products.
- **Teams / scale:** Company-wide Google engineering (monorepo). >25% of all new code AI-generated as of Q3 2024 (directly attributable Pichai quote). Reported follow-ons: >30% (Q1 2025), ~50% (late 2025), ~75% (Q2 2026) — later figures are secondary/social reporting, directional only.
- **Evidence:**
  - https://thehill.com/policy/technology/4962336-google-ceo-says-more-than-25-percent-of-companys-new-code-written-by-ai/ — Pichai Q3 2024 earnings statement (>25%). Source type: exec quote (credible secondary).
  - https://fortune.com/2024/10/30/googles-code-ai-sundar-pichai/ — corroborating coverage with engineer-review context. Source type: reputable news (credible secondary).
  - https://www.sec.gov/Archives/edgar/data/0001652044/000165204425000087/googexhibit991q32025.htm — Alphabet Q3 2025 8-K filing (earnings context). Source type: earnings filing (primary).

### Cider (internal IDE) + Critique (code review)
- **Confidence tier:** T2 (strong)
- **Signal type(s):** internal_dogfooding, vendor_maker
- **How it's used:** developer workflow / IDE, code review
- **What for:** AI autocomplete; AI-suggested changelist (CL) descriptions; AI input/suggestions on code reviews; one-click ML-powered edit application on review comments; in-IDE chat.
- **Teams / scale:** Org-wide (Cider is the standard internal IDE; Critique the standard review tool). 97% reported engineer satisfaction with Critique; no precise seat count disclosed.
- **Evidence:**
  - https://read.engineerscodex.com/p/how-google-takes-the-pain-out-of — Cider/Critique AI features, 97% satisfaction. Source type: reputable news (credible secondary).
  - https://www.techradar.com/pro/google-issues-official-internal-guidance-on-using-ai-for-coding-and-its-devs-might-not-be-best-pleased — leaked internal guidance naming Cider and Gemini for Google. Source type: reputable news (credible secondary).

### Goose / Gemini for Google (internal coding assistant)
- **Confidence tier:** T2 (strong)
- **Signal type(s):** internal_dogfooding, vendor_maker
- **How it's used:** developer workflow / IDE, internal automation
- **What for:** code generation, debugging and optimization for internal engineering, trained on Google's ~25-year proprietary engineering knowledge base.
- **Teams / scale:** Google engineering broadly; reportedly mandated, with daily-AI-usage expectations and a prohibition on unapproved third-party AI coding tools. No headcount disclosed.
- **Evidence:**
  - https://contxto.com/en/artificial-intelligence/google-introduces-ai-powered-coding-assistant-goose/ — Goose built on Gemini + Google's engineering knowledge base. Source type: reputable news (credible secondary).
  - https://sightsinplus.com/news/technology/google-mandates-use-of-internal-ai-models-for-coding-tasks/ — reported internal mandate and third-party prohibition. Source type: reputable news (credible secondary).

### AlphaEvolve (Google DeepMind)
- **Confidence tier:** T1 (confirmed)
- **Signal type(s):** internal_dogfooding, vendor_maker
- **How it's used:** internal automation, autonomous algorithm discovery/optimization
- **What for:** optimizing Borg data-center scheduling; TPU design optimization; kernel tiling and FlashAttention speedups; open scientific/algorithmic problems.
- **Teams / scale:** Google DeepMind; deployed across Google's compute/infrastructure ecosystem. ~0.7% of Google's worldwide compute continuously recovered (Borg heuristic); 23% kernel-tiling and 32% FlashAttention speedups. Now also offered via Google Cloud (product), hence the dual signal.
- **Evidence:**
  - https://deepmind.google/blog/alphaevolve-a-gemini-powered-coding-agent-for-designing-advanced-algorithms/ — quantified internal deployment. Source type: company blog (primary).
  - https://arxiv.org/abs/2506.13131 — AlphaEvolve technical paper. Source type: paper (primary).
- **Note:** an autonomous algorithm-discovery agent, a different category from an interactive developer-IDE coding assistant, but relevant as internal agentic-AI use.

### Gemini CLI — *vendor_maker (internal use NOT evidenced)*
- **Confidence tier:** T4 for internal dogfooding
- **Signal type(s):** vendor_maker
- **How it's used / what for:** open-source (Apache 2.0) terminal AI agent for refactoring, docs generation, shell command execution, script running, file editing; MCP support. A tool Google ships for external developers.
- **Teams / scale:** External developers. Free tier 60 req/min, 1000 req/day. Internal Google use plausible but not specifically documented.
- **Evidence:**
  - https://blog.google/innovation-and-ai/technology/developers-tools/introducing-gemini-cli-open-source-ai-agent/ — launch (Jun 25, 2025). Source type: company blog (primary).
  - https://techcrunch.com/2025/06/25/google-unveils-gemini-cli-an-open-source-ai-tool-for-terminals/ — launch coverage. Source type: reputable news (credible secondary).

### Google Antigravity — *vendor_maker / product (internal use NOT evidenced)*
- **Confidence tier:** T4 for internal dogfooding
- **Signal type(s):** vendor_maker, product_integration
- **How it's used / what for:** agentic development platform (modified VS Code fork) orchestrating up to 5 parallel autonomous agents; cross-service audits/refactors. Antigravity 2.0 (I/O 2026) expanded to IDE + CLI + SDK + Managed Agents.
- **Teams / scale:** External developers. Free public preview; no internal-seat figures.
- **Evidence:**
  - https://developers.googleblog.com/build-with-google-antigravity-our-new-agentic-development-platform/ — launch (Nov 18, 2025). Source type: company blog (primary).
  - https://9to5google.com/2026/05/19/google-antigravity-agentic-developer-suite/ — Antigravity 2.0 at I/O 2026. Source type: reputable news (credible secondary).
- **Note:** Antigravity exposes third-party Anthropic Claude (Sonnet/Opus) and an OpenAI open variant via BYO API key — a **product feature for external developers**, NOT internal Google engineering use of third-party tools.

### Jules — *vendor_maker (internal use NOT evidenced)*
- **Confidence tier:** T4 for internal dogfooding
- **Signal type(s):** vendor_maker
- **How it's used / what for:** asynchronous autonomous coding agent (Gemini 2.5 Pro) that clones repos into a cloud VM, plans, makes multi-file changes, runs tests, opens GitHub PRs, and snapshots environments.
- **Teams / scale:** External developers (Google Labs). ~2.28M beta site visits and 140k+ publicly shared code improvements during beta — **external** adoption metrics, not internal Google use.
- **Evidence:**
  - https://blog.google/innovation-and-ai/models-and-research/google-labs/jules/ — Google Labs product page (May 20, 2025). Source type: company blog (primary).
  - https://techcrunch.com/2025/08/06/googles-ai-coding-agent-jules-is-now-out-of-beta/ — GA Aug 6, 2025, beta metrics. Source type: reputable news (credible secondary).

### Gemini Code Assist — *vendor_maker (internal use NOT evidenced)*
- **Confidence tier:** T4 for internal dogfooding
- **Signal type(s):** vendor_maker
- **How it's used / what for:** commercial AI code assistant (VS Code, JetBrains, GitHub app) — code completion/generation, transformation, a code-review agent, large-context bug tracing, agent mode.
- **Teams / scale:** External developers/enterprises. Google-run experiment: 2.5x higher odds of completing common dev tasks — a **product experiment metric**, not internal-seat data.
- **Evidence:**
  - https://blog.google/innovation-and-ai/technology/developers-tools/gemini-code-assist-updates-google-io-2025/ — GA, code-review agent (I/O 2025). Source type: company blog (primary).
  - https://developers.google.com/gemini-code-assist/docs/overview — overview and 2.5x experiment figure. Source type: company docs (primary).

## What we could NOT confirm
- **Internal Google engineer use of third-party agentic tools (T4):** GitHub Copilot, Cursor, Claude Code, Codex — reporting indicates the OPPOSITE (engineers restricted to internal tools; unapproved third-party agents prohibited). No internal third-party dogfooding evidenced.
- **Internal dogfooding of Gemini CLI / Antigravity / Jules / Gemini Code Assist specifically (T4):** these are confirmed vendor_maker products; the files surface no specific evidence Google's own engineers use them as their internal default (internal use centers on Cider/Goose).

## Caveats & source-quality notes
- **vendor_maker vs internal_dogfooding discipline:** the tools Google builds/sells (Gemini CLI, Antigravity, Jules, Code Assist) must be kept separate from what Google's own engineers use internally (Cider, Critique, Goose/Gemini-for-Google, AlphaEvolve, monorepo codegen). Their usage metrics (Jules 2.28M visits; Code Assist 2.5x) are external/product metrics, not internal-seat counts.
- **AI-code-% figures:** only the Q3 2024 >25% figure is a clean directly-attributable Pichai quote; the >30%/50%/75% follow-ons (incl. the Fastcompany "75%" headline) are secondary/social reporting and should be treated as directional/lower-confidence, not confirmed verbatim exec quotes.
- **Internal-mandate framing:** the "engineers must use internal tools / third-party prohibited" claim comes from secondary tech-press (TechRadar, SightsInPlus) reporting on leaked internal guidance, not a Google primary source.
- **Goose name collision:** Google's internal "Goose" is distinct from Block's unrelated open-source "Goose" agent (Linux Foundation, Dec 2025); search results conflated them, so some Goose details are lower confidence.
- **403-WebFetch limitation:** WebFetch was broadly blocked (HTTP 403), so claims rely on WebSearch result summaries; all cited URLs are real URLs that appeared in search results.
