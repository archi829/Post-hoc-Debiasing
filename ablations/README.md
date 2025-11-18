# 🧪 Ablation Studies & Supplementary Experiments

This directory documents the experimental journey and scientific rigor behind our final proposed framework. We conducted several ablation studies to justify our architectural choices (LoRA, Combined Loss, Co-Adaptation) and to demonstrate the failure modes of alternative approaches.

## 📂 Contents

### **1. `01_ablation_no_utility_loss.ipynb`**
* **Hypothesis:** Can we achieve perfect fairness (50% bias score) by training *only* on the Fairness Loss ($L_{PLL}$)?
* **Outcome (Negative Result):** The model achieved a very low bias score (~50%) but suffered from **Catastrophic Forgetting** of language capabilities. Perplexity skyrocketed (> 1000), rendering the model incoherent.
* **Conclusion:** This justifies the inclusion of the **Utility Term ($L_{MLM}$)** in our final Combined Loss function.

### **2. `02_ablation_peft_architecture_search.ipynb`**
* **Hypothesis:** Which Parameter-Efficient Fine-Tuning (PEFT) method balances fairness and utility best: **LoRA** or **Prompt Tuning**?
* **Outcome:**
    * **Prompt Tuning:** Failed to converge; high perplexity instability.
    * **LoRA:** Successfully minimized intrinsic bias while maintaining low perplexity.
* **Conclusion:** LoRA was selected as the optimal adapter architecture for our final framework.

### **3. `03_ablation_triplet_loss_failure.ipynb`**
* **Hypothesis:** Can **Triplet Loss** on [CLS] embeddings effectively debias the model?
* **Outcome (Negative Result):** Even with a corrected dataset, Triplet Loss failed to reduce the intrinsic bias score (remained ~59%). This empirically proves that bias in Masked Language Models lives in the **token probability distributions**, not just the sentence embeddings.
* **Conclusion:** Direct probability optimization (via PLL) is superior to embedding-distance optimization for this task.

* **Conclusion:** This baseline confirms the **Fairness-Utility Trade-off** inherent in frozen methods, motivating our novel **Co-Adaptation (Unfreezing)** strategy used in the main project.