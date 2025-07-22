# Introduction to Information Retrieval
*Core Concepts for RAG Systems*

## 1. The Retrieval Process

```mermaid
flowchart LR
    A[User Query] --> B(("Retriever (Librarian)"))
    B --> C["Knowledge Base (Library)"]
    C --> D["Relevant Documents (Books)"]
    D --> E[LLM Response]
```
**Key Analogy:**
- **Librarian** = Retriever algorithm
- **Library Sections** = Vector index
- **Book Recommendations** = Top-K document retrieval

## 2. Core Components

```mermaid
flowchart TD
    A[User Query] --> B(Tokenizer)
    B --> C[Query Terms]
    C --> D{Retriever}
    D --> E[(Index)]
    E --> F[Ranked Documents]
    F --> G[Response Generator]
    
    subgraph Retrieval System
        B
        D
        E
    end

    style A fill:#4CAF50,stroke:#388E3C,color:white
    style B fill:#2196F3,stroke:#0b7dda,color:white
    style D fill:#FF9800,stroke:#F57C00,color:white
    style E fill:#9C27B0,stroke:#7B1FA2,color:white
    style G fill:#607D8B,stroke:#455A64,color:white
```

## 3. Relevance Scoring

**Scoring Methods:**
- Cosine similarity
- BM25 (traditional IR)
- Hybrid scoring

```mermaid
graph TD
    A[Query] --> B[Embedding]
    C[Document] --> D[Embedding]
    B --> E[Similarity Calculation]
    D --> E
    E --> F[Ranked Results]
```

## 4. Precision vs. Recall Tradeoff

**Operational Challenges:**
- Avoiding false positives (irrelevant docs)
- Preventing false negatives (missed relevant docs)

## 5. Modern Implementations

```mermaid
journey
    title Evolution of Retrieval Systems
    section Traditional
      SQL Databases: 5: 2000
      TF-IDF: 3: 2005
    section Modern
      Vector Search: 8: 2020
      Neural Retrievers: 9: 2023
```

**Key Technologies:**
- Vector Databases (Pinecone, Weaviate)
- Dense Retrievers (DPR, ColBERT)
- Hybrid Search (Combining keywords + vectors)

## Key Takeaways

**Fundamental Goal:**
> "Find the most relevant information for a query from large collections"

**RAG Integration:**
- Retrievers act as LLM's "research assistants"

**Critical Metrics:**

| Metric    | Ideal Target |
|-----------|--------------|
| Precision | >80%         |
| Recall    | >90%         |
| Latency   | <100ms       |

**Implementation Checklist:**
- Design document processing pipeline
- Choose indexing strategy (inverted index, HNSW)
- Select scoring/ranking approach
- Optimize top-K retrieval

## Visual Summary

```mermaid
mindmap
  root((Information Retrieval))
    Principles
      "Precision/Recall"
      "Ranking"
      "Query Understanding"
    Techniques
      "Vector Search"
      "Keyword Search"
      "Hybrid"
    Applications
      "Web Search"
      "RAG Systems"
      "Enterprise Search"
```
