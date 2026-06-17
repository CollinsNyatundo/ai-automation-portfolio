# AI Automation Portfolio — n8n Workflow Showcase

> **Production-grade n8n workflows demonstrating modular agent architecture, evaluator-optimizer quality loops, RAG pipelines, SEO content automation, multi-agent orchestration, and governed AI content operations.**

[![n8n](https://img.shields.io/badge/n8n-Workflow-%23FF6D5A?logo=n8n&logoColor=white)](https://n8n.io)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## 🎯 Portfolio Overview

This repository contains **sanitized, production-ready n8n workflows** showcasing advanced AI automation patterns. All credential IDs, webhook IDs, resource IDs (Google Sheets, Drive, Airtable, Pinecone), and instance-specific values have been replaced with `{{ PLACEHOLDERS }}` — ready for your credentials.

### Core Patterns Demonstrated

| Pattern | Description | Key Workflows |
|---------|-------------|---------------|
| **Modular Tool Workflow Architecture** | Master orchestrator delegates to specialized sub-workflows exposed as callable tools with defined I/O schemas | `AI_Marketing_Team`, `Blog_Post`, `LinkedIn_Post` |
| **Evaluator-Optimizer Quality Loop** | Generator → Evaluator (criteria-based) → Optimizer → loops until "Finished" — zero manual review | `Evaluator_Optimizer` |
| **RAG-as-a-Tool** | Ingestion pipeline + retrieval exposed as agent tools; webhook/voice interfaces | `Data_to_Pinecone`, `Voice_RAG_Agent` |
| **Governed Content Pipeline** | Real-time research → AI writing → AI image generation → full audit trail (Sheets) + asset storage (Drive) | `Blog_Post`, `LinkedIn_Post`, `Newsletter_Service` |
| **Multi-LLM Orchestration** | Different models for different tasks (reasoning, writing, evaluation, optimization, embedding) | `Think_Agents`, `AI_Marketing_Team` |
| **Scheduled AI Automation** | Cron triggers → data fetch → AI transformation → multi-channel delivery | `Analytics_Reporting`, `Social_Media_Automation`, `Newsletter_Service` |
| **Multi-Agent Orchestration** | Master assistant routes to 7+ specialized domain agents | `Retrofuture_Master_Assistant`, `Real_Estate_Lead_Automation` |

---

## 📁 Repository Structure

```
ai-automation-portfolio/
├── ARCHITECTURE.md              # Mermaid diagram: full system architecture
├── README.md                    # This file
├── LICENSE                      # MIT License
└── showcase/
    ├── README.md                # Setup guide, credential placeholders, linking instructions
    ├── AI_Marketing_Team.json   # Orchestrator + 6 tool workflows (Blog, LinkedIn, Image gen/edit/search, Video)
    ├── Blog_Post.json           # SEO pipeline: Tavily → GPT-4.1 → gpt-image-1 → Sheets/Drive log
    ├── LinkedIn_Post.json       # Parallel LinkedIn pipeline with same governance
    ├── Evaluator_Optimizer.json # Generator → Evaluator → Optimizer loop until "Finished"
    ├── Data_to_Pinecone.json    # RAG ingestion: Drive → Extract → Chunk → Embed → Pinecone
    ├── Voice_RAG_Agent.json     # RAG-as-tool + webhook interface
    ├── Think_Agents.json        # Multi-LLM agent with 7 tools (Think, Pinecone RAG, Gmail, Airtable, Tavily, Calendar)
    ├── Analytics_Reporting.json # Daily cron → GA → AI summary → Email
    ├── Social_Media_Automation.json # Daily cron → AI caption → Canva → Instagram
    ├── Newsletter_Service.json  # Weekly cron → Fetch posts → AI draft → Mailchimp
    ├── Lead_Generation_Outreach.json # Lead enrichment → AI outreach sequence → CRM log
    ├── E_commerce_Inventory.json # Inventory sync → Alerting → Reorder automation
    ├── Email_Marketing.json     # Segmented campaigns → AI personalization → SendGrid/Mailchimp
    ├── RAG_Pipeline___Chatbot.json # Document ingestion → Chat interface → Pinecone retrieval
    ├── Content_Creation_Workflow.json # End-to-end content: Research → Write → Review → Publish
    ├── Feature_Engineering_n8n.json # CSV → Code Analysis → LLM Feature Engineering Strategy
    ├── Real_Estate_Lead_Automation.json # 10 Tools + 3 Sub-Agents: CRM, Calendar, Gmail, Slack, Sheets, DocuSign, Twilio, Notion, Zapier
    ├── Retrofuture_Master_Assistant.json # Master orchestrator routing to 7 specialized agents
    ├── Retrofuture_Artisan_Production.json # Production scheduling, artisan assignments, workshop ops
    ├── Retrofuture_Customer_Experience.json # Customer support, order status, customization, returns
    ├── Retrofuture_Custom_Orders.json # Custom order creation, personalization, design specs, pricing
    ├── Retrofuture_Supply_Chain.json # Component availability, suppliers, inventory, sourcing
    ├── Retrofuture_Workshop_Technical.json # Equipment, tools, techniques, safety, workshop setup
    ├── Retrofuture_Sales_Design.json # Launches, limited editions, partnerships, wholesale
    └── Retrofuture_Order_Analytics.json # Production metrics, sales reporting, customer analytics, dashboards
```

---

## 🚀 Quick Start

### 1. Prerequisites
- n8n instance (self-hosted or cloud)
- API credentials for services you'll use (see [Credential Placeholders](#credential-placeholders))

### 2. Import Workflows
```bash
# In n8n: Workflows → Import → select .json files from showcase/
```

### 3. Configure Credentials
Replace all `{{ PLACEHOLDERS }}` in workflow nodes with your actual credential IDs and resource IDs. See [showcase/README.md](showcase/README.md) for detailed setup.

### 4. Link Tool Workflows
For `AI_Marketing_Team.json`, update each `toolWorkflow` node's `workflowId.value` to point to the imported sub-workflow IDs.

For `Retrofuture_Master_Assistant.json`, link the 7 specialized agent workflows.

For `Real_Estate_Lead_Automation.json`, link the 3 sub-agent workflows.

### 5. Test
1. Run `Data_to_Pinecone` once to ingest source documents
2. Test `Voice_RAG_Agent` webhook with a question
3. Send Telegram message to `AI_Marketing_Team`: "Write a blog post about AI automation"
4. Trigger `Evaluator_Optimizer` and watch the quality loop iterate
5. Query `Retrofuture_Master_Assistant`: "Check inventory for brass gears"
6. Trigger `Real_Estate_Lead_Automation` via HighLevel webhook

---

## 🔧 Credential Placeholders

| Placeholder | Service | Purpose |
|-------------|---------|---------|
| `{{ OPENROUTERAPI_CREDENTIAL_ID }}` | OpenRouter | LLM access (GPT-4.1, Claude, etc.) |
| `{{ OPENAIAPI_CREDENTIAL_ID }}` | OpenAI | gpt-image-1, embeddings, GPT models |
| `{{ ANTHROPICAPI_CREDENTIAL_ID }}` | Anthropic | Claude 3.5 Sonnet |
| `{{ GOOGLEPALMAPI_CREDENTIAL_ID }}` | Google Gemini | Gemini 2.0 Flash |
| `{{ DEEPSEEKAPI_CREDENTIAL_ID }}` | DeepSeek | DeepSeek R1 (reasoning) |
| `{{ TAVILY_CREDENTIAL_ID }}` | Tavily | Real-time web research |
| `{{ PINECONEAPI_CREDENTIAL_ID }}` | Pinecone | Vector database |
| `{{ GOOGLESHEETSOAUTH2API_CREDENTIAL_ID }}` | Google Sheets | Audit logs, contacts, data |
| `{{ GOOGLEDRIVEOAUTH2API_CREDENTIAL_ID }}` | Google Drive | Asset storage, source documents |
| `{{ GOOGLEDOCSOAUTH2API_CREDENTIAL_ID }}` | Google Docs | Final output documents |
| `{{ GOOGLECALENDAROAUTH2API_CREDENTIAL_ID }}` | Google Calendar | Event management |
| `{{ GMAILOAUTH2_CREDENTIAL_ID }}` | Gmail | Email sending/retrieval |
| `{{ TELEGRAMAPI_CREDENTIAL_ID }}` | Telegram | Bot triggers & delivery |
| `{{ AIRTABLETOKENAPI_CREDENTIAL_ID }}` | Airtable | Contact/CRM database |
| `{{ CANVA_API_CREDENTIAL_ID }}` | Canva | Design automation |
| `{{ MAILCHIMP_CREDENTIAL_ID }}` | Mailchimp | Email campaigns |
| `{{ SENDGRID_CREDENTIAL_ID }}` | SendGrid | Transactional email |
| `{{ FACEBOOKGRAPHAPI_CREDENTIAL_ID }}` | Meta | Instagram/Facebook posting |
| `{{ HIGHLEVEL_API_CREDENTIAL_ID }}` | GoHighLevel | CRM (Real Estate workflow) |
| `{{ SLACK_API_CREDENTIAL_ID }}` | Slack | Team notifications (Real Estate) |
| `{{ TWILIO_API_CREDENTIAL_ID }}` | Twilio | SMS notifications (Real Estate) |
| `{{ NOTION_API_CREDENTIAL_ID }}` | Notion | Knowledge base (Real Estate) |
| `{{ DOCUSIGN_API_CREDENTIAL_ID }}` | DocuSign | E-signatures (Real Estate) |
| `{{ ZAPIER_API_CREDENTIAL_ID }}` | Zapier | External automations (Real Estate) |

---

## 📦 Additional Resource Placeholders

| Placeholder | Description |
|-------------|-------------|
| `{{ GOOGLE_SHEETS_LOG_ID }}` | Google Sheets for content audit log |
| `{{ GOOGLE_DRIVE_FOLDER_ID }}` | Drive folder for AI-generated images |
| `{{ GOOGLE_DOC_ID }}` | Source document for RAG ingestion |
| `{{ GOOGLE_SHEETS_CONTACTS_ID }}` | Contacts spreadsheet |
| `{{ GOOGLE_CALENDAR_EMAIL }}` | Calendar email for events |
| `{{ AIRTABLE_BASE_ID }}` | Airtable base for contacts/CRM |
| `{{ AIRTABLE_TABLE_ID }}` | Airtable table for contacts |
| `{{ SUB_WORKFLOW_ID }}` | ID of imported sub-workflow (Blog_Post, LinkedIn_Post, etc.) |
| `{{ WEBHOOK_ID }}` | Webhook URL (generated on first deploy) |
| `{{ PINECONE_INDEX }}` | Pinecone index name |
| `{{ PINECONE_NAMESPACE }}` | Pinecone namespace (e.g., "projects", "marketing") |

---

## 🏗️ Architecture

See [ARCHITECTURE.md](ARCHITECTURE.md) for a complete Mermaid diagram showing:
- Orchestrator layer (AI Marketing Team, Think Agents, Retrofuture Master, Real Estate Agent)
- Modular tool workflows (Blog, LinkedIn, Image, Video, Retrofuture agents)
- Evaluator-Optimizer quality loop
- RAG pipeline (ingestion + retrieval)
- Content automation (Blog, LinkedIn, Newsletter, Social)
- Reporting & analytics
- Business automation (Real Estate, Lead Gen, E-commerce, Email)
- All external integrations

---

## 🎬 Video Demo Script

A 2-3 minute screen recording covering:
1. **AI Marketing Team Orchestrator** — Telegram invocation → blog post + image + Sheets log
2. **Evaluator-Optimizer Loop** — Watch it iterate until "Finished" criteria met
3. **RAG Pipeline** — Ingest document → query via webhook → agent retrieves + answers
4. **Governed Content** — Open Sheets log, Drive folder — every asset traced
5. **Multi-Agent Think_Agents** — 7 tools, 4 LLMs, self-verification via Think tool
6. **Retrofuture Master Assistant** — Query routes to correct specialized agent
7. **Real Estate Lead Automation** — HighLevel trigger → agent qualifies → assigns → orchestrates
8. **Scheduled Automation** — Daily analytics, weekly newsletter, social media
9. **Lead Gen / E-commerce / Email** — Domain-specific automation examples

---

## 📚 Workflow Categories

### Core AI Agent Patterns
| Workflow | Pattern | Complexity |
|----------|---------|------------|
| `AI_Marketing_Team.json` | Modular Tool Workflow Orchestrator | ⭐⭐⭐⭐⭐ |
| `Think_Agents.json` | Multi-LLM Agent with 7 Tools | ⭐⭐⭐⭐⭐ |
| `Evaluator_Optimizer.json` | Evaluator-Optimizer Quality Loop | ⭐⭐⭐⭐ |

### Multi-Agent Orchestration (RetroFuture Gadgetry)
| Workflow | Pattern | Complexity |
|----------|---------|------------|
| `Retrofuture_Master_Assistant.json` | Master Orchestrator (routes to 7 agents) | ⭐⭐⭐⭐⭐ |
| `Retrofuture_Artisan_Production.json` | Production Scheduling Agent | ⭐⭐⭐⭐ |
| `Retrofuture_Customer_Experience.json` | Customer Support Agent | ⭐⭐⭐⭐ |
| `Retrofuture_Custom_Orders.json` | Custom Orders Agent | ⭐⭐⭐⭐ |
| `Retrofuture_Supply_Chain.json` | Supply Chain Agent | ⭐⭐⭐⭐ |
| `Retrofuture_Workshop_Technical.json` | Workshop Technical Agent | ⭐⭐⭐⭐ |
| `Retrofuture_Sales_Design.json` | Sales & Design Agent | ⭐⭐⭐⭐ |
| `Retrofuture_Order_Analytics.json` | Analytics Agent | ⭐⭐⭐⭐ |

### RAG & Knowledge Base
| Workflow | Pattern | Complexity |
|----------|---------|------------|
| `Data_to_Pinecone.json` | RAG Ingestion Pipeline | ⭐⭐⭐ |
| `Voice_RAG_Agent.json` | RAG-as-Tool + Webhook | ⭐⭐⭐ |
| `RAG_Pipeline___Chatbot.json` | Document → Chat Interface | ⭐⭐⭐ |

### Content Automation
| Workflow | Pattern | Complexity |
|----------|---------|------------|
| `Blog_Post.json` | SEO Pipeline (Research→Write→Image→Log) | ⭐⭐⭐⭐ |
| `LinkedIn_Post.json` | Social Pipeline (Research→Write→Image→Log) | ⭐⭐⭐⭐ |
| `Newsletter_Service.json` | Weekly Cron → AI Draft → Mailchimp | ⭐⭐⭐ |
| `Social_Media_Automation.json` | Daily Cron → Caption → Canva → Instagram | ⭐⭐⭐ |
| `Content_Creation_Workflow.json` | End-to-end: Research→Write→Review→Publish | ⭐⭐⭐⭐ |

### Reporting & Analytics
| Workflow | Pattern | Complexity |
|----------|---------|------------|
| `Analytics_Reporting.json` | Daily GA → AI Summary → Email | ⭐⭐ |
| `Feature_Engineering_n8n.json` | CSV → Code Analysis → LLM Strategy | ⭐⭐⭐⭐ |

### Business Automation
| Workflow | Domain | Complexity |
|----------|--------|------------|
| `Real_Estate_Lead_Automation.json` | Real Estate: 10 Tools + 3 Sub-Agents | ⭐⭐⭐⭐⭐ |
| `Lead_Generation_Outreach.json` | Lead enrichment → AI outreach → CRM | ⭐⭐⭐ |
| `E_commerce_Inventory.json` | Inventory sync → Alerting → Reorder | ⭐⭐⭐ |
| `Email_Marketing.json` | Segmented campaigns → Personalization → Send | ⭐⭐⭐ |

---

## 🤝 Contributing

This is a portfolio showcase repository. For improvements:
1. Fork the repo
2. Create a feature branch
3. Submit a PR with description of the pattern/improvement

---

## 📄 License

MIT License — feel free to use, adapt, and learn from these workflows.

---

## 👤 Author

**Collins Nyatundo**  
AI Automation Specialist  
- GitHub: [@CollinsNyatundo](https://github.com/CollinsNyatundo)  
- Email: cnyagakan@gmail.com

*Built with n8n • Powered by LLMs • Designed for production*