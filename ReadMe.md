<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0a0a0f,50:0d1b2a,100:1a1a2e&height=160&section=header&text=Ajeet%20Kumar%20Upadhyay&fontSize=42&fontColor=ffffff&fontAlignY=55&desc=AI%20Engineer%20%E2%80%94%20LLMs%20%C2%B7%20RAG%20%C2%B7%20Agentic%20Systems%20%C2%B7%20Voice%20AI%20%C2%B7%20LLM%20Gateways&descAlignY=78&descSize=16&descColor=7dd3fc" />

</div>

<div align="center">

[![LinkedIn](https://img.shields.io/badge/LinkedIn-%230077B5.svg?logo=linkedin&logoColor=white)](https://linkedin.com/in/ajeet-kumar-upadhyay)
[![GitHub](https://img.shields.io/badge/GitHub-%23121011.svg?logo=github&logoColor=white)](https://github.com/Ajeetkrup)
[![Twitter](https://img.shields.io/badge/Twitter-%231DA1F2.svg?logo=twitter&logoColor=white)](https://x.com/ajeetkrup401)
[![Email](https://img.shields.io/badge/Email-D14836?logo=gmail&logoColor=white)](mailto:ajeetkrup401@gmail.com)

![Profile Views](https://komarev.com/ghpvc/?username=ajeetkrup&label=Profile%20Views&color=0ea5e9&style=flat)

</div>

---

## 🧠 Who I Am

> **Building AI systems where latency, observability, and quality aren't afterthoughts — they're the design.**

I'm an **AI Engineer** specializing in LLM systems, RAG pipelines, agentic architectures, and Voice AI. My engineering instinct is systems-first: I build AI with explicit state machines, measurable quality loops, and trace-level visibility — not black-box chains.

IBM-certified across RAG, Agents, Fine-tuning, and Transformers.

```
🤖  Specializing in:  Multi-Agent Systems · LLM Gateways · RAG Pipelines · Voice AI
⚡  Engineering focus: Latency · Semantic Caching · Observability · Eval-Driven Quality
🎓  IBM Certified: RAG & Agentic AI · Generative AI Engineering Professional
🏢  AI Projects: Production-grade systems with real metrics — not toy demos
📍  Noida, India  |  Open to AI / LLM Engineer roles (remote & full-time)
```

---

## 🚀 AI Projects

---

### 🗂️ DocuMind — Agentic Self-Correcting RAG for Document Q&A

> **Stack:** Python · FastAPI · LangGraph · LangChain · ChromaDB · BM25 · Groq · ONNX Runtime · RAGAS · Arize Phoenix · React 19 · Vite

**[🌐 Live Demo](https://documind-production-81f2.up.railway.app/)** · [![GitHub](https://img.shields.io/badge/View%20on%20GitHub-121011?style=flat-square&logo=github)](https://github.com/Ajeetkrup)

A full-stack AI system that ingests enterprise documents and answers questions via an **adaptive, self-correcting retrieval workflow** — built with production engineering depth, not a chat wrapper.

**🔀 Agentic Workflow (LangGraph State Machine)**

The QA pipeline is a deterministic state machine with explicit branching — not a linear chain:

```
generate_query_or_respond → retrieve → grade_documents
                                              ↓
                                    [relevant] → generate_answer
                                    [weak]     → rewrite_question → retrieve (loop)
```

**⚙️ Key Engineering Decisions**

| Decision | Why | Impact |
|----------|-----|--------|
| LangGraph state machine over linear chains | Needed explicit branching, looping, deterministic transitions | Self-correction + explainable execution flow |
| Hybrid retriever (dense 0.7 + BM25 0.3) | Dense misses exact terms; BM25 misses semantic paraphrases | Better recall across varied query styles |
| ChromaDB over Milvus-lite | Milvus-lite not Windows-friendly without Docker | Local persistent vector storage, zero Docker dependency |
| Metadata filtering before indexing | Docling outputs nested metadata Chroma rejects | Prevents ingestion failures at scale |
| Explicit anti-injection prompt constraints | Retrieved context is untrusted; can carry adversarial instructions | Safer grading and answer generation |
| Background RAGAS evaluation | Quality must be measured without blocking user latency | Continuous signal for iterative improvement |
| Phoenix OTEL instrumentation | Agentic systems need trace-level visibility | Faster diagnosis, safer production iteration |

**🔐 Prompt Injection Guardrails**
- Retrieved context explicitly marked as `UNTRUSTED` in all prompts
- Model constrained to ignore any instructions embedded inside documents
- Applied at both grading and answering stages — not just the final generation

**📊 Observability & Evaluation**
- **Arize Phoenix + OpenTelemetry**: traces capture full agent execution paths including routing decisions, retrieval steps, and grade scores
- **RAGAS background eval**: scores `AgentGoalAccuracyWithReference` asynchronously per request — measurable quality loop with zero latency impact

---

### 🔀 Omni-Router — Production LLM Gateway with Semantic Caching & Intent Routing

> **Stack:** Python · FastAPI · FAISS · Redis · ONNX Runtime · LiteLLM · Groq · ARQ · DeepEval · MLflow

[![GitHub](https://img.shields.io/badge/View%20on%20GitHub-121011?style=flat-square&logo=github)](https://github.com/Ajeetkrup)

A production-style LLM gateway combining **semantic caching, intent-based model routing, async quality evaluation, and experiment observability** — built to minimize latency and cost while preserving quality for complex queries.

**🏗️ Architecture Flow**
```
Request → ONNX Embedding → FAISS Similarity Search
              ↓                        ↓
         Cache Miss            Cache Hit → Redis → Response
              ↓
     NearestCentroid Classifier
         ↙              ↘
    Simple              Complex
   (Llama)             (Qwen)
       ↓                   ↓
   LiteLLM + Groq Inference
              ↓
          Response
              ↓ (async, zero latency impact)
       ARQ Job Queue → DeepEval → MLflow
```

**⚡ Architecture Highlights**

| Component | Implementation | Reasoning |
|-----------|---------------|-----------|
| Embeddings | ONNX + `ORTModelForFeatureExtraction` + NumPy mean pooling | Fast CPU vectorization without full PyTorch overhead |
| Semantic cache | FAISS `IndexFlatIP` + Redis | High-similarity hits skip LLM inference entirely |
| Intent classifier | NearestCentroid on `all-MiniLM-L6-v2` embeddings | Lightweight at inference; benchmarked against LR, SVM, RF, XGBoost, KNN |
| Async eval | ARQ job queue → DeepEval | Zero latency impact on response path |
| Observability | MLflow: route taken, model used, latency, prompt size, relevancy, toxicity | Full audit trail for drift detection |

**🧠 Classifier Design**
- Built binary intent classifier using sentence embeddings
- Benchmarked: Logistic Regression, SVM, Random Forest, XGBoost, KNN, NearestCentroid, and deep neural architectures
- **Chose NearestCentroid**: lightweight at inference, stable with embedding-space separation, interpretable decision boundary

**📬 Async Evaluation Pipeline**
- `AnswerRelevancyMetric` and `ToxicityMetric` evaluated via ARQ workers after response is returned
- Failure isolation prevents eval crashes from affecting the main request path
- Drives closed-loop quality monitoring for drift detection and retraining signals

---

### 🎙️ Voice AI Assistant — Real-time STT/LLM/TTS Pipeline

> **Stack:** Python · FastAPI · WebSockets · OpenAI · Deepgram

- Sub-300ms round-trip: Deepgram STT → streaming LLM → TTS audio over WebSockets
- Streaming LLM inference with chunked audio output for sub-perceptual first-byte latency
- WebSocket architecture designed for concurrent multi-user sessions with session isolation

---

### 📺 YouTube Transcript Q&A — RAG over Video Content

> **Stack:** Python · LangChain · ChromaDB · Groq · Streamlit

- Auto-pipeline: transcript extraction → semantic chunking → embeddings → vector storage → Q&A
- Sub-2s end-to-end query processing on live Streamlit app

---

## 🛠️ Technical Stack

### 🤖 LLM & Agentic Frameworks
![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=flat-square&logo=openai&logoColor=white)
![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat-square&logo=langchain&logoColor=white)
![LangGraph](https://img.shields.io/badge/LangGraph-1C3C3C?style=flat-square&logo=langchain&logoColor=white)
![CrewAI](https://img.shields.io/badge/CrewAI-FF4500?style=flat-square&logoColor=white)
![Google ADK](https://img.shields.io/badge/Google%20ADK-4285F4?style=flat-square&logo=google&logoColor=white)
![Groq](https://img.shields.io/badge/Groq-F55036?style=flat-square&logoColor=white)
![Hugging Face](https://img.shields.io/badge/Hugging%20Face-FFD21E?style=flat-square&logo=huggingface&logoColor=black)

### 🔍 RAG & Vector Search
![FAISS](https://img.shields.io/badge/FAISS-0080FF?style=flat-square&logoColor=white)
![Pinecone](https://img.shields.io/badge/Pinecone-000000?style=flat-square&logoColor=white)
![ChromaDB](https://img.shields.io/badge/ChromaDB-FF6B35?style=flat-square&logoColor=white)
![BM25](https://img.shields.io/badge/BM25%20Hybrid-6366F1?style=flat-square&logoColor=white)

### 🎙️ Voice & Real-time AI
![Deepgram](https://img.shields.io/badge/Deepgram-101010?style=flat-square&logoColor=white)
![WebSockets](https://img.shields.io/badge/WebSockets-010101?style=flat-square&logo=socket.io&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=flat-square&logo=fastapi)

### ⚙️ ML Engineering & Evaluation
![PyTorch](https://img.shields.io/badge/PyTorch-%23EE4C2C.svg?style=flat-square&logo=PyTorch&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=flat-square&logo=scikit-learn&logoColor=white)
![ONNX](https://img.shields.io/badge/ONNX%20Runtime-005CED?style=flat-square&logoColor=white)
![MLflow](https://img.shields.io/badge/MLflow-0194E2?style=flat-square&logo=mlflow&logoColor=white)
![RAGAS](https://img.shields.io/badge/RAGAS-22C55E?style=flat-square&logoColor=white)
![DeepEval](https://img.shields.io/badge/DeepEval-8B5CF6?style=flat-square&logoColor=white)
![Arize Phoenix](https://img.shields.io/badge/Arize%20Phoenix-F97316?style=flat-square&logoColor=white)

### ☁️ Infra & Backend
![AWS](https://img.shields.io/badge/AWS-%23FF9900.svg?style=flat-square&logo=amazon-aws&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-%230db7ed.svg?style=flat-square&logo=docker&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-%23DC382D.svg?style=flat-square&logo=redis&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-%23316192.svg?style=flat-square&logo=postgresql&logoColor=white)

---

## 🏅 Certifications

| Certification | Issuer | Year |
|---|---|---|
| **RAG and Agentic AI Professional** | IBM / Coursera | 2025 |
| Specializations: RAG, Vector DBs, Multimodal AI, Agents, LangChain, LangGraph, CrewAI, AutoGen | | |
| **Generative AI Engineering Professional** | IBM / Coursera | 2025 |
| Specializations: Prompt Engineering, LLM Apps, Transformers, NLP, Fine-tuning | | |
| Generative AI Language Modeling with Transformers | IBM | 2025 |
| Generative AI Advanced Fine-Tuning for LLMs | IBM | 2025 |
| Vector Databases for RAG: An Introduction | IBM | 2025 |
| Data Analysis with Python | IBM | 2025 |

---

## 📊 GitHub Stats

<div align="center">

![](https://github-readme-stats.vercel.app/api?username=ajeetkrup&theme=dark&hide_border=true&include_all_commits=true&count_private=true)

![](https://github-readme-streak-stats.herokuapp.com/?user=ajeetkrup&theme=dark&hide_border=true)

![](https://github-readme-stats.vercel.app/api/top-langs/?username=ajeetkrup&theme=dark&hide_border=true&include_all_commits=true&count_private=true&layout=compact&hide=javascript,typescript,css,html)

</div>

---

## 🎓 Education

**B.Tech — Computer Science & Engineering**
I.K. Gujral Punjab Technical University · 2019–2023 · **CGPA: 8.67 / 10**

---

## 📫 Let's Connect

Open to **AI Engineer / LLM Engineer** roles and high-impact AI projects.

<div align="center">

| | |
|---|---|
| 📧 | [ajeetkrup401@gmail.com](mailto:ajeetkrup401@gmail.com) |
| 💼 | [linkedin.com/in/ajeet-kumar-upadhyay](https://linkedin.com/in/ajeet-kumar-upadhyay) |

</div>

---

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:1a1a2e,50:0d1b2a,100:0a0a0f&height=100&section=footer" />

*"State machines over chains. Metrics over vibes. Traces over guesses."*

</div>
