# 🧠 Comparing Language Models for Text Generation via TOPSIS

> **Author:** Sahil Kumar
> **Roll Number:** 102316091
> **Course:** UCS 654 — Predictive Analytics

---

## 🔍 Overview

This assignment tackles a fundamental question in NLP engineering:
*When multiple pre-trained language models are available, which one should you actually deploy?*

Rather than relying on a single benchmark, this study applies **TOPSIS** *(Technique for Order Preference by Similarity to Ideal Solution)* — a structured multi-criteria decision framework — to rank six popular autoregressive Transformers against **five distinct performance and efficiency indicators**.

---

## ⚙️ Pipeline at a Glance

```
  [ WikiText-2 Dataset ]
          │
          ▼
  [ Preprocessing & Tokenization ]
          │
          ▼
  [ Inference on 6 Transformer Models ]
          │
          ▼
  [ Computing 5 Evaluation Metrics ]
          │
          ▼
  [ TOPSIS Multi-Criteria Ranking ]
          │
          ▼
  [ Best-Fit Model Selected ✅ ]
```

The entire workflow runs end-to-end on **Google Colab** with GPU acceleration enabled.

---

## 📦 Experiment Configuration

| Parameter | Value |
|-----------|-------|
| Task | Autoregressive Text Generation |
| Benchmark Dataset | WikiText-2 (Raw Split) |
| Evaluation Passages | 200 |
| Generation Prompts | 100 |
| Total Models Benchmarked | 6 |
| Ranking Strategy | TOPSIS |
| Runtime | Google Colab (GPU) |

---

## 🤖 Models Under Evaluation

| # | Model Name | Hugging Face Identifier | Param Count |
|---|------------|-------------------------|-------------|
| 1 | GPT-2 | `gpt2` | 124 M |
| 2 | GPT-2 Medium | `gpt2-medium` | 355 M |
| 3 | DistilGPT-2 | `distilgpt2` | 82 M |
| 4 | BLOOM-560M | `bigscience/bloom-560m` | 560 M |
| 5 | OPT-350M | `facebook/opt-350m` | 350 M |
| 6 | Pythia-410M | `EleutherAI/pythia-410m` | 410 M |

---

## 📏 Evaluation Criteria

| Metric | Optimization Direction | What It Measures |
|--------|------------------------|------------------|
| BLEU Score | ↑ Higher is better | n-gram precision vs. reference text |
| ROUGE-L | ↑ Higher is better | Longest common subsequence overlap |
| Perplexity | ↓ Lower is better | Prediction confidence of the model |
| Inference Latency (ms) | ↓ Lower is better | Time to produce one generation |
| Model Size (MB) | ↓ Lower is better | Disk/memory footprint |

---

## 🔄 How It Works

### Input
A plain-text prompt is fed to each model for continuation:
```
"The history of artificial intelligence began in"
```

### Output
Each model produces a text continuation, for example:
```
"The history of artificial intelligence began in the 1950s, when pioneering
researchers first theorized that machines could replicate human cognition..."
```

Additionally, a **ranked comparison table** is generated for all six models, including their TOPSIS closeness scores and final positions.

---

## 📊 Benchmark Results

| Model | BLEU ↑ | ROUGE-L ↑ | Perplexity ↓ | Latency (ms) ↓ | Size (MB) ↓ | TOPSIS Score | Rank |
|-------|--------|-----------|--------------|----------------|-------------|--------------|------|
| **DistilGPT-2** | 0.2315 | 0.3198 | 36.72 | **9.84** | **331.24** | **0.7375** | **🥇 1** |
| GPT-2 | 0.2548 | 0.3412 | 29.45 | 18.32 | 487.56 | 0.7248 | 🥈 2 |
| OPT-350M | 0.2734 | 0.3589 | 25.61 | 22.18 | 662.78 | 0.6296 | 🥉 3 |
| Pythia-410M | 0.2689 | 0.3478 | 26.84 | 24.56 | 789.45 | 0.5279 | 4 |
| BLOOM-560M | 0.2672 | 0.3521 | 27.33 | 28.45 | 1065.32 | 0.3450 | 5 |
| GPT-2 Medium | **0.2891** | **0.3687** | **22.18** | 34.71 | 1421.48 | 0.2625 | 6 |

### 💡 Key Observations

- **GPT-2 Medium** tops every quality metric (BLEU, ROUGE-L, Perplexity) but **ranks last** when efficiency is factored in — it's simply too slow and too large.
- **DistilGPT-2** wins the overall ranking by delivering a compelling speed-size-quality trade-off that no heavier model can match.
- **OPT-350M** and **Pythia-410M** occupy the middle ground — decent quality without extraordinary efficiency.
- TOPSIS makes it clear: **the best model is context-dependent**, and raw quality scores alone are insufficient for deployment decisions.

---

## 📈 Visualization

<img width="990" height="490" alt="TOPSIS Model Ranking Chart" src="results/topsis_ranking.png" />

*Figure: TOPSIS Closeness Coefficients for all six evaluated text generation models*

---

## 🏁 Conclusion

This experiment demonstrates that **choosing a language model is an engineering trade-off**, not just a quality competition.

Key insights from this study:

- ✅ **TOPSIS** enables principled, reproducible model selection across heterogeneous criteria
- ✅ Lightweight models like **DistilGPT-2** can outperform heavier ones in real-world deployment scenarios by leveraging better efficiency
- ✅ Heavy models like **GPT-2 Medium** are best reserved for offline, batch-generation tasks where latency is not a bottleneck
- ✅ Multi-metric ranking exposes trade-offs that single-metric evaluation entirely misses

> **Bottom line:** If computational budget matters — and it almost always does — **DistilGPT-2** is the pragmatic champion of this benchmark.

---

*Assignment submitted as part of UCS 654 | Thapar Institute of Engineering & Technology*
