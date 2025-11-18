# Post-Hoc Debiasing of BERT via Combined-Loss LoRA and Downstream Co-Adaptation

![Project Architecture](images/architecture_diagram.png)

## 📌 Abstract
This project introduces a novel two-stage framework to mitigate societal stereotypes in Large Language Models (BERT) without sacrificing downstream performance. We propose a **Combined Loss** function for intrinsic debiasing and a **Co-Adaptation** strategy for downstream transfer.

## 🚀 Key Features
* **Combined Loss Objective:** Optimizes $L_{MLM} + L_{PLL}$ to balance utility and fairness.
* **LoRA Integration:** Uses Low-Rank Adaptation for parameter-efficient training.
* **Co-Adaptation:** Demonstrates that unfreezing adapters recovers **12% more accuracy** than standard frozen baselines.

## 🛠️ Methodology
1. **Upstream Phase:** Intrinsic debiasing using the **CrowS-Pairs** dataset with neutral anchor augmentation.
2. **Downstream Phase:** Transfer learning on the **Bias in Bios** dataset comparing Frozen vs. Unfrozen (Co-Adaptation) strategies.

## 📊 Results
| Method | Accuracy | TPR-Gap (Fairness) |
| :--- | :--- | :--- |
| Baseline (Frozen) | 69.6% | 0.227 |
| **Co-Adaptation (Ours)** | **81.9%** | **0.167** |

![Results Graph](images/results_graph.png)

## 💻 Installation & Usage
1. Clone the repo:
   ```bash
   git clone [https://github.com/yourusername/Post-Hoc-Debiasing-BERT.git](https://github.com/yourusername/Post-Hoc-Debiasing-BERT.git)
