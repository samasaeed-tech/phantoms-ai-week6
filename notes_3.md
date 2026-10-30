# W6D3: Text Embeddings & Semantic Similarity Analysis

## 1. Concept Summary
* **Embedding Definition:** An embedding is a dense numerical vector representation of text in a high-dimensional continuous vector space. Instead of matching exact surface keywords, it captures the underlying **semantic meaning, context, and relationships** of the text.
* **Dimensions:** In this experiment using `all-MiniLM-L6-v2`, each sentence is transformed into a **384-dimensional vector**.
* **Semantic vs. Keyword Matching:** Keyword matching checks for exact word matches, whereas semantic similarity evaluates contextual closeness. This enables models to recognize that "Real Madrid victory" and "Football club win" share high similarity despite having completely different words.

---

## 2. Experimental Results Table (Cosine Similarity)

| Pair Description | Sentences Compared | Expected Similarity | Actual Cosine Similarity |
| :--- | :--- | :--- | :--- |
| **Programming vs. Programming** | S1 (Python web/AI) & S2 (Software engineers Python) | High (~0.7) | **0.6888** |
| **Football vs. Football** | S3 (Real Madrid) & S4 (Football victory) | High (~0.6) | **0.5020** |
| **Food vs. Food** | S5 (Chocolate cake/coffee) & S6 (Cocoa dessert) | High (~0.5) | **0.4678** |
| **Homonym Test ("Bank")** | S7 (Money Bank) & S8 (River Bank) | Low / Moderate | **0.2809** |
| **Football vs. Economy** | S3 (Real Madrid) & S10 (Global markets) | Near Zero / Negative | **-0.0286** |
| **Programming vs. AI** | S1 (Python) & S9 (Machine Learning) | Low / Moderate | **0.0417** |

---

## 3. Analysis & Key Takeaways

1. **Expectations vs. Reality:**
   * Domain-aligned sentences (Programming, Football, Food) achieved high semantic similarity scores, validating that embeddings capture context rather than exact words.
   * Completely unrelated domains (Football vs. Economy) produced a negative score (`-0.0286`), indicating near-complete orthogonality in vector space.

2. **The "Bank" Context Analysis (Homonym Handling):**
   * The model effectively distinguished between financial "bank" (S7) and geographical "river bank" (S8).
   * Despite sharing the exact keyword "bank", the similarity score dropped significantly to `0.2809`. This proves that contextual embeddings incorporate surrounding tokens (e.g., *deposit/savings* vs. *river/water*) to determine true semantic meaning.

3. **Multilingual Limitations:**
   * English-centric models like `all-MiniLM-L6-v2` perform optimally on English input. For multilingual or Arabic applications, specialized models such as `paraphrase-multilingual-MiniLM-L12-v2` or Gemini Embeddings API should be used.
   * 
