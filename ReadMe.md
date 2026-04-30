<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0f0c29,50:302b63,100:24243e&height=160&section=header&text=Ajeet%20Kumar%20Upadhyay&fontSize=42&fontColor=ffffff&fontAlignY=55&desc=Frontend%20Engineer%20→%20AI%20Engineer%20%E2%80%94%20LLMs%20%C2%B7%20RAG%20%C2%B7%20Voice%20AI%20%C2%B7%20Agentic%20Systems&descAlignY=78&descSize=16&descColor=a78bfa" />

</div>

<div align="center">

[![LinkedIn](https://img.shields.io/badge/LinkedIn-%230077B5.svg?logo=linkedin&logoColor=white)](https://linkedin.com/in/ajeet-kumar-upadhyay)
[![GitHub](https://img.shields.io/badge/GitHub-%23121011.svg?logo=github&logoColor=white)](https://github.com/Ajeetkrup)
[![Twitter](https://img.shields.io/badge/Twitter-%231DA1F2.svg?logo=twitter&logoColor=white)](https://x.com/ajeetkrup401)
[![Email](https://img.shields.io/badge/Email-D14836?logo=gmail&logoColor=white)](mailto:ajeetkrup401@gmail.com)

![Profile Views](https://komarev.com/ghpvc/?username=ajeetkrup&label=Profile%20Views&color=7c3aed&style=flat)

</div>

---

## 🧠 Who I Am

> **3 years shipping production systems. Now building AI on top of that foundation.**  
> Real Redis caching. Real WebSocket pipelines. Real latency tracking. Now applied to LLMs.

I'm a **Software Engineer transitioning into AI Engineering** — coming from 3 years of production frontend and full-stack experience, now specializing in LLM systems, RAG pipelines, and agentic AI. My production background means I approach AI with an engineer's instinct: latency matters, caching matters, observability matters.

IBM-certified across RAG, Agents, Fine-tuning, and Transformers.

```
🏢  Software Engineer @ InnovationM, Noida  (frontend/full-stack → AI transition)
⚡  3 years production systems · Real-time architectures · Latency-aware engineering
🤖  Building:  Multi-Agent Systems · Voice AI · RAG Pipelines · LLM Gateways
🎓  IBM Certified: RAG & Agentic AI · Generative AI Engineering Professional
📍  Noida, India  |  Open to AI/LLM Engineer roles (remote & full-time)
```

---

## 📊 Production Track Record (Engineering Background)

<div align="center">

| Metric | Achievement | Context |
|--------|------------|---------|
| ⚡ API Response Time | **800ms → 250ms** (68% faster) | Redis caching at Klimb.io |
| 🎙️ Voice Chatbot UI | **200+ daily interactions** | STT integration at InnovationM |
| ⚙️ Interview Engine Latency | **40% reduction** | WebSocket engine at InnovationM |
| 👥 Concurrent Users | **500+** at 99.9% uptime | React + Node.js at Klimb.io |
| 🚀 Build Performance | **70% faster cold-start** | CRA → Vite migration |
| 📈 Page Load | **30% reduction** | Next.js SSR + memoization |

</div>

---

## 🚀 AI Portfolio Projects

> These are personal/portfolio projects built to develop and demonstrate AI engineering skills.

---

### 🔀 Omni-Router — Production LLM Gateway with Semantic Caching & Intent Routing
> **Stack:** Python · FastAPI · FAISS · Redis · ONNX Runtime · LiteLLM · Groq · ARQ · DeepEval · MLflow

A production-style LLM gateway combining **semantic caching, intent-based model routing, async quality evaluation, and experiment observability** — designed to minimize latency and cost while preserving quality for complex queries.

**⚡ Architecture Highlights**
- **ONNX embeddings on CPU**: Uses `ORTModelForFeatureExtraction` with NumPy mean pooling — fast local vectorization without full PyTorch overhead
- **Semantic cache before LLM call**: Requests are embedded and searched via FAISS (`IndexFlatIP`); high-similarity queries served from Redis, skipping LLM inference entirely
- **Two-tier model routing**: Cache misses classified as `simple` or `complex` — simple → **Llama**, complex → **Qwen**

**🧠 Classifier Design**
- Built binary intent classifier using sentence embeddings from `all-MiniLM-L6-v2`
- Benchmarked: Logistic Regression, SVM, Random Forest, XGBoost, KNN, NearestCentroid, and deep neural network architectures
- **Chose NearestCentroid**: lightweight at inference, stable with embedding-space separation, easy to debug

**📬 Async Evaluation (ARQ + DeepEval)**
- Evaluation jobs enqueued *after* response returned — zero latency impact
- Runs `AnswerRelevancyMetric` and `ToxicityMetric` with failure isolation
- Drives closed-loop quality monitoring for drift detection and retraining signals

**📊 MLflow Observability**
- Gateway logs: model used · route taken · request latency · prompt size
- Worker logs: relevancy · toxicity · evaluation duration · judge model

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
              ↓ (async)
       ARQ Job Queue → DeepEval → MLflow
```

[![GitHub](https://img.shields.io/badge/View%20on%20GitHub-121011?style=flat-square&logo=github)](https://github.com/Ajeetkrup)

---

### 🗂️ DocuMind — Intelligent Multi-Document Q&A
> **Stack:** Python · LangChain · ChromaDB · Groq · RAGAS · Gradio

- **Hybrid retrieval** (BM25 + semantic search) for grounded, hallucination-reduced answers
- Multi-agent pipeline: relevance checker → retriever → response generator with query rewriting
- Supports PDF, DOCX, TXT, Markdown via Docling parser
- Evaluated with RAGAS metrics (faithfulness, answer relevance, context precision)

[![GitHub](https://img.shields.io/badge/View%20on%20GitHub-121011?style=flat-square&logo=github)](https://github.com/Ajeetkrup)

---

### 🎙️ Voice AI Assistant — Real-time STT/LLM/TTS Pipeline
> **Stack:** Python · FastAPI · WebSockets · OpenAI · Deepgram

- Sub-300ms round-trip: Deepgram STT → streaming LLM → TTS audio over WebSockets
- Streaming LLM inference for improved perceived responsiveness
- Scalable WebSocket architecture for concurrent multi-user sessions

---

### 📺 YouTube Transcript Q&A — RAG over Video Content
> **Stack:** Python · LangChain · ChromaDB · Groq · Streamlit

- Auto-pipeline: transcript extraction → chunking → embeddings → vector storage → semantic Q&A
- Live Streamlit app with sub-2s end-to-end query processing

---

## 🛠️ Stack

### 🤖 AI / LLM
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

### 🎙️ Voice & Realtime
![Deepgram](https://img.shields.io/badge/Deepgram-101010?style=flat-square&logoColor=white)
![WebSockets](https://img.shields.io/badge/WebSockets-010101?style=flat-square&logo=socket.io&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=flat-square&logo=fastapi)

### ⚙️ ML Engineering
![PyTorch](https://img.shields.io/badge/PyTorch-%23EE4C2C.svg?style=flat-square&logo=PyTorch&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=flat-square&logo=scikit-learn&logoColor=white)
![MLflow](https://img.shields.io/badge/MLflow-0194E2?style=flat-square&logo=mlflow&logoColor=white)
![RAGAS](https://img.shields.io/badge/RAGAS%20Eval-22C55E?style=flat-square&logoColor=white)

### 🌐 Frontend (Production Experience)
![React](https://img.shields.io/badge/React-%2320232a.svg?style=flat-square&logo=react&logoColor=%2361DAFB)
![Next.js](https://img.shields.io/badge/Next.js-black?style=flat-square&logo=next.js&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-%23007ACC.svg?style=flat-square&logo=typescript&logoColor=white)
![TailwindCSS](https://img.shields.io/badge/TailwindCSS-%2338B2AC.svg?style=flat-square&logo=tailwind-css&logoColor=white)
![Redux](https://img.shields.io/badge/Redux-%23593d88.svg?style=flat-square&logo=redux&logoColor=white)

### ☁️ Infra & Backend
![AWS](https://img.shields.io/badge/AWS-%23FF9900.svg?style=flat-square&logo=amazon-aws&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-%230db7ed.svg?style=flat-square&logo=docker&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-%23DC382D.svg?style=flat-square&logo=redis&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-%23316192.svg?style=flat-square&logo=postgresql&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-6DA55F?style=flat-square&logo=node.js&logoColor=white)

---

## 💼 Experience

**🏢 Software Engineer — InnovationM** *(Mar 2024 – Present)*

Full-stack engineering on AI-adjacent products — voice interfaces, real-time systems, and enterprise dashboards:
- Built **voice chatbot UI** integrating Speech-to-Text API with Redux Toolkit — reduced HR query response time by 40% across 200+ daily interactions
- Architected **WebSocket-based real-time interview engine** (React, TypeScript) — reduced question-delivery latency by 40%, supporting 150+ daily sessions
- Led **CRA → Vite migration** across iMPortal and FoxMatrix — 70% faster cold-start, zero Jest regression failures
- Delivered **Next.js SSR + memoization** for Revsure.ai (50+ enterprise clients) — 30% page load reduction tracked via New Relic
- Built **Storybook design system** across 3 product lines — 20+ WCAG-compliant components, 25% reduction in PR review cycle time

**🏢 Full Stack Developer — Klimb.io** *(May 2023 – Mar 2024)*

- Implemented **Redis caching layer** — API response time 800ms → 250ms (68% gain)
- Built TanStack Query server-state management — 55% higher cache hit rate, 40% less boilerplate
- Scaled React + Node.js app to **500+ concurrent users** with 99.9% uptime through 3x traffic spikes
- Built executive dashboards processing 10,000+ data points/day with virtualized rendering

**🏢 Teaching Assistant — Coding Ninjas** *(Oct 2022 – Feb 2023)*

- Mentored 100+ students in Data Structures, Algorithms, and Web Development
- Reviewed code submissions and led doubt-resolution sessions

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

![](https://github-readme-stats.vercel.app/api?username=ajeetkrup&theme=midnight-purple&hide_border=true&include_all_commits=true&count_private=true)

![](https://github-readme-streak-stats.herokuapp.com/?user=ajeetkrup&theme=midnight-purple&hide_border=true)

![](https://github-readme-stats.vercel.app/api/top-langs/?username=ajeetkrup&theme=midnight-purple&hide_border=true&include_all_commits=true&count_private=true&layout=compact)

</div>

---

## 🎓 Education

**B.Tech — Computer Science & Engineering**
I.K. Gujral Punjab Technical University · 2019–2023 · **CGPA: 8.67 / 10**

---

## 📫 Let's Connect

Open to **AI Engineer / LLM Engineer** roles and high-impact freelance AI projects.

<div align="center">

| | |
|---|---|
| 📧 | [ajeetkrup401@gmail.com](mailto:ajeetkrup401@gmail.com) |
| 💼 | [linkedin.com/in/ajeet-kumar-upadhyay](https://linkedin.com/in/ajeet-kumar-upadhyay) |

</div>

---

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:24243e,50:302b63,100:0f0c29&height=100&section=footer" />

*"3 years of production instinct. Now applying it to AI."*

</div>
