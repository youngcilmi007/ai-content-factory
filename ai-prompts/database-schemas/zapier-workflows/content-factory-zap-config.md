# Zapier Workflow Configuration: AI Content Factory
# Zapier Workflow Configuration: AI Content Factory

This document outlines the exact field mappings and webhook payloads for the direct automation pipeline connecting GitHub directly to your Google Sheets tracking log.

---

## ⚡ Step-by-Step Zap Setup

### 🔌 Trigger Step: GitHub — New Commit or Push
- **Event:** `New Commit`
- **Repository:** `youngcilmi007/ai-content-factory`
- **Branch:** `main`
- **Purpose:** Automatically captures code updates, prompt additions, and documentation changes.

### 📊 Action Step: Google Sheets — Create Spreadsheet Row
- **Spreadsheet:** `fc lion` (or your Master Content Log)
- **Worksheet:** Sheet1
- **Row Mappings:**
  - **Commit Reference:** Map to GitHub Commit ID / Hash
  - **Content Title:** Map to Commit Message
  - **Platforms Targeted:** Set to `LinkedIn, X, Newsletter`
  - **Generation Date:** Map to Zapier Execution Timestamp (`{{zap_meta_human_now}}`)
  - **Status:** Set to `Synced`
  - **GitHub Asset URL:** Map to Commit URL
