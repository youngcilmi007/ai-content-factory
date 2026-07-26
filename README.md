# ai-content-factory
An autonomous AI workflow using Zapier, Notion, and Google Sheets to transform single notes into multi-platform content drafts.
# AI-Powered Content Factory & Social Multiplier

An autonomous multi-platform content distribution workflow built using **Zapier**, **Notion**, **OpenAI/Gemini**, and **Google Sheets**. This project transforms a single rough idea or raw note into structured, multi-channel content drafts and maintains a synchronized analytics tracker.

---

## 🎯 The Business Problem
Content creators and marketing teams spend countless hours manually rewriting a single blog post or core idea into separate versions for LinkedIn, X (Twitter), and email newsletters. This creates bottlenecks and inconsistent publishing schedules.

## 💡 The Automated Solution
This workflow creates an autonomous content pipeline:
1. **Intake:** User creates a new page in Notion with a rough topic or note and sets the status to "Ready".
2. **AI Processing:** Zapier intercepts the new Notion page, sends the content payload to an AI Agent, which parses and adapts the tone for distinct formats.
3. **Multi-Platform Drafting:** The AI automatically populates structured child sections or sub-tasks for LinkedIn (short & professional), X (thread structure), and Email (newsletter abstract).
4. **Master Analytics Log:** Safely logs content creation metrics, target publishing dates, and platform statuses into a master Google Sheet.

---

## 🧱 Workflow Architecture

```text
[Notion Idea Board (Status: Ready)] ➔ [Zapier Core Paths] ➔ [AI Agent Adaptation Engine]
[ GitHub Repository ] 
       │  (Webhook: Push / New Release / Template File Update)
       ▼
[ Zapier Automation Trigger ]
       │
       ├─► [ Notion Content Hub ] ➔ Creates or Updates Database Properties
       │
       └─► [ Google Sheets Master Log ] ➔ Inserts/Updates Rows (Content Title, Platform, Status, Link)
                                                                        │
         ┌──────────────────────────────────────────────────────────────┘
         ▼
[Notion Multi-Platform Drafts] ──► [Google Sheets Master Content Calendar]
