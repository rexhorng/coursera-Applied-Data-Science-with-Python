# Agentic AI 編碼工具:部署架構與資料外洩防護分析

**Deployment Architecture & Data-Leakage Controls for Agentic AI Coding Tools**

**研究日期:** 2026-05-25
**範圍:** 前述 10 家公司中,有使用 Claude Code / OpenAI Codex / Cursor / GitHub Copilot 等 agent 的對象
**方法與限制:** 公開來源。廠商企業條款=高可信且文件完整;部分公司特定架構已查證(NVIDIA NIM、Qualcomm 端上、Azure 租戶隔離);Apple「跑在自家伺服器」屬二手報導;AMD 確切後端未公開。多數公司不會公布內部完整資料治理設定,部分內容係從「可用能力」推斷而非確認其實際組態。

---

## 0. 核心觀念:Agent 與模型是「分離」的

最重要的一點:**「使用 Claude Code」不等於「把程式碼送到 Anthropic」**。

Claude Code / Codex CLI / Cursor 本質是 **agent / harness(用戶端工具)**,背後的**模型**可以替換。因此「資料會不會外洩」主要取決於**模型後端接在哪裡**,而非用了哪個 agent。後端有四種接法:

| 接法 | 機制 | 資料離開公司的範圍 |
|------|------|------------------|
| **(a) 廠商 SaaS(買使用權)** | 直接呼叫 Anthropic / OpenAI 雲端 API | 送到廠商雲(靠合約 no-train + ZDR 防護) |
| **(b) 自家雲租戶** | Claude Code 改接 AWS Bedrock / Google Vertex;GPT-4 走 Azure OpenAI | 留在自家 VPC / 地區 |
| **(c) 自架 / 地端模型** | agent 指向自架模型(如 NVIDIA NIM 容器) | 不出公司基礎設施 |
| **(d) 完全端上** | 模型直接跑在裝置 NPU,不連網 | 完全不離開裝置 |

---

## 1. 各公司部署落點(含證據強度)

| 公司 | 用的 agent | 模型怎麼接 | 防外洩做法 | 證據 |
|------|-----------|-----------|-----------|------|
| **NVIDIA** | Cursor / Codex / Claude Code | Claude Code 可接**自架 NIM**(Anthropic 相容 `/v1/messages` 端點,自架容器免 proxy);Codex 跑在自家 Blackwell;Cursor 為客製企業版 | 模型可完全自架於自家基礎設施,程式碼不出公司 | **高**(NVIDIA 官方文件) |
| **Apple** | Claude / Claude Code | 向 Anthropic **取得模型授權,但把客製 Claude 跑在 Apple 自己的伺服器**(Private Cloud Compute 策略) | 「敏感程式碼不離開 Apple 自控伺服器」 | 中(Bloomberg / 二手報導) |
| **Qualcomm** | 自研 on-device 助手 | LLaMA-3-8B 直接跑在 **Snapdragon NPU(端上)** | 程式碼完全不上雲、不經第三方——最極端防護 | 中-高(VP demo) |
| **MediaTek** | 自建 GPT-4 IDE + 自研模型 | GPT-4 走 **Azure OpenAI**(留在自家 Azure 租戶);自研模型跑自家 **on-prem DGX SuperPOD** | 租戶隔離 + 自家機房;不被拿去訓練 | 高(MS / NVIDIA case study) |
| **Microsoft** | GitHub Copilot(+曾用 Claude Code) | Copilot 跑在自家 Azure;內部 Claude Code 正被汰換回 Copilot CLI | 自家雲 + 企業條款 | 高 |
| **Cisco** | GitHub Copilot(+自研 JARVIS) | Copilot Business / Enterprise(雲 SaaS);另建 **Cisco AI Defense** 做 agent 護欄 | 企業版不訓練 / 不留存 + AI 防火牆 | 高 |
| **AMD** | Claude Code / Codex / Cursor | **未公開確認**;推測走 Anthropic 商用 API(Apex 工具的 agent 後端可互換) | 靠企業條款;細節未揭露 | 低-中 |
| **Broadcom** | 未具名 agentic 助手 | 經 **VMware Tanzu Platform + 自訂 MCP 授權**治理;Claude 為 Tanzu 可選模型 | MCP 授權 + 平台治理層 | 中 |
| **Google** | 自研 Gemini stack | 全用自家 Gemini、跑自家基礎設施;**限制員工用第三方 agent** | 根本不外送(自研自用) | 高 |

> Marvell 僅見 EDA 領域(Synopsys Formal Advisor),非一般編碼 agent,故未列入此部署分析。

---

## 2. 廠商企業資料條款(「買使用權」時的基本防護)

這是「跟廠商購買使用權」時,避免資料外洩的合約層基礎,均已查證:

### Anthropic — Claude / Claude Code
- 預設**不拿商用產品資料(Claude for Work、API、Claude Code)訓練模型**。
- **Zero Data Retention(ZDR,零資料保留)**:回應後不在靜態儲存留存;適用於以「商用組織 API key」或 Claude Enterprise 使用 Claude Code 的情況。
- Team / Enterprise 標準附 DPA;否則預設保留約 30 天。
- 部署彈性:Claude Code 也可走 **AWS Bedrock / Google Vertex**(模型在你的雲租戶)或**自架**(NVIDIA NIM)。

### OpenAI — Codex
- 預設**不拿 API / Enterprise 資料訓練**。
- 合格端點可申請 **ZDR**;否則預設保留約 30 天。
- **Azure OpenAI** 對 EA / MCA 客戶提供 ZDR。

### GitHub Copilot — Business / Enterprise
- **不拿 prompt / 程式碼訓練、不留存 prompt 與建議**(注意:**Copilot Coding Agent 的 session log 會保留**於帳號生命週期)。
- ⚠️ 個人版(Free / Pro / Pro+)**預設會拿資料去訓練**,須手動 opt-out——企業務必使用 **Business / Enterprise**。

### Microsoft Azure OpenAI(MediaTek、Microsoft 走此路徑)
- prompt / completion **留在你自己的租戶**、同地區、**不與 OpenAI 共享、不訓練**。
- AES-256 靜態加密、可加客戶自管金鑰(CMK)、可用 private endpoint / VNet 鎖網路。

---

## 3. 防外洩的三層防線

```
第 1 層 — 合約層      no-train(預設不訓練) + Zero Data Retention(零資料保留) + DPA
第 2 層 — 部署層      自家雲租戶隔離(Bedrock/Vertex/Azure) → 自架模型(NIM) → 完全端上(NPU)
第 3 層 — 治理層      API key 輪替與額度上限、secret scanning、MCP 授權(Broadcom)、
                      AI 防火牆/護欄(Cisco AI Defense)、gateway/proxy 轉譯(如 LiteLLM)
```

越往第 2 層後段(自架 / 端上),程式碼離開公司的範圍越小;Qualcomm 的端上方案是其中最極端、外洩面最小的設計。

---

## 4. 觀察與結論

1. **「自研 / 自控」與「第三方 agent」是兩條清楚的路線**,且與 IP 敏感度高度相關:
   - **IP 最敏感者自己掌控模型落點**:Qualcomm(端上)、Google(自研自用)、Apple(授權模型但自架)、MediaTek(自家租戶 + 地端)。
   - **第三方 agent 採用者靠合約 + 部署彈性**:NVIDIA(可自架 NIM)、Microsoft / Cisco(企業版 Copilot + 自家雲 / 護欄)。
2. **NVIDIA 是「魚與熊掌兼得」的範例**:用最強的第三方 agent(Claude Code / Cursor / Codex),但把模型後端接在自家基礎設施(NIM / Blackwell),兼顧能力與資料主權。
3. **合約防護已是業界標配**:Anthropic / OpenAI / GitHub Copilot 企業版「預設不訓練 + 可開 ZDR」已成基本盤;真正的差異在於企業願不願意再往「自家租戶 / 自架 / 端上」推進。

### 信心與限制
- **高可信**:廠商企業條款;NVIDIA NIM 整合;Azure 租戶隔離;Qualcomm 端上策略。
- **中等**:Apple「跑在自家伺服器 / PCC」(Bloomberg 二手報導,Apple 未正式確認)。
- **低 / 未揭露**:AMD 確切模型後端;多數公司的內部資料治理細節未公開,屬推斷。

---

## Sources

- Anthropic — Zero Data Retention(適用範圍含 Claude Code): https://privacy.claude.com/en/articles/8956058-i-have-a-zero-data-retention-agreement-with-anthropic-what-products-does-it-apply-to
- Anthropic — Is my data used for model training?: https://privacy.claude.com/en/articles/7996868-is-my-data-used-for-model-training
- NVIDIA — Use Claude Code with NIM(自架後端): https://docs.nvidia.com/nim/large-language-models/latest/ai-assistant-integrations/claude-code.html
- TechSpot — Apple relies on Anthropic's Claude internally(跑在 Apple 自家伺服器): https://www.techspot.com/news/111151-apple-hidden-ai-partner-company-heavily-relies-anthropic.html
- eWeek — Xcode + Claude / Apple Private Cloud Compute 角度: https://www.eweek.com/news/xcode-claude-ai-integration-neuron/
- OpenAI — Enterprise privacy(no training, ZDR): https://openai.com/enterprise-privacy/
- OpenAI Codex — Enterprise admin setup / ZDR: https://developers.openai.com/codex/enterprise/
- GitHub — How Copilot handles data(Business/Enterprise 不訓練): https://resources.github.com/learn/pathways/copilot/essentials/how-github-copilot-handles-data/
- Microsoft Learn — Azure OpenAI data privacy(資料留在租戶、不訓練): https://learn.microsoft.com/en-us/azure/foundry/responsible-ai/openai/data-privacy
- Claude Code on AWS Bedrock — 自架 / 治理: https://elevata.io/en/claude-code-on-aws-complete-guide-bedrock-setup-self-hosted-models
