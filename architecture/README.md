# Architecture Documentation

> **AI Automation Portfolio — System Architecture Diagrams**
>
> This directory contains **individual architecture diagrams** for each automation category in the portfolio. Each diagram focuses on a specific workflow pattern, making it easier to understand, maintain, and extend.

---

## 📁 Directory Structure

```
architecture/
├── README.md                           # This file — index of all diagrams
├── mermaid/                            # Mermaid flowcharts & sequence diagrams
│   ├── core-ai-agents.mmd              # Core AI Agent patterns
│   ├── retrofuture-multi-agent.mmd     # RetroFuture 8-agent orchestration
│   ├── real-estate-automation.mmd      # Real Estate Lead Automation
│   ├── rag-pipeline.mmd                # RAG ingestion & retrieval
│   ├── content-automation.mmd          # SEO/Content pipelines
│   ├── reporting-analytics.mmd         # Reporting & analytics
│   └── business-automation.mmd         # Lead gen, e-commerce, email
├── excalidraw/                         # Hand-drawn architecture diagrams
│   ├── ai-marketing-team.excalidraw    # Modular tool workflow orchestrator
│   ├── evaluator-optimizer.excalidraw  # Quality loop architecture
│   ├── think-agents.excalidraw         # Multi-LLM agent with 7 tools
│   ├── retrofuture-master.excalidraw   # RetroFuture master orchestrator
│   ├── real-estate-agent.excalidraw    # Real Estate 10-tool agent
│   └── rag-voice-agent.excalidraw      # Voice RAG + webhook interface
├── architecture-diagram/               # Dark-themed SVG infrastructure diagrams
│   ├── n8n-infrastructure.html         # n8n stack: Postgres, Qdrant, Docker
│   ├── content-pipeline-infra.html     # Content automation infrastructure
│   └── rag-infrastructure.html         # RAG pipeline infrastructure
└── concept-diagrams/                   # Clean educational SVG diagrams
    ├── data-flow-pipeline.html         # Source → Process → Sink pattern
    ├── agent-tool-pattern.html         # Tool workflow pattern
    └── quality-gate-loop.html          # Evaluator-optimizer quality gate
```

---

## 🎯 Diagram Categories & Workflows

### 1. Core AI Agent Patterns
| Diagram | Type | Workflows Covered |
|---------|------|-------------------|
| `core-ai-agents.mmd` | Mermaid Flowchart | `AI_Marketing_Team`, `Think_Agents`, `Evaluator_Optimizer` |
| `ai-marketing-team.excalidraw` | Excalidraw | `AI_Marketing_Team` modular orchestrator |
| `evaluator-optimizer.excalidraw` | Excalidraw | `Evaluator_Optimizer` quality loop |
| `think-agents.excalidraw` | Excalidraw | `Think_Agents` 4 LLMs + 7 tools |

### 2. Multi-Agent Orchestration: RetroFuture (8 Agents)
| Diagram | Type | Workflows Covered |
|---------|------|-------------------|
| `retrofuture-multi-agent.mmd` | Mermaid Flowchart | All 8 RetroFuture agents |
| `retrofuture-master.excalidraw` | Excalidraw | Master orchestrator routing |

### 3. Multi-Agent Orchestration: Real Estate
| Diagram | Type | Workflows Covered |
|---------|------|-------------------|
| `real-estate-automation.mmd` | Mermaid Flowchart | `Real_Estate_Lead_Automation` |
| `real-estate-agent.excalidraw` | Excalidraw | 10-tool agent + 3 sub-agents |

### 4. RAG & Knowledge Base
| Diagram | Type | Workflows Covered |
|---------|------|-------------------|
| `rag-pipeline.mmd` | Mermaid Flowchart | `Data_to_Pinecone`, `Voice_RAG_Agent`, `RAG_Pipeline___Chatbot` |
| `rag-voice-agent.excalidraw` | Excalidraw | Voice RAG webhook interface |
| `rag-infrastructure.html` | Architecture Diagram | RAG pipeline infrastructure |
| `data-flow-pipeline.html` | Concept Diagram | Source → Process → Sink pattern |

### 5. Content Automation
| Diagram | Type | Workflows Covered |
|---------|------|-------------------|
| `content-automation.mmd` | Mermaid Flowchart | `Blog_Post`, `LinkedIn_Post`, `Newsletter_Service`, `Social_Media_Automation`, `Content_Creation_Workflow` |
| `content-pipeline-infra.html` | Architecture Diagram | Content automation infrastructure |
| `agent-tool-pattern.html` | Concept Diagram | Tool workflow pattern |

### 6. Reporting & Analytics
| Diagram | Type | Workflows Covered |
|---------|------|-------------------|
| `reporting-analytics.mmd` | Mermaid Flowchart | `Analytics_Reporting`, `Feature_Engineering_n8n` |
| `quality-gate-loop.html` | Concept Diagram | Evaluator-optimizer quality gate |

### 7. Business Automation
| Diagram | Type | Workflows Covered |
|---------|------|-------------------|
| `business-automation.mmd` | Mermaid Flowchart | `Lead_Generation_Outreach`, `E_commerce_Inventory`, `Email_Marketing` |

---

## 🛠️ How to View Diagrams

### Mermaid (`.mmd`)
- **GitHub**: Renders natively in `README.md` files
- **VS Code**: Install "Mermaid Preview" extension
- **Obsidian/Notion**: Paste into markdown blocks
- **Online**: <https://mermaid.live> — paste `.mmd` content

### Excalidraw (`.excalidraw`)
- **Web**: Drag & drop `.excalidraw` file onto <https://excalidraw.com>
- **VS Code**: Install "Excalidraw" extension
- **Share**: Use `skills/diagramming/excalidraw/scripts/upload.py` for shareable links

### Architecture Diagram / Concept Diagrams (`.html`)
- **Browser**: Open `.html` file directly (`double-click` or `open`/`xdg-open`)
- **Offline**: Fully self-contained, no internet required (except Google Fonts)
- **PNG Export**: Use `skills/architecture-diagram/scripts/render_png.sh`

---

## 📐 Diagram Design Principles

| Principle | Implementation |
|-----------|----------------|
| **Single Responsibility** | One diagram per automation pattern/category |
| **Readable Node Count** | ≤ 30 nodes per diagram (per Diagram Maker skill) |
| **Semantic Colors** | Consistent color coding across all diagrams |
| **Layered Detail** | High-level in Mermaid, detailed in Excalidraw/SVG |
| **Cross-Reference** | Each diagram links to relevant workflow files in `showcase/` |

---

## 🔄 Updating Diagrams

When adding/updating workflows in `showcase/`:
1. Identify which category the workflow belongs to
2. Update the corresponding Mermaid diagram (`.mmd`)
3. Update the corresponding Excalidraw diagram if structural
4. Update infrastructure diagrams if new services added
5. Update this README index

---

## 📚 Related Resources

- **Portfolio Root**: [../README.md](../README.md) — workflow categories & setup
- **Showcase Workflows**: [../showcase/](../showcase/) — 25 sanitized workflows
- **Mermaid Syntax**: <https://mermaid.js.org/syntax/flowchart.html>
- **Excalidraw Format**: <https://github.com/excalidraw/excalidraw>
- **Diagram Maker Skill**: `skills/diagramming/diagram-maker/`
- **Architecture Diagram Skill**: `skills/creative/architecture-diagram/`
- **Concept Diagrams Skill**: `skills/creative/concept-diagrams/`
- **Excalidraw Skill**: `skills/creative/excalidraw/`