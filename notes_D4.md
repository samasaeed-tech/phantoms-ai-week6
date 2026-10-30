# W6D4: Cosine Similarity, Euclidean Distance & Mini Semantic Search

## 1. Manual Math Calculations (Small Vectors Example)
Let's take two sample vectors: 
* $v_1 = [1, 2, 3]$
* $v_2 = [4, 5, 6]$

* **Dot Product:** 
  $$\text{Dot Product} = (1 \times 4) + (2 \times 5) + (3 \times 6) = 4 + 10 + 18 = 32$$

* **Magnitudes (Norms):**
  * $\|v_1\| = \sqrt{1^2 + 2^2 + 3^2} = \sqrt{1 + 4 + 9} = \sqrt{14} \approx 3.7416$
  * $\|v_2\| = \sqrt{4^2 + 5^2 + 6^2} = \sqrt{16 + 25 + 36} = \sqrt{77} \approx 8.7750$

* **Cosine Similarity:**
  $$\text{Cosine Similarity} = \frac{\text{Dot Product}}{\|v_1\| \times \|v_2\|} = \frac{32}{3.7416 \times 8.7750} = \frac{32}{32.8328} \approx 0.9746$$

---

## 2. Concept Explanations
* **Cosine Similarity:** Measures the cosine of the angle between two vectors in a multi-dimensional space. It determines how closely aligned the vectors are in **direction**, completely ignoring their scale or magnitude. This makes it ideal for text embeddings where longer documents might have higher absolute vector values but share the exact same semantic topic.
* **Euclidean Distance:** Measures the straight-line distance between two points in Euclidean space. Unlike cosine similarity, it is heavily influenced by the magnitude and length of the vectors.

---

## 3. Magnitude Test & Results
* **Experiment:** Multiplying vector $v_1$ (Sentence 1) by a factor of 10 (`v1_scaled = embeddings[0] * 10`).
* **Cosine Similarity:** Remained completely unchanged at **`0.6888`** because the directional angle between the vectors did not alter[cite: 3].
* **Euclidean Distance:** Increased dramatically from **`0.7889` to `9.3394`** because the absolute distance in space expanded significantly due to the scale change[cite: 3].

---

## 4. Mini Semantic Search Results
* **Query:** *"I want to build a machine learning model using Python."*[cite: 3]
* **Top 3 Retrieved Sentences:**
  1. `[Score: 0.5291]` - Python is a flexible programming language used for web development and AI.[cite: 3]
  2. `[Score: 0.4731]` - Software engineers use Python to build modern scalable applications.[cite: 3]
  3. `[Score: 0.3533]` - Machine learning models require clean datasets for accurate training.[cite: 3]
* **Analysis:** The search successfully ranked sentences based on deep semantic closeness (matching Python, web development/AI, and machine learning) rather than relying purely on exact keyword matching.
