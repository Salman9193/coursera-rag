# How Large Language Models (LLMs) Work
*Core Concepts and RAG Integration*

## 1. LLM Basics: "Fancy Autocomplete"

**Key Properties:**
- **Token-by-Token Generation:** Predicts next word piece (token) based on probability
- **Vocabulary:** 10K-100K tokens (words/subwords/punctuation)
- **Autoregressive:** Each new token depends on previous choices

```mermaid
graph LR
    A["Prompt: "What a beautiful day...""] --> B[Token Probabilities]
    B --> C["shining (80%)"]
    B --> D["rising (15%)"]
    B --> E["exploding (0.1%)"]
    B -->|Random Selection| F["Completion: "the sun is shining""]
```

## 2. Training Process

**How LLMs Learn:**
- **Exposure:** Shown trillions of text snippets
- **Prediction Task:** Guess missing words in sentences
- **Parameter Updates:** Adjusts billions of numerical weights

## 3. Limitations & Hallucinations

**Why Hallucinations Occur:**
- LLMs optimize for likely not true text
- No built-in fact-checking mechanism

```mermaid
graph TD
    A[User Query] --> B{In Training Data?}
    B -->|Yes| C[Factual Response]
    B -->|No| D[Probable-but-False Response]
    D --> E["Hallucination (e.g., 'The sun explodes daily')"]
```

# Key Limitations & Why RAG Solves Them

## 3. Key Limitations

### A. Context Window
**Impact:**
- Longer contexts → higher accuracy but:
  - Quadratic compute growth (attention layers)
  - "Lost in the middle" problem

### B. Computational Costs
**Real-World Examples:**

| Operation         | Cost (Relative) |
|-------------------|-----------------|
| 1k token prompt   | 1x              |
| 10k token prompt  | 100x            |
| 100k token prompt | 10,000x         |




## 4. RAG to the Rescue

**How RAG Fixes LLM Limitations:**
- **Knowledge Gaps:** Provides missing data via retrieval
- **Hallucination Control:** Anchors responses in documents
- **Dynamic Updates:** No retraining needed
- **Optimization:**
    - Retrieval filters 99%+ irrelevant data
    - Enables small models to beat larger ones
    - Cuts costs by 10-100x for domain tasks

```mermaid
sequenceDiagram
    participant User
    participant RAG
    participant LLM
    User->>RAG: "Our Q3 sales trends?"
    RAG->>LLM: Prompt + Retrieved Reports
    LLM->>User: Grounded Response
```

## Key Takeaways

- **LLMs ≠ Knowledge Bases:** They're statistical text predictors
- **Context Window Limits:** Typical range: 4K-1M tokens
- **RAG Synergy:** Retrievers feed LLMs precise data when needed
- - **LLMs fundamentally limited by:**
  - Fixed context windows
  - O(n²) attention scaling
  - Static knowledge
- **RAG strategically overcomes these by:**
  - Dynamic knowledge injection
  - Context compression
  - Continuous updates
 
[Previous](./3_RAG_Architecture.md) | [Home](./Readme.md) | [Next](./5_Intro_to_Information_Retrieval.md)
