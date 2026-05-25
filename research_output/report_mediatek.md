# MediaTek (2454.TW) — Agentic AI Developer-Tool Adoption

**Research date:** 2026-05-25  ·  **Confidence:** Medium — two T1 home-built signals; no brand-name agentic coding agent.

## Executive summary
MediaTek's agentic/AI coding usage is internal dogfooding of HOME-BUILT tooling, not adoption of brand-name agentic coding agents. It integrated GPT-4 (via Azure OpenAI) into its software-development IDE for code suggestion/generation/auto-fix (Microsoft case study + Business Weekly), and runs AI-assisted code completion plus documentation agents on its NVIDIA DGX SuperPOD AI factory (NVIDIA case study + MediaTek blog). Its DaVinci (達哥) platform reportedly reached 97% employee usage. GitHub Copilot appears only as an aspirational reference, not a confirmed deployment.

## Tools in use

### MediaTek DaVinci (達哥) + GPT-4 / Azure OpenAI IDE integration
- **Confidence tier:** T1 (confirmed)
- **Signal type(s):** internal_dogfooding
- **How it's used:** developer workflow / IDE; internal automation — code suggestion / generation / automatic error-fixing inside the dev IDE.
- **What for:** code suggestion and generation in the software-development IDE; automatic error correction / bug fixing; improving developer productivity within the IC design flow; broader enterprise automation (docs, market analysis, HR screening) via the DaVinci platform.
- **Teams / scale:** Company-wide internal platform (DaVinci/達哥); code-assist use sits within software development / IC design engineering. Reported 97% of employees have used DaVinci, 88% of users reported productivity gains, 50+ cross-department GenAI projects (company-cited, PLATFORM-WIDE, not coding-specific). MediaTek has thousands of software engineers.
- **Evidence:**
  - https://news.microsoft.com/zh-tw/features/azure_openai_security/ — Microsoft case study naming MediaTek; GPT-4 integrated into its dev IDE for code suggestion/generation/auto-fix (vendor case study / primary).
  - https://www.businessweekly.com.tw/business/indep/1003492 — Business Weekly corroborates the GPT-4-in-IDE code-assist claim within the IC design flow (reputable news).
  - https://www.cw.com.tw/article/5131170 — CommonWealth; 97% usage / 88% productivity / 50+ projects figures (reputable news).
  - https://www.ithome.com.tw/news/162202 — iThome; DaVinci 1.0 API libraries interact with software-dev and IC-design environments (reputable news).

### Domain-adapted LLM AI agents on NVIDIA DGX SuperPOD (AI Factory)
- **Confidence tier:** T1 (confirmed)
- **Signal type(s):** internal_dogfooding
- **How it's used:** developer workflow / IDE; internal automation — AI-assisted code completion and automated technical documentation in R&D.
- **What for:** AI-assisted code completion to reduce programming time and error rates; agentic extraction of information from design flowcharts/state diagrams to auto-generate technical documentation (days instead of weeks); chip-design support.
- **Teams / scale:** R&D / engineering org running MediaTek's on-premises AI factory (Tongluo, Taiwan). Factory processes ~60B tokens/month for inference and thousands of training iterations/month (attributed to Co-COO/CFO David Ku) — infrastructure scale, not coding-seat counts. No per-engineer coding-adoption figures.
- **Evidence:**
  - https://www.nvidia.com/en-us/customer-stories/mediatek-ai-factory/ — NVIDIA official customer story naming MediaTek; AI-assisted code completion + agentic documentation generation (vendor case study / primary).
  - https://www.mediatek.com/tek-talk-blogs/building-mediateks-ai-future-with-an-on-premises-ai-factory-powered-by-nvidia — MediaTek's own blog (David Ku attribution) (company blog / primary).
  - https://telematicswire.net/mediatek-builds-on-premises-ai-factory-with-nvidia-to-supercharge-ai-innovation/ — secondary corroboration (reputable news).

### GitHub Copilot (referenced as model / aspiration)
- **Confidence tier:** T3 (weak)
- **Signal type(s):** internal_dogfooding
- **How it's used:** developer workflow / IDE — described as the model MediaTek wants to emulate.
- **What for:** auto-completing code lines from partial engineer input, as part of a "smart software factory" goal.
- **Teams / scale:** MediaTek Software Engineering and Product Security Division; scale unknown (framed as a plan "similar to" Copilot, not a confirmed product rollout).
- **Evidence:**
  - https://www.yourator.co/articles/237 — single weak source; MediaTek division aims for a Copilot-like capability (weak).

## What we could NOT confirm
- **No internal use of any brand-name agentic coding agent:** Claude Code, Cursor, Devin, Windsurf, Gemini CLI, Amazon Q Developer, OpenAI Codex/Operator, Antigravity, Cowork — nothing surfaced tied to MediaTek (T4).
- **GitHub Copilot actual product deployment (T3):** only an aspirational analogy ("plans similar to Copilot") from one weak source; no seats or confirmed deployment.

## Caveats & source-quality notes
- WebFetch returned HTTP 403 on most domains (nvidia.com, mediatek.com, microsoft.com, businessweekly, cw.com.tw, telematicswire); quotes are verbatim WebSearch snippets of those primary/credible pages, not full-page reads. Publication dates unverified.
- Self-/vendor-reported figures: the 97%/88%/50-project numbers are company-cited and PLATFORM-WIDE (all of DaVinci), so they apply to coding use only loosely; the 60B-tokens/month figure is infrastructure scale, not coding seats.
- These are home-built tools on GPT-4/Azure OpenAI and NVIDIA DGX SuperPOD, not named third-party agentic coding agents.
- The GPT-4/IDE material dates to MediaTek's ~2022–2023 GenAI rollout; the NVIDIA AI factory material is ~2025–2026. DaVinci was reportedly transferred to Cyberon (賽微科技) in early 2025.
