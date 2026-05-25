# Microsoft (MSFT) — Agentic AI Developer-Tool Adoption

**Research date:** 2026-05-25  ·  **Confidence:** High — among the strongest in the dataset, with hard published internal numbers plus an exec quote

## Executive summary
Microsoft occupies three roles at once: it is the **vendor/maker** of GitHub Copilot, a heavy **internal dogfooder** of Copilot on its own flagship codebases (with hard published numbers in dotnet/runtime and the github.com core repo), and a **product integrator** shipping Anthropic and OpenAI models inside Copilot, Copilot Studio and Foundry. GitHub Copilot internal use is T1-confirmed. Notably, Microsoft engineers had widely adopted **Anthropic's Claude Code** internally (T2), but most internal Claude Code licenses are being canceled by June 30, 2026 in favor of Copilot CLI — so this adoption is evidenced precisely as it is being wound down.

## Tools in use

### GitHub Copilot (coding agent / agent mode / Copilot CLI)
- **Confidence tier:** T1 (confirmed) for internal dogfooding
- **Signal type(s):** vendor_maker, internal_dogfooding, product_integration
- **How it's used:** developer workflow / IDE, code review, CI/CD, internal automation
- **What for:** assigning GitHub issues to Copilot, which plans the work, opens a PR, writes code and runs tests; code maintenance, modernization and large-scale refactors; bug fixes and CI/CD pipeline stability; automatic AI-powered code review on every PR (in dotnet/runtime); tedious tasks like fixing 161 typos across 100 files in one PR, removing deprecated feature flags, cleaning stale code/tests, DB schema/column-type migrations, and patching production bugs (in the github.com core repo). Internally, Copilot CLI is being standardized as the single agentic command-line tool for long-running sessions.
- **Teams / scale:**
  - **.NET team (dotnet/runtime):** 878 Copilot-coding-agent PRs over ~10 months, 535 merged, 67.9% success rate; experiment began the day CCA launched publicly (May 2025).
  - **GitHub engineering (github.com core repo):** qualitative ("a prolific engineer") based on one month of Copilot-authored PRs; no headcount/percentage published.
  - **Experiences + Devices org (Copilot CLI):** reporting describes "thousands of engineers" being moved onto Copilot CLI by June 30, 2026 (figure from internal-memo journalism, approximate).
  - **Company-wide:** Satya Nadella stated 20–30% of code in Microsoft's repos is AI/software-written (at LlamaCon, April 2025 — not an earnings call).
- **Evidence:**
  - https://devblogs.microsoft.com/dotnet/ten-months-with-cca-in-dotnet-runtime/ — 878 PRs / 535 merged / 67.9% success; AI code review on every PR. Source type: company blog (primary).
  - https://github.blog/ai-and-ml/github-copilot/how-copilot-helps-build-the-github-platform/ — Copilot dogfooding in github.com core repo (typo fixes, flag removal, schema migrations, CI/CD/prod bug patches). Source type: company blog (primary).
  - https://www.cnbc.com/2025/04/29/satya-nadella-says-as-much-as-30percent-of-microsoft-code-is-written-by-ai.html — Nadella "20%, 30% of the code... written by software." Source type: exec quote (credible secondary).
  - https://github.com/newsroom/press-releases/coding-agent-for-github-copilot — vendor/maker: autonomous coding agent announced at Build 2025. Source type: company blog (primary).
  - https://github.blog/news-insights/product-news/github-copilot-meet-the-new-coding-agent/ — coding agent GA (assign issue, plans, opens PR, writes code, runs tests). Source type: company blog (primary).
  - https://newsletter.pragmaticengineer.com/p/microsoft-ai-dev-tools — internal consolidation onto Copilot CLI. Source type: reputable news (credible secondary).

### Anthropic Claude Code (being phased out internally)
- **Confidence tier:** T2 (strong)
- **Signal type(s):** internal_dogfooding
- **How it's used:** developer workflow / IDE, internal automation (agentic CLI-based software development)
- **What for:** agentic CLI-based software development by Microsoft engineers; reportedly the more popular internal tool before the mandated switch to Copilot CLI.
- **Teams / scale:** Experiences + Devices org (engineers on Windows, M365, Teams, Outlook, Surface). Widely adopted per reporting; most internal licenses being canceled by June 30, 2026 (end of fiscal year). No exact seat count published.
- **Evidence:**
  - https://winbuzzer.com/2026/05/15/microsoft-starts-canceling-claude-code-licenses-xcxwbn/ — license cancellation, migration to Copilot CLI, Claude Code reportedly the more popular tool. Source type: reputable news (credible secondary).
  - https://newsletter.pragmaticengineer.com/p/microsoft-ai-dev-tools — internal Claude Code use and the shift. Source type: reputable news (credible secondary).
  - https://www.developer-tech.com/news/microsoft-claude-code-github-copilot-cli/ — drivers (toolchain unification, cost/fiscal timing, control). Source type: reputable news (credible secondary).

### Anthropic Claude models in Copilot Studio / Foundry / GitHub Copilot
- **Confidence tier:** T4 for internal dev use (confirmed product integration, but not internal dogfooding)
- **Signal type(s):** product_integration
- **How it's used:** product integration (customer-facing model availability, not Microsoft-internal developer use)
- **What for:** Claude Sonnet 4 / Opus 4.1 as selectable models for building/orchestrating agents in Copilot Studio; Claude Opus 4.6 in Microsoft Foundry and rolling out across GitHub Copilot.
- **Teams / scale:** Customer-facing; available by default in most geographies as of Jan 6, 2026 (EU/UK/EFTA require admin opt-in). Not an internal-headcount metric.
- **Evidence:**
  - https://www.microsoft.com/en-us/microsoft-copilot/blog/copilot-studio/anthropic-joins-the-multi-model-lineup-in-microsoft-copilot-studio/ — Claude models added to Copilot Studio. Source type: company blog (primary).
  - https://www.eweek.com/news/claude-opus-4-6-microsoft-foundry-github-copilot/ — Claude Opus 4.6 in Foundry and GitHub Copilot. Source type: reputable news (credible secondary).

## What we could NOT confirm
- **Internal standardization on Cursor, Windsurf, or Devin (T4):** only generic comparison listicles surfaced; no company-specific evidence.
- **Exact internal Claude Code seat count (T2 gap):** adoption is well-reported but scale is unquantified — all detail comes from internal-memo journalism, not an official Microsoft statement.

## Caveats & source-quality notes
- **Microsoft-as-Copilot-owner vs internal dogfooding:** be careful to distinguish the three roles. The vendor/maker signal (owns GitHub, ships Copilot/agent mode/coding agent/CLI) is separate from the internal dogfooding metrics (dotnet/runtime, github.com core repo). The hardest evidence is the two primary dogfooding devblogs.
- **Product integration vs internal use:** shipping Anthropic/OpenAI models inside Copilot/Studio/Foundry is a customer-facing feature (T4 for internal dev use) and must not be conflated with Microsoft engineers' own tool usage.
- **403-WebFetch limitation:** several authoritative URLs (CNBC, GitHub blog, Microsoft devblog) returned HTTP 403 to direct fetch; content captured via search-result summaries, so some verbatim quotes/numbers may be approximate.
- **Self-reported scale:** dogfooding numbers (67.9% success rate; "thousands of engineers") come from single self-reported Microsoft/GitHub posts or internal-memo journalism — treat as directional. Nadella's "20–30%" was stated at LlamaCon (April 2025), NOT an earnings call.
