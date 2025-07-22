# 📘 Module 4: LLMs and Text Generation

>  DeepLearning.AI_ fileciteturn3file0

---

## 📋 Module Overview

- **LLM Foundations**  
- **Transformer Workflows and Grounding**  
- **Advanced Techniques**  
- **Hands-on Project**  

---

## 🔧 Transformer Architecture

- **Origins**: "Attention is All You Need" (Vaswani et al., 2017).  
- **Encoder–Decoder**: Encoder for context understanding; decoder for text generation.  
- **Attention Mechanism**: Each token attends to all others to compute weighted representations.  
- **Layers & Heads**: Multiple transformer layers; each with many attention heads extracting abstract patterns.  

---

## 🔢 Sampling Strategies

- **Greedy Decoding**: Always picks highest-probability token; deterministic but can loop.  
- **Temperature**: Adjusts distribution sharpness (Temp=0 for greedy; >1 for creative).  
- **Top‑K Sampling**: Chooses from top K tokens only.  
- **Top‑P (Nucleus) Sampling**: Chooses from smallest set of tokens whose cumulative probability ≥ P.  
- **Repetition Penalty**: Lowers probability of repeated tokens to avoid loops.  
- **Logit Bias**: Directly boosts or suppresses specific tokens.  

---

## 🏷️ Model Selection & Prompt Engineering

- **LLM Characteristics**: Size, cost per token, context window, latency, training cutoff.  
- **Prompt Formats**: JSON-like `messages` with roles (system, user, assistant).  
- **System Prompt**: High‑level instructions (tone, guidelines, grounding rules).  
- **Prompt Templates**: Structured injection of system prompt, history, retrieved docs, and user query.  

---

## 🛠️ Advanced Prompting Techniques

- **In‑Context Learning**: Few‑shot or one‑shot examples in prompt for pattern learning.  
- **Chain of Thought**: Encourage step‑by‑step reasoning (`Think step by step`).  
- **Scratchpad**: Use intermediate reasoning blocks to improve accuracy.  
- **Templates**: Embed examples and retrieval chunks systematically.  

---

## 🌐 Context Window Management

- **Advanced Techniques Consume More Tokens**: Reasoning tokens, RAG docs all count.  
- **Context Pruning**: Keep only the latest N messages or relevant chunks.  
- **Efficient Chunk Inclusion**: Only include documents pertinent to the current query.  

---

## 🚫 Handling Hallucinations & Citation

- **Why Hallucinate**: LLMs predict plausible tokens, not factual ones.  
- **RAG Grounding**: Force use of retrieved docs; system prompt to cite only factual info.  
- **Citation Generation**: Instruct LLM to append `[n]` citations; use ContextCite for attribution.  
- **Self-Consistency**: Multiple generations to detect inconsistencies (costly).  

---

## 📊 Evaluating LLM Performance

- **Retriever vs. LLM Roles**: Evaluate LLM’s response clarity, relevance, faithfulness.  
- **Response Relevancy**: Can you infer the prompt from the response? (cosine similarity).  
- **Faithfulness**: % of factual claims supported by retrieved docs.  
- **RAGAS Metrics**: Noise sensitivity, citation quality via LLM-as-judge.  
- **System‑Level A/B Testing**: Capture user feedback and isolate changes.  

---

## 🤖 Agentic RAG

- **Flowchart Architecture**: Split tasks across router, retriever, LLM agents, citation model.  
- **Sequential, Conditional, Iterative, Parallel Workflows**: Customize pipelines per task.  
- **External Tools**: Integrate databases, code, web search for richer responses.  

---

## 🔁 RAG vs Fine‑Tuning

- **RAG**: Best for injecting fresh knowledge at query time.  
- **Fine‑Tuning**: Best for domain/task specialization; changes model behavior, not knowledge.  
- **Combined Approach**: Fine‑tune models to leverage retrieved context more effectively.  

---

## ✅ Conclusion

- **Transformers & Attention** underpin LLM capabilities.  
- **Sampling & Decoding** strategies balance creativity and accuracy.  
- **Prompt Engineering** & **Grounding** prevent hallucinations.  
- **Evaluation** ensures quality and trust.  
- **Agentic Systems** and **Fine‑Tuning** unlock advanced RAG deployments.
