# Content Factory Database & Field Mapping Guide

This document defines the schema and property configuration for syncing raw notes, AI-generated multi-platform drafts, and calendar tracking across Notion and Google Sheets.

---

## 🗂️ 1. Notion Content Hub Database Properties
The Notion workspace serves as the primary dashboard where content ideas are drafted, processed, and reviewed.

* **Title (Title):** The core content topic or headline (e.g., *Automating Lead Triage with Zapier*)
* **Status (Status):** 
  * `Idea` (Initial draft stage)
  * `Ready for AI` (Triggers the multi-step Zapier automation)
  * `Draft Generated` (AI has populated the content blocks)
  * `Published` (Live on social channels)
* **LinkedIn Post (Text / Code Block):** Stores the AI-formatted professional post.
* **X Thread (Text / Code Block):** Stores the sequential 3-part micro-thread.
* **Newsletter Abstract (Text):** Stores the executive summary for email distribution.

---

## 📊 2. Google Sheets Master Content Calendar Schema
The Google Sheet acts as the overarching publication schedule and performance metrics log.
Column HeaderData TypeSource / GitHub Integration MappingCommit ReferenceTextPulls the latest commit hash or file name from ai-content-factoryContent TitleTextNotion Database Page Title or Markdown HeadingPlatforms TargetedTextLinkedIn, X, NewsletterGeneration DateDateTimeTimestamp of Zapier automation executionStatusSelectSynced, Scheduled, or PublishedGitHub Asset URLURLDirect link to files in the repository (e.g., prompts and schemas)





| Column Letter | Column Header | Data Type | Description |
| :--- | :--- | :--- | :--- |
| **A** | `Content Title` | Text | Notion Page Title |
| **B** | `Platforms Targeted` | Text | `LinkedIn, X, Newsletter` |
| **C** | `Generation Date` | DateTime | Timestamp from Zapier execution |
| **D** | `Status` | Select | `Scheduled` / `Published` |
| **E** | `Performance Link` | URL | Direct link to live post |
