# Zapier Workflow Configuration: AI Content Factory

This document outlines the exact field mappings, step configurations, and webhook payloads required to run the automated content generation pipeline between Notion, OpenAI/Gemini, and Google Sheets.

---

## ⚙️ Step-by-Step Zap Setup

### Trigger: Notion — `New Database Item`
* **Database:** `Content Hub`
* **Trigger Event:** When a new page is added or status changes to `Ready for AI`.

### Action 1: OpenAI / Gemini — `Send Prompt`
* **Model:** `gpt-4o` or compatible LLM
* **User Message Mapping:** 
  * Pulls the raw page title and description from the Notion trigger step.
  * Injects the system prompt from [`ai-prompts/content-transformation-prompt.md`](https://github.com/youngcilmi007/ai-content-factory/tree/main/ai-prompts).

### Action 2: Notion — `Update Database Item`
* **Record ID:** Select the current Notion Page ID from Step 1.
* **Property Mappings:**
  * `LinkedIn Post` ➔ Map to AI JSON response key `linkedin_post`
  * `X Thread` ➔ Map to AI JSON response key `twitter_thread`
  * `Newsletter Abstract` ➔ Map to AI JSON response key `newsletter_abstract`
  * `Status` ➔ Update to `Draft Generated`
 
### 🔌 Trigger Step: GitHub — New Commit or Push
- **Event:** `New Commit`
- **Repository:** `youngcilmi007/ai-content-factory`
- **Branch:** `main`
- **Purpose:** Automatically captures code updates, prompt additions, or schema changes to kick off the automation chain.

### 🔄 Action Step 1: Notion Content Hub
- **Action:** Create or Update Database Item
- **Database:** `Content Hub`
- **Mapping:** Maps GitHub commit titles and file additions to page properties.

### 📊 Action Step 2: Google Sheets Master Log
- **Action:** Create Spreadsheet Row
- **Sheet:** `AI Content Master Log`
- **Mapping:** Records the Commit Reference, Content Title, Platforms, Status, and GitHub Asset URL.### Action 3: Google Sheets — `Create Spreadsheet Row`
* **Spreadsheet:** `Master Content Calendar`
* **Row Mappings:**
  * `Content Title` ➔ Notion Page Title
  * `Platforms Targeted` ➔ LinkedIn, X, Newsletter
  * `Generation Date` ➔ Zapier Execution Timestamp (`{{zap_meta_human_now}}`)
  * `Status` ➔ `Scheduled`
