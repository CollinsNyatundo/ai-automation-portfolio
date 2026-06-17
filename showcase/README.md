# AI Automation Portfolio — Showcase Workflows

This directory contains **25 sanitized flagship n8n workflows** demonstrating production-grade AI automation patterns. All credential IDs, webhook IDs, resource IDs (Google Sheets, Drive, Airtable, Pinecone), and instance-specific values have been replaced with `{{ PLACEHOLDERS }}`.

---

## Workflows Included

### Core AI Agent Patterns

| File | Pattern Demonstrated | Key Technologies | Category |
|------|---------------------|------------------|----------|
| `AI_Marketing_Team.json` | **Modular Tool Workflow Architecture** — Master orchestrator delegates to 6 callable sub-workflow tools | n8n, OpenRouter (GPT-4.1), Telegram, Memory, ToolWorkflow nodes | Core Agent |
| `Think_Agents.json` | **Multi-LLM Agent with 7 Tools** — 4 LLMs + Think, Pinecone RAG, Gmail, Airtable, Tavily, Calendar, Email | GPT-4.1, Claude 3.5, Gemini 2.0, DeepSeek R1, Pinecone, Google, Airtable | Core Agent |
| `Evaluator_Optimizer.json` | **Evaluator-Optimizer Quality Loop** — Generator → Evaluator (criteria) → Optimizer → loop until "Finished" | GPT-4o-mini, DeepSeek R1, Google Docs, Conditional Loop | Quality |

### Multi-Agent Orchestration (RetroFuture Gadgetry)

| File | Pattern Demonstrated | Key Technologies | Category |
|------|---------------------|------------------|----------|
| `Retrofuture_Master_Assistant.json` | **Master Orchestrator** — Routes queries to 7 specialized agents based on business function | GPT-4o, Memory, 7 ToolWorkflow nodes | Multi-Agent |
| `Retrofuture_Artisan_Production.json` | **Production Scheduling Agent** — Artisan assignments, workshop coordination, quality control | GPT-4o, HTTP Request, Sheets | Multi-Agent |
| `Retrofuture_Customer_Experience.json` | **Customer Support Agent** — Inquiries, order status, customization, returns | GPT-4o, HTTP Request, CRM | Multi-Agent |
| `Retrofuture_Custom_Orders.json` | **Custom Orders Agent** — New orders, personalization, design specs, pricing | GPT-4o, HTTP Request, CRM | Multi-Agent |
| `Retrofuture_Supply_Chain.json` | **Supply Chain Agent** — Component availability, suppliers, inventory, sourcing | GPT-4o, HTTP Request, Sheets | Multi-Agent |
| `Retrofuture_Workshop_Technical.json` | **Workshop Technical Agent** — Equipment, tools, techniques, safety, setup | GPT-4o, HTTP Request, Knowledge Base | Multi-Agent |
| `Retrofuture_Sales_Design.json` | **Sales & Design Agent** — Launches, limited editions, partnerships, wholesale | GPT-4o, HTTP Request, CRM | Multi-Agent |
| `Retrofuture_Order_Analytics.json` | **Analytics Agent** — Production metrics, sales reporting, customer analytics, dashboards | GPT-4o, HTTP Request, Sheets/BI | Multi-Agent |

### RAG & Knowledge Base

| File | Pattern Demonstrated | Key Technologies | Category |
|------|---------------------|------------------|----------|
| `Data_to_Pinecone.json` | **RAG Ingestion Pipeline** — Drive → Extract → Chunk → Embed → Pinecone Upsert | Google Drive, ExtractFromFile, RecursiveCharacterTextSplitter, OpenAI Embeddings, Pinecone | RAG |
| `Voice_RAG_Agent.json` | **RAG-as-a-Tool + Webhook Interface** — Voice/webhook → Agent → Pinecone Tool → Response | Pinecone VectorStoreTool, OpenAI, Webhook, RespondToWebhook | RAG |
| `RAG_Pipeline___Chatbot.json` | **Document → Chat Interface** — Ingest → Embed → Chat Retrieval | Google Drive, Pinecone, OpenAI, Chat Trigger | RAG |

### Content Automation

| File | Pattern Demonstrated | Key Technologies | Category |
|------|---------------------|------------------|----------|
| `Blog_Post.json` | **Governed SEO Content Pipeline** — Research → Write → Image Prompt → AI Image → Drive/Sheets Audit Log | Tavily, GPT-4.1, gpt-image-1, Google Sheets/Drive, Structured Output Parser | Content |
| `LinkedIn_Post.json` | **Governed LinkedIn Content Pipeline** — Same pattern as Blog_Post, optimized for LinkedIn | Tavily, GPT-4.1, gpt-image-1, Google Sheets/Drive | Content |
| `Newsletter_Service.json` | **Weekly Newsletter** — Cron → Fetch Posts → AI Draft → Mailchimp | HTTP Request, OpenAI, Mailchimp | Content |
| `Social_Media_Automation.json` | **Daily Social Media** — Cron → AI Caption → Canva → Instagram | OpenAI, Canva API, Facebook Graph API | Content |
| `Content_Creation_Workflow.json` | **End-to-End Content** — Research → Write → Review → Publish | Tavily, OpenAI, Google Docs/Sheets/Drive | Content |

### Reporting & Analytics

| File | Pattern Demonstrated | Key Technologies | Category |
|------|---------------------|------------------|----------|
| `Analytics_Reporting.json` | **Daily Automated Reporting** — Cron → Google Analytics → AI Summary → Email | Google Analytics, GPT-3.5/4, SMTP/Email | Reporting |
| `Feature_Engineering_n8n.json` | **LLM Feature Engineering Advisor** — CSV → Code Analysis → LLM Strategy Recommendations | HTTP Request, Code Node, GPT-4.1-mini, HTML Output | Data Science |

### Business Automation

| File | Pattern Demonstrated | Key Technologies | Category |
|------|---------------------|------------------|----------|
| `Real_Estate_Lead_Automation.json` | **Real Estate Lead Orchestrator** — 10 Tools (CRM, Calendar, Gmail, Slack, Sheets, DocuSign, Twilio, Notion, Zapier) + 3 Sub-Agents | HighLevel, Google, Gmail, Slack, DocuSign, Twilio, Notion, Zapier, Sub-Agents | Business |
| `Lead_Generation_Outreach.json` | **Lead Enrichment & Outreach** — Enrich → AI Sequence → CRM Log | HTTP Request, OpenAI, CRM/Sheets | Business |
| `E_commerce_Inventory.json` | **Inventory Automation** — Sync → Alert → Reorder | HTTP Request, OpenAI, Sheets/Email | Business |
| `Email_Marketing.json` | **Segmented Campaigns** — Segment → AI Personalize → SendGrid/Mailchimp | HTTP Request, OpenAI, SendGrid/Mailchimp | Business |

---

## Architecture Overview

See [ARCHITECTURE.md](../ARCHITECTURE.md) for a complete Mermaid diagram showing how these workflows interconnect.

**Core Patterns:**
1. **Tool Workflow Pattern** — Sub-workflows exposed as callable tools with defined I/O schemas
2. **Evaluator-Optimizer Loop** — Automated quality control via iterative refinement
3. **RAG-as-a-Tool** — Knowledge base ingestion + retrieval exposed as agent tools
4. **Governed Content Generation** — Full audit trail (Sheets) + asset storage (Drive) for every AI output
5. **Multi-LLM Orchestration** — Different models for different tasks (reasoning, writing, evaluation, optimization)
6. **Scheduled AI Automation** — Cron triggers → data fetch → AI transformation → delivery
7. **Multi-Agent Orchestration** — Master assistant routes to specialized domain agents

---

## Setup Instructions

### 1. Import Workflows
Import all `.json` files into your n8n instance (Workflows → Import).

### 2. Create Credentials
Configure the following credentials in n8n (replace placeholders):

| Credential Type | Placeholder | Service |
|----------------|-------------|---------|
| OpenRouter API | `{{ OPENROUTERAPI_CREDENTIAL_ID }}` | OpenRouter (GPT-4.1, etc.) |
| OpenAI API | `{{ OPENAIAPI_CREDENTIAL_ID }}` | OpenAI (gpt-image-1, embeddings) |
| Anthropic API | `{{ ANTHROPICAPI_CREDENTIAL_ID }}` | Anthropic (Claude) |
| Google Gemini API | `{{ GOOGLEPALMAPI_CREDENTIAL_ID }}` | Google Gemini |
| DeepSeek API | `{{ DEEPSEEKAPI_CREDENTIAL_ID }}` | DeepSeek |
| Tavily API | `{{ TAVILY_CREDENTIAL_ID }}` | Tavily Web Search |
| Google Sheets OAuth2 | `{{ GOOGLESHEETSOAUTH2API_CREDENTIAL_ID }}` | Google Sheets (logs, contacts) |
| Google Drive OAuth2 | `{{ GOOGLEDRIVEOAUTH2API_CREDENTIAL_ID }}` | Google Drive (assets, source docs) |
| Google Docs OAuth2 | `{{ GOOGLEDOCSOAUTH2API_CREDENTIAL_ID }}` | Google Docs (final outputs) |
| Google Calendar OAuth2 | `{{ GOOGLECALENDAROAUTH2API_CREDENTIAL_ID }}` | Google Calendar |
| Gmail OAuth2 | `{{ GMAILOAUTH2_CREDENTIAL_ID }}` | Gmail |
| Pinecone API | `{{ PINECONEAPI_CREDENTIAL_ID }}` | Pinecone Vector DB |
| Telegram API | `{{ TELEGRAMAPI_CREDENTIAL_ID }}` | Telegram Bot |
| Airtable Token | `{{ AIRTABLETOKENAPI_CREDENTIAL_ID }}` | Airtable |
| Canva API | `{{ CANVA_API_CREDENTIAL_ID }}` | Canva |
| Mailchimp API | `{{ MAILCHIMP_CREDENTIAL_ID }}` | Mailchimp |
| SendGrid API | `{{ SENDGRID_CREDENTIAL_ID }}` | SendGrid |
| Facebook Graph API | `{{ FACEBOOKGRAPHAPI_CREDENTIAL_ID }}` | Instagram/Facebook |
| HighLevel API | `{{ HIGHLEVEL_API_CREDENTIAL_ID }}` | GoHighLevel CRM |
| Slack API | `{{ SLACK_API_CREDENTIAL_ID }}` | Slack |
| Twilio API | `{{ TWILIO_API_CREDENTIAL_ID }}` | Twilio SMS |
| Notion API | `{{ NOTION_API_CREDENTIAL_ID }}` | Notion |
| DocuSign API | `{{ DOCUSIGN_API_CREDENTIAL_ID }}` | DocuSign |
| Zapier API | `{{ ZAPIER_API_CREDENTIAL_ID }}` | Zapier |

### 3. Configure Resources
Replace resource placeholders in workflow nodes:

| Placeholder | Description | Where to Find |
|-------------|-------------|---------------|
| `{{ GOOGLE_SHEETS_LOG_ID }}` | Google Sheets for content audit log | Create a Sheet with columns: Request, ID, Link, Post, Title, Type |
| `{{ GOOGLE_DRIVE_FOLDER_ID }}` | Drive folder for AI-generated images | Create folder in Drive, copy ID from URL |
| `{{ GOOGLE_DOC_ID }}` | Source document for RAG ingestion | Upload doc to Drive, copy ID |
| `{{ GOOGLE_SHEETS_CONTACTS_ID }}` | Contacts spreadsheet | Create Sheet with Name, Email, Phone columns |
| `{{ GOOGLE_CALENDAR_EMAIL }}` | Calendar email for events | Your Google Calendar email |
| `{{ AIRTABLE_BASE_ID }}` | Airtable base for contacts | Create base, copy ID from URL |
| `{{ AIRTABLE_TABLE_ID }}` | Airtable table for contacts | Create table, copy ID |
| `{{ SUB_WORKFLOW_ID }}` | ID of imported sub-workflow | After importing sub-workflows, copy their workflow IDs |
| `{{ WEBHOOK_ID }}` | Webhook URL for Voice_RAG_Agent | Generated on first deploy in n8n |
| `{{ PINECONE_INDEX }}` | Pinecone index name | Create index in Pinecone console |
| `{{ PINECONE_NAMESPACE }}` | Pinecone namespace | e.g., "projects", "marketing" |

### 4. Link Tool Workflows
In `AI_Marketing_Team.json`, update each `toolWorkflow` node's `workflowId.value` to point to the imported sub-workflow IDs:
- `Create Image` → imported `Create_Image` workflow ID
- `Edit Image` → imported `Edit_Image` workflow ID
- `Search Images` → imported `Search_Images` workflow ID
- `Blog Post` → imported `Blog_Post` workflow ID
- `LinkedIn Post` → imported `LinkedIn_Post` workflow ID
- `Video` → imported `Faceless_Video` workflow ID (if available)

For `Retrofuture_Master_Assistant.json`, link the 7 specialized agent workflows.

For `Real_Estate_Lead_Automation.json`, link the 3 sub-agent workflows.

### 5. Test Each Workflow
1. **Data_to_Pinecone** — Run once to ingest source document into Pinecone
2. **Voice_RAG_Agent** — Test webhook with a question about ingested content
3. **AI_Marketing_Team** — Send Telegram message: "Write a blog post about AI automation"
4. **Evaluator_Optimizer** — Trigger with a bio request, watch the loop iterate
5. **Think_Agents** — Chat with the agent, test each tool (email, calendar, RAG, web search)
6. **Retrofuture_Master_Assistant** — Query: "Check inventory for brass gears" → routes to Supply Chain
7. **Real_Estate_Lead_Automation** — Trigger via HighLevel webhook, verify agent routing
8. **Analytics_Reporting** — Run manually, check email output
9. **Content workflows** — Trigger with a topic, verify Sheets log + Drive assets

---

## Credits
Based on workflows from **Nate Herk's "The Ultimate n8n Course"**, community templates, and custom builds — adapted and extended for production portfolio demonstration.

**Author:** Collins Nyatundo  
**Role Target:** AI Automation Specialist  
**Contact:** cnyagakan@gmail.com