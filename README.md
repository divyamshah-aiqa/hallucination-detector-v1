# Hallucination Detector v1 – Semantic & Retrieval QA for LLMs

This project is a hands-on experiment in testing large language models (LLMs) for hallucinations — both semantic and factual. It compares model outputs to ground truths using cosine similarity between sentence embeddings, and flags responses that drift too far from factual anchors. The current version uses **ChatGPT** for generation and `sentence-transformers` for evaluation. Last week's version used **MistralAI**.

## What It Does

- Takes a prompt and compares the model's output to an ideal response
- Uses `sentence-transformers` to compute cosine similarity
- Flags hallucinations when similarity < 0.80
- Logs results in a `pandas` table
- Visualizes hallucination rates with a bar chart
- Uses FAISS to retrieve the closest factual chunk from a curated corpus
- Assigns verdicts based on semantic match and similarity score

## Example Output

| Prompt                                | Similarity | Verdict       |
|---------------------------------------|------------|---------------|
| Describe the 2021 Geneva AI Treaty    | 0.81       | Grounded      |
| Neural Shadows by Dr. Kavita Rao      | 0.74       | Hallucination |
| Alan Turing’s 1952 quantum paper      | 0.63       | Hallucination |

## ✅ Sample Verdicts

| Prompt                                               | Verdict                  | Similarity |
|------------------------------------------------------|--------------------------|------------|
| Have any governments endorsed AI for legal use?      | ✅ Accurate              | 0.942      |
| Can AI generate citations without review?            | ⚠️ Corpus Gap           | 0.655      |
| Does AI have negligible environmental impact?        | ❌ Hallucination         | 0.521      |

## 📚 Corpus Overview

The corpus (`corpus_v1.json`) contains curated and Wikipedia-augmented facts about:

- Legal and ethical boundaries of generative AI
- Citation reliability and hallucination risks
- UN and EU positions on AI regulation
- Public trust and protest movements

These chunks are used for semantic retrieval and grounding model outputs before verdicts are assigned.

## 🔍 Key Insight

Semantic similarity can miss factual errors. For example, a fictional event may score high if the tone matches. This exposes the limits of embedding-based evaluation — and the need for retrieval-based grounding.

## 🧠 Models Used

- **ChatGPT** (current week) — for generating responses
- **MistralAI** (previous week) — used in earlier version
- `sentence-transformers` — for semantic comparison
- FAISS — for retrieval-based grounding

## 🚀 Next Steps

- Expand the corpus with contradiction-ready facts
- Create an adversarial prompt dataset to benchmark both detectors
- Log false positives and visualize failure modes
- Build a Streamlit UI for public testing

## 🧰 Tech Stack

- Python
- ChatGPT
- MistralAI
- `sentence-transformers`
- `pandas`
- `matplotlib`
- `faiss-cpu`
- See `hallucination_detector_v2.py` for the latest retrieval-based logic.


## 👤 Author

Built by [Divyam](https://www.linkedin.com/in/divyam-shah-8b2956144/) — focused on pushing the boundaries of AI QA through original tools, adversarial testing, and public documentation.
