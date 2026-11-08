<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0a0a0f,50:0d1b2a,100:1a1a2e&height=150&section=header&text=Ajeet%20Kumar%20Upadhyay&fontSize=38&fontColor=ffffff&fontAlignY=55&desc=AI%20Engineer%20%E2%80%94%20LLM%20Systems%20%C2%B7%20Routing%20%C2%B7%20Graph%20RAG%20%C2%B7%20Agentic%20Workflows&descAlignY=78&descSize=15&descColor=7dd3fc" />

[![LinkedIn](https://img.shields.io/badge/LinkedIn-%230077B5.svg?logo=linkedin&logoColor=white)](https://linkedin.com/in/ajeet-kumar-upadhyay)
[![GitHub](https://img.shields.io/badge/GitHub-%23121011.svg?logo=github&logoColor=white)](https://github.com/Ajeetkrup)
[![Hugging Face](https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-Ajeet--001-blue)](https://huggingface.co/Ajeet-001)
[![Twitter](https://img.shields.io/badge/Twitter-%231DA1F2.svg?logo=twitter&logoColor=white)](https://x.com/ajeetkrup401)
[![Email](https://img.shields.io/badge/Email-D14836?logo=gmail&logoColor=white)](mailto:ajeetkrup401@gmail.com)

</div>

---

## 🧠 Who I Am

> **Building production AI systems where latency budgets, deterministic routing, and eval loops come first.**

I am an **AI Engineer with 3+ years of experience** designing and deploying production AI systems: set-equivariant model routing, self-correcting Graph RAG, structured document extraction, and real-time voice/WebSocket pipelines.

- ⚡ **Model & Systems Engineering:** Author of [`gemmarouter`](https://github.com/Ajeetkrup/gemmarouter) (custom 11.6M set-equivariant decision head on EmbeddingGemma 2).
- 📉 **Measurable Business Impact:** Reduced LLM costs by **60%** at Febi.ai, cut analyst effort by **85%** at InnovationM, and dropped API latencies by **68%** at Klimb.io.
- 🎓 **IBM Certified:** RAG & Agentic AI Professional · Generative AI Engineering Professional.
- 📍 **Noida, India** | Open to AI Engineer / LLM Systems roles.

---

## 🚀 Featured Engineering Projects

### ⚡ [gemmarouter — Set-Equivariant Decision & Tool Router](https://github.com/Ajeetkrup/gemmarouter)
[![GitHub](https://img.shields.io/badge/View%20Repo-121011?style=flat-square&logo=github)](https://github.com/Ajeetkrup/gemmarouter)
[![Hugging Face](https://img.shields.io/badge/%F0%9F%A4%97%20Model%20Weights-Ajeet--001%2Fembeddinggemma2--decision--router-yellow?style=flat-square)](https://huggingface.co/Ajeet-001/embeddinggemma2-decision-router)
> **Stack:** PyTorch · Hugging Face · EmbeddingGemma 2 · Set Transformer · Python SDK & CLI

Official SDK & model head (`Ajeet-001/embeddinggemma2-decision-router`) for tool selection, intent dispatch, and agent routing:
- **Architecture:** 11.6M-parameter `SetEquivariantDecisionHead` operating on frozen 271M `google/embeddinggemma-2` embeddings.
- **Zero-Latency Option Caching:** Caches candidate vectors in memory — live requests require only **1 query encode + ~1.6ms GPU pass** (~7–12ms CPU).
- **Exact 0.00% Order Sensitivity:** Permutation-invariant 2-layer Set Transformer guarantees identical decisions regardless of option order.
- **Calibrated Abstention:** 6-feature Null Gate automatically abstains (`decision=None`) on out-of-scope or adversarial queries (`P(null) >= 0.58`), preventing hallucinated tool triggers.
- **Circuit-Breaker Dispatch:** Includes `@router.tool` decorator for automatic dispatch and native CLI playground.

---

### 📑 [DocuMind — Contract Risk & Graph RAG Intelligence](https://github.com/Ajeetkrup/Documind)
[![GitHub](https://img.shields.io/badge/View%20Repo-121011?style=flat-square&logo=github)](https://github.com/Ajeetkrup/Documind)
> **Stack:** Python · FastAPI · LangGraph · Qdrant · Memgraph · Groq · Docling · RAGAS · Arize Phoenix · React

Enterprise legal intelligence engine that resolves cross-document contract links and clause precedence:
- **Hybrid Retrieval:** Blends semantic dense search (Qdrant) with graph traversal (Memgraph) to trace which amendments override base agreements.
- **Self-Correcting Agent:** Deterministic LangGraph state machine grades retrieved context, rewrites weak queries, and self-corrects prior to generation.
- **Production Observability:** Background RAGAS evaluation for goal accuracy without user blocking; OpenTelemetry + Arize Phoenix tracing for full agent execution paths.

---

### 🔀 [Omni-Router — Production LLM Gateway & Semantic Caching](https://github.com/Ajeetkrup/Omni-Router)
[![GitHub](https://img.shields.io/badge/View%20Repo-121011?style=flat-square&logo=github)](https://github.com/Ajeetkrup/Omni-Router)
> **Stack:** Python · FastAPI · FAISS · Redis · ONNX Runtime · LiteLLM · ARQ · DeepEval · MLflow

Cost- and latency-optimized gateway routing incoming prompts between lightweight and reasoning models:
- **Sub-ms Semantic Caching:** FAISS `IndexFlatIP` + Redis over ONNX-quantized embeddings (`all-MiniLM-L6-v2`) skips inference on repeat/semantically similar queries.
- **Lightweight Intent Classifier:** NearestCentroid classifier splits queries into Simple (Llama) vs. Complex (Qwen) with minimal CPU overhead.
- **Asynchronous Eval Pipeline:** ARQ worker queues run DeepEval (relevancy & toxicity) and log metrics to MLflow out-of-band with zero response latency penalty.

---

## 💼 Work Experience

#### **AI Engineer** — *Febi.ai* `(Jul 2026 – Nov 2026)`
- **60% Cost Reduction:** Re-architected multi-page invoice extraction into a unified single LLM pipeline with page-level fallbacks, slashing API calls and network overhead.
- **Hybrid OCR & QR Engine:** Integrated RapidOCR and QR decoding to extract critical GSTIN, IRN, and invoice numbers deterministically before model fallback.
- **Multi-Tenant Data Sync:** Built company-specific server dispatch pipelines with database-backed vendor prefill for missing fields.

#### **Software Engineer (AI)** — *InnovationM* `(Mar 2024 – May 2026)`
- **Autonomous Research Agent:** Developed multi-source supplier profiling agents with LangChain/LangGraph, reducing manual analyst time by **85%**.
- **Real-Time Voice AI:** Engineered FastAPI + WebSocket streaming engine with Deepgram STT, supporting **150+ concurrent live interview sessions** at 40% lower latency.
- **Policy Graph RAG:** Built Neo4j knowledge graph RAG over internal enterprise manuals with OpenTelemetry and Arize Phoenix tracing.

#### **Full Stack Developer** — *Klimb.io* `(May 2023 – Mar 2024)`
- **Latency Optimization:** Architected Redis caching layer, lowering average API response times from **800ms to 250ms (68% drop)**.
- **Scale:** Engineered high-throughput PostgreSQL analytics pipelines handling 10,000+ daily events with 99.9% uptime.

---

## 🛠️ Technical Skills
AI & Modeling : Transformers, LangGraph, LangChain, Tool Calling, LoRA/QLoRA Fine-Tuning, Structured Outputs Vector & Graph DB : Qdrant, Memgraph, Neo4j, ChromaDB, FAISS, Pinecone, BM25 Hybrid Search Eval & Tracing : RAGAS, DeepEval, Arize Phoenix, OpenTelemetry, MLflow, Langfuse Backend & Infra : Python, FastAPI, WebSockets, PyTorch, ONNX Runtime, Redis, PostgreSQL, Docker, Kubernetes

---

## 🏅 Certifications & Education

- **IBM Professional Certification:** RAG & Agentic AI (Specialized in LangGraph, CrewAI, Vector DBs, Multi-Agent Systems)
- **IBM Professional Certification:** Generative AI Engineering (Transformers, LLM Architecture, Fine-Tuning)
- **B.Tech in Computer Science & Engineering:** I.K. Gujral Punjab Technical University (2019–2023) — **CGPA: 8.67 / 10**

---

## 📊 GitHub Stats

<div align="center">

![](https://github-readme-stats.vercel.app/api?username=ajeetkrup&theme=dark&hide_border=true&include_all_commits=true&count_private=true)
![](https://github-readme-streak-stats.herokuapp.com/?user=ajeetkrup&theme=dark&hide_border=true)

</div>

---

<div align="center">

*"State machines over chains. Metrics over vibes. Traces over guesses."*

</div>
