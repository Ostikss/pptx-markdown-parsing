## PPTX to Markdown Converter with Neural Layout Parsing

# **1. Project tasks:**
- Implemented the baseline PPTX-to-Markdown converter using heuristic parsing.
- Designed and implemented PPTX parsing logic (text, tables, images, equations).
- Analyzed the reference paper and conducted hybrid approach experiments.
- Implement the neural network in PyTorch.
- Trained the graph neural network and assisted with experiments.
# **2. Main insights**
The central goal of the project was to compare two fundamentally different approaches to PPTX parsing: a fast heuristic-based method and a neural layout-aware method inspired by the Docling paper.
Baseline approach
The baseline converter is extremely fast and efficient. It performs well on slides that contain mostly text, simple bullet lists, and straightforward layouts. In such cases, the produced Markdown is clean, readable, and well structured.
However, this approach relies heavily on simple geometric heuristics. As a result, it struggles with: complex tables, images and mixed content, non-standard or irregular layouts.
Docling-style approach
The neural layout-aware approach is significantly more robust. By treating slide elements as nodes in a graph and learning their relationships, the neural model can correctly parse complex layouts, including tables, images, and multi-block structures.
The main advantage of this approach is structural accuracy: the resulting Markdown better preserves reading order, hierarchy, and semantic grouping.
The main drawback is speed: neural inference is considerably slower than heuristic parsing.
Hybrid approach experiments
I experimented with a hybrid strategy that combines both methods. The idea was to use the heuristic parser where possible and fall back to the neural model for difficult cases.
In practice, several limitations became apparent:
-	If a slide is a single complex object, heuristic parsing already fails at the first stage.
-	Running all slides through the neural model removes the performance benefits of the baseline.
-	A truly effective hybrid approach would require an additional slide complexity classifier to decide which method to apply.
Without such a classifier, the hybrid system becomes either inefficient or unreliable.
# **3. Future plans**
-	Based on the project results, several directions for future work appear promising:
Develop a lightweight classifier to distinguish between simple and complex slides, enabling selective use of neural parsing.
-	Apply neural models only to problematic elements (tables, images, dense blocks), while keeping heuristic parsing for the rest.


