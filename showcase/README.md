# AI Automation Portfolio — Showcase Workflows

This directory contains **6 sanitized flagship n8n workflows** demonstrating production-grade AI automation patterns. All credential IDs, webhook IDs, resource IDs (Google Sheets, Drive, Airtable, Pinecone), and instance-specific values have been replaced with `{{ PLACEHOLDERS }}`.

---

## Workflows Included

| File | Pattern Demonstrated | Key Technologies |
|------|---------------------|------------------|
| `AI_Marketing_Team.json` | **Modular Tool Workflow Architecture** — Master orchestrator delegates to 6 callable sub-workflow tools | n8n, OpenRouter (GPT-4.1), Telegram, Memory, ToolWorkflow nodes |
| `Blog_Post.json` | **Governed SEO Content Pipeline** — Research → Write → Image Prompt → AI Image → Drive/Sheets Audit Log | Tavily, GPT-4.1, gpt-image-1, Google Sheets/Drive, Structured Output Parser |
| `LinkedIn_Post.json` | **Governed LinkedIn Content Pipeline** — Same pattern as Blog_Post, optimized for LinkedIn format | Tavily, GPT-4.1, gpt-image-1, Google Sheets/Drive |
| `Evaluator_Optimizer.json` | **Evaluator-Optimizer Quality Loop** — Generator → Evaluator (criteria) → Optimizer → loop until "Finished" | GPT-4o-mini, DeepSeek R1, Google Docs, Conditional Loop |
| `Data_to_Pinecone.json` | **RAG Ingestion Pipeline** — Drive → Extract → Chunk → Embed → Pinecone Upsert | Google Drive, ExtractFromFile, RecursiveCharacterTextSplitter, OpenAI Embeddings, Pinecone |
| `Voice_RAG_Agent.json` | **RAG-as-a-Tool + Webhook Interface** — Voice/webhook → Agent → Pinecone Tool → Response | Pinecone VectorStoreTool, OpenAI, Webhook, RespondToWebhook |

---

## Architecture Overview

See [ARCHITECTURE.md](../ARCHITECTURE.md) for a complete Mermaid diagram showing how these workflows interconnect.

**Core Patterns:**
1. **Tool Workflow Pattern** — Sub-workflows exposed as callable tools with defined I/O schemas
2. **Evaluator-Optimizer Loop** — Automated quality control via iterative refinement
3. **RAG-as-a-Tool** — Knowledge base ingestion + retrieval exposed as agent tools
4. **Governed Content Generation** — Full audit trail (Sheets) + asset storage (Drive) for every AI output
5. **Multi-LLM Orchestration** — Different models for different tasks (reasoning, writing, evaluation, optimization)

---

## Setup Instructions

### 1. Import Workflows
Import all 6 `.json` files into your n8n instance (Workflows → Import).

### 2. Create Credentials
Configure the following credentials in n8n (replace placeholders):

| Credential Type | Placeholder | Service |
|----------------|-------------|---------|
| OpenRouter API | `{{ OPENROUTERAPI_CREDENTIAL_ID }}` | OpenRouter (GPT-4.1, etc.) |
| OpenAI API | `{{ OPENAIAPI_CREDENTIAL_ID }}` | OpenAI (gpt-image-1, embeddings) |
| Tavily API | `{{ TAVILY_CREDENTIAL_ID }}` | Tavily Web Search |
| Google Sheets OAuth2 | `{{ GOOGLESHEETSOAUTH2API_CREDENTIAL_ID }}` | Google Sheets (logs, contacts) |
| Google Drive OAuth2 | `{{ GOOGLEDRIVEOAUTH2API_CREDENTIAL_ID }}` | Google Drive (assets, source docs) |
| Google Docs OAuth2 | `{{ GOOGLEDOCSOAUTH2API_CREDENTIAL_ID }}` | Google Docs (final outputs) |
| Google Calendar OAuth2 | `{{ GOOGLECALENDAROAUTH2API_CREDENTIAL_ID }}` | Google Calendar |
| Gmail OAuth2 | `{{ GMAILOAUTH2_CREDENTIAL_ID }}` | Gmail |
| Pinecone API | `{{ PINECONEAPI_CREDENTIAL_ID }}` | Pinecone Vector DB |
| Telegram API | `{{ TELEGRAMAPI_CREDENTIAL_ID }}` | Telegram Bot |
| Airtable Token | `{{ AIRTABLETOKENAPI_CREDENTIAL_ID }}` | Airtable |
| Anthropic API | `{{ ANTHROPICAPI_CREDENTIAL_ID }}` | Anthropic (Claude) |
| Google Gemini API | `{{ GOOGLEPALMAPI_CREDENTIAL_ID }}` | Google Gemini |
| DeepSeek API | `{{ DEEPSEEKAPI_CREDENTIAL_ID }}` | DeepSeek |

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
| `{{ SUB_WORKFLOW_ID }}` | ID of imported sub-workflow | After importing Blog_Post, LinkedIn_Post, etc., copy their workflow IDs |
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

### 5. Test Each Workflow
1. **Data_to_Pinecone** — Run once to ingest source document into Pinecone
2. **Voice_RAG_Agent** — Test webhook with a question about ingested content
3. **AI_Marketing_Team** — Send Telegram message: "Write a blog post about AI automation"
4. **Evaluator_Optimizer** — Trigger with a bio request, watch the loop iterate

---

## Credits
Based on workflows from **Nate Herk's "The Ultimate n8n Course"** — adapted and extended for production portfolio demonstration.

**Author:** Collins Nyatundo  
**Role Target:** AI Automation Specialist  
**Contact:** cnyagakan@gmail.com