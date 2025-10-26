# Hallucination Detector v1 – Semantic & Retrieval QA for LLMs

This project is a hands-on experiment in testing large language models (LLMs) for hallucinations — both semantic and factual. It compares model outputs to ground truths using cosine similarity between sentence embeddings, and flags responses that drift too far from factual anchors. The current version uses MistralAI for generation and `sentence-transformers` for evaluation.

## What It Does

- Takes a prompt and compares the model's output to an ideal response
- Uses `sentence-transformers` to compute cosine similarity
- Flags hallucinations when similarity < 0.80
- Logs results in a `pandas` table
- Visualizes hallucination rates with a bar chart

## Example Output

| Prompt | Similarity | Verdict |
|--------|------------|---------|
| Describe the 2021 Geneva AI Treaty | 0.81 | Grounded |
| Neural Shadows by Dr. Kavita Rao | 0.74 | Hallucination |
| Alan Turing’s 1952 quantum paper | 0.63 | Hallucination |

## Key Insight

Semantic similarity can miss factual errors. For example, a fictional event may score high if the tone matches. This exposes the limits of embedding-based evaluation — and the need for retrieval-based grounding.

## Model Used

This version uses MistralAI for generating responses and `sentence-transformers` for semantic comparison.

## Next Steps

- Build a retrieval-based hallucination detector using FAISS or Haystack
- Create an adversarial prompt dataset to benchmark both detectors
- Study types of hallucinations (semantic, factual, citation, multi-hop)
- Log false positives and visualize failure modes
  

## Tech Stack

- Python
- MistralAI
- `sentence-transformers`
- `pandas`
- `matplotlib`
- FAISS or Haystack (planned)

## Author

Built by [Divyam](https://www.linkedin.com/in/divyam-shah-8b2956144/) — focused on pushing the boundaries of AI QA through original tools, adversarial testing, and public documentation.
