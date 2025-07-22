# 📘 Module 3: Information Retrieval in Production

> DeepLearning.AI_

---

## 📋 Module Overview

- Approximate Nearest Neighbors (ANN) algorithms
- Hierarchical Navigable Small World (HNSW)
- Vector Databases: setup, indexing, search
- Chunking strategies and advanced techniques
- Query parsing: rewriting, NER, HyDE
- Cross-encoders, ColBERT
- Reranking pipelines
- Production best practices

---

## 🔍 Approximate Nearest Neighbors (ANN)

- **KNN (Brute Force)**: Linear scan of all vectors → slow at scale  
- **ANN**: Uses proximity graphs or index structures for sub-linear search  
  - Fast, but may not return absolute nearest neighbors  
- **Neighbor Graphs**: Nodes = vectors, edges connect nearest neighbors fileciteturn2file7

---

## 🧱 Hierarchical Navigable Small World (HNSW)

1. **Layer 3**: ~10 random vectors, rough navigation  
2. **Layer 2**: ~100 vectors, intermediate navigation  
3. **Layer 1**: All vectors, precise nearest-neighbor search  
- Traversal: start at top layer, descend to layer 1 for best match  
- Complexity: roughly logarithmic in dataset size fileciteturn2file19

---

## 📂 Vector Databases

- Optimized storage and ANN search for high-dimensional data  
- Outperform relational databases for semantics-based retrieval  
- **Weaviate** used in this course fileciteturn2file24

### Typical Operations

1. **Setup**: create collections with vectorizer configs  
2. **Load Documents**: batch import with error handling  
3. **Indexing**: build HNSW index for fast ANN  
4. **Search**: `near_text`, BM25, hybrid, filtered queries fileciteturn2file28turn2file29

---

## 🔗 Complete Workflow

```mermaid
graph LR
  A[Configure DB] --> B[Load & Index Data]
  B --> C[Perform Searches]
```
fileciteturn2file32

---

## 📑 Chunking

- **Why?** Stay within token limits, improve relevance, send only useful context fileciteturn2file34
- **Fixed-size**: e.g., 250 characters per chunk; optionally with overlap for context continuity fileciteturn2file39
- **Overlapping**: chunks overlap by 10–20% to avoid cutting sentences fileciteturn2file40
- **Recursive splitting**: split on newline or semantic markers for better structure fileciteturn2file41

---

## 🧠 Advanced Chunking Techniques

- **Semantic chunking**: group sentences by embedding similarity, split when semantic distance exceeds threshold fileciteturn2file46
- **LLM-based chunking**: prompt an LLM to segment document into concept-based chunks fileciteturn2file50
- **Context-aware**: prepend external metadata/context to each chunk for improved retrieval and generation fileciteturn2file51

**Choosing an Approach**:
- Start with fixed-size or recursive splits  
- Experiment with semantic/LLM-based for higher precision  
- Add context-aware as a first improvement fileciteturn2file53

---

## 🔍 Query Parsing

### Query Rewriting

- Clean up user prompts, clarify ambiguity, add domain terminology/synonyms  
- Example: rewrite patient scenario for medical DB search fileciteturn2file57

### Named Entity Recognition (NER)

- Extract entities (places, dates, people, organizations) to refine search filters  
- GLINER demo: tag “The Great Gatsby” as BOOK, “1920s” as DATE fileciteturn2file60

### HyDE (Hypothetical Document Embeddings)

- Generate a hypothetical “ideal” document from the prompt  
- Embed that document for ANN search, matching doc-to-doc instead of prompt-to-doc fileciteturn2file62

---

## ⚖️ Cross-Encoders & ColBERT

### Bi-Encoder

- Embed prompt and docs separately, use ANN for initial retrieval fileciteturn2file64

### Cross-Encoder

- Concatenate prompt+doc, score with deeper model  
- High quality but too slow for large corpora; use for reranking top-k fileciteturn2file65

### ColBERT

- Late interaction on per-token embeddings  
- Balances speed (pre-computed tokens) and quality (token-level matching)  
- Storage-heavy (vector per token) but high relevance fileciteturn2file68

---

## 🔄 Reranking

- Pipeline: initial retrieval (bi-encoder/hybrid) → rerank top results (cross-encoder or LLM scoring) → final docs to LLM fileciteturn2file75
- Improves precision for LLM generation, minimal additional latency fileciteturn2file79

---

## 📌 Key Takeaways

- **ANN & HNSW** for sub-linear retrieval  
- **Vector DBs** streamline indexing and search  
- **Chunking**: foundational step for RAG workflows  
- **Query parsing**: rewriting, NER, HyDE enhance recall/precision  
- **Cross/ColBERT & reranking**: trade quality vs. efficiency

---
