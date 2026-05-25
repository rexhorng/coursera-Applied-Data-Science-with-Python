# Cisco Systems (CSCO) — Agentic AI Developer-Tool Adoption

**Research date:** 2026-05-25  ·  **Confidence:** High (T1) for GitHub Copilot internal use, triangulated by three independent sources

## Executive summary
Cisco's best-documented third-party agentic/AI coding tool is GitHub Copilot, confirmed (T1) via GitHub's own rollout guidance (~6,000 developers in one business group), an arXiv study conducted at Cisco on real proprietary codebases, and Cisco IT's own blog ("3X increase in output"). Cisco engineers are publicly moving toward agentic coding (a Cisco Live EMEA 2026 talk), and Cisco builds its own internal multi-agent platform-engineering assistant, JARVIS (Outshift). A Claude Code signal exists only via an unverified "ciscoittech" GitHub org and is weak (T3). No credible evidence was found for internal use of Cursor, Codex, Amazon Q, Gemini CLI, Devin, or Windsurf.

## Tools in use

### GitHub Copilot
- **Confidence tier:** T1 (confirmed)
- **Signal type(s):** internal_dogfooding
- **How it's used:** developer workflow / IDE; code review; documentation generation.
- **What for:** Code autocompletion and snippet/function generation; documentation (~50% time saved reported); repetitive coding, unit-test generation, debugging, pair programming (~30–40% time saved); a shift toward human review of AI-generated code ("3X output"); evaluating/explaining and documenting Python sample scripts (Webex engineering).
- **Teams / scale:** Cisco IT / engineering org; a ~6,000-developer business group (per GitHub) rolled out with training; an arXiv study cohort of 26 Cisco engineers on proprietary codebases; one named Webex Engineering Technical Leader using Copilot in VS Code. Cisco IT cites a "3X increase in output" and 30–50% productivity gains across IT functions (projected ~36% overall). Figures are company/vendor self-reported — directional. The 6,000-developer figure is one business group, not company-wide.
- **Evidence:**
  - https://blogs.cisco.com/cisco-on-cisco/the-future-of-work-how-cisco-it-leverages-ai-for-innovation-and-employee-experience — Cisco IT blog stating AI-first engineering with Copilot shows a 3X output increase (primary, company blog).
  - https://resources.github.com/learn/pathways/copilot/essentials/tips-for-a-successful-rollout-of-github-copilot/ — GitHub rollout guidance citing Cisco's ~6,000-developer rollout and training partnership (vendor case study).
  - https://arxiv.org/abs/2406.17910 — arXiv study conducted at Cisco with 26 engineers on real proprietary code, finding 33–36% projected time reduction (primary study).
  - https://developer.webex.com/blog/look-ma-no-hands-using-ai-to-generate-and-refine-webex-github-sample-documentation — Webex Developers blog showing a Cisco engineer using Copilot in VS Code (primary, company blog).

### Copilot agent mode / agentic coding agents (general)
- **Confidence tier:** T2 (strong)
- **Signal type(s):** internal_dogfooding
- **How it's used:** developer workflow / IDE — moving from AI code-assistant ("copilot") usage toward agentic ("agent") engineering.
- **What for:** Direction-of-travel signal toward agentic developer tooling; no specific tool/scale named.
- **Teams / scale:** Cisco CX Engineering (Generative AI and Network Security) — presenter John Groetzinger, Principal Engineer. Scale unknown (conference talk).
- **Evidence:**
  - https://www.ciscolive.com/c/dam/r/ciscolive/emea/docs/2026/pdf/AI-2957.pdf — Cisco Live EMEA 2026 session AI-2957, "From Copilot to Agent: A Developer's Journey into AI-Powered Engineering" (primary, conference talk).

### JARVIS (Cisco Outshift internal AI Platform Engineer)
- **Confidence tier:** T1 (confirmed) — but Cisco-built internal automation, not a third-party coding agent.
- **Signal type(s):** vendor_maker + internal_dogfooding
- **How it's used:** internal automation; CI/CD; developer workflow.
- **What for:** Automating developer requests / eliminating operational bottlenecks; configuring CI/CD pipelines (5–7 days reduced to under an hour); platform-engineering tasks surfaced into Jira, Backstage, Webex, and CLI.
- **Teams / scale:** Cisco Outshift Platform Engineering team. Self-reported: 10x productivity boost, up to 70% time saved on repetitive ops; 15+ sub-agents, 40 tool integrations, 10 automated workflows. Self-reported — directional.
- **Evidence:**
  - https://outshift.cisco.com/blog/JARVIS-agentic-platform-engineering-Outshift — Cisco's own Outshift blog describing JARVIS (primary, company blog).
  - https://blog.langchain.com/cisco-outshift/ — LangChain case study naming Cisco; JARVIS is a LangGraph/LangSmith multi-agent system (vendor case study).

### Claude Code
- **Confidence tier:** T3 (weak) — affiliation unverified.
- **Signal type(s):** internal_dogfooding (ambiguous)
- **How it's used:** orchestrating parallel Claude Code agents across a codebase (claimed context reduction and faster execution).
- **What for:** Multi-agent development framework (claimed ~97% context reduction, 3–6x faster execution via parallel agents).
- **Teams / scale:** GitHub org "ciscoittech" — Cisco affiliation NOT independently confirmed. Scale unknown.
- **Evidence:**
  - https://github.com/ciscoittech/claude-agent-framework — "ciscoittech" org's claude-agent-framework, claiming production-derived patterns (weak; affiliation unverified). Could be an unofficial/personal handle borrowing the Cisco name — should not be counted as official Cisco Claude Code adoption.

## What we could NOT confirm
- **Claude Code (T3, weak):** the only signal is the unverified "ciscoittech" GitHub org; its tie to Cisco Systems is not independently confirmed.
- **Cursor, OpenAI Codex/Operator, Amazon Q Developer, Gemini CLI, Antigravity, Devin, Windsurf, Cowork (T4):** searches returned only generic listicles/comparison pages, treated as non-evidence.
- **No direct exec/earnings quote** tying Cisco coding-agent use to a named executive was found.

## Caveats & source-quality notes
- **403 / WebFetch limitation:** Several primary URLs (Cisco blogs, arXiv, the Cisco Live PDF, GitHub resources, the Webex dev blog) returned HTTP 403 to direct fetch; supporting claims rest on search-result snippets of those real URLs, not full-page reads.
- **Self-reported scale:** Productivity figures (3X output, 30–50% time savings, JARVIS 10x/70%) are company/vendor self-reported and directional, not independently audited. The 6,000-developer figure is one business group, not company-wide.
- **Unverified affiliation (mis-attribution risk):** The "ciscoittech" handle may not represent Cisco Systems; the Claude Code signal is held at T3 for this reason.
- **Build-vs-buy nuance:** JARVIS and Cisco's company-wide internal AI Assistant (~156k daily interactions, 100k+ users) are Cisco-BUILT tooling, distinct from third-party coding-agent dogfooding — included as context but kept separate from third-party tool adoption.
