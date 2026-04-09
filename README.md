# ASE-materials
# Catching the AI Imprint: A Hybrid Framework for Mixed-Authorship AI Code Detection

[![Conference](https://img.shields.io/badge/Conference-ASE-blue.svg)](#) [![Dataset](https://img.shields.io/badge/Dataset-WildDeclCode-green.svg)](#) [![Framework](https://img.shields.io/badge/Framework-HybridSense-orange.svg)](#)

This repository contains the dataset, replication materials, and experimental results for the paper **"Catching the AI Imprint: A Hybrid Framework for Mixed-Authorship AI Code Detection"**. 

With the deep integration of AI into software engineering, detecting AI-generated code has emerged as a critical research imperative. Existing studies primarily rely on synthetic data, lacking investigation into authentic, mixed-authorship code. To bridge this gap, we introduce **WildDeclCode**, a real-world mixed-authorship dataset, and **HybridSense**, a state-of-the-art detection framework.

## 📂 Repository Structure & Paper Mapping

The directory structure of this repository maps directly to the core components and evaluation sections of the manuscript:

```text
├── WildDeclCode/
│   ├── ai_generated_code/
│   └── human_written_code/
├── HybridSense/
│   ├── C/
│   ├── C++/
│   ├── Java/
│   ├── Javascript/
│   ├── Python/
│   ├── Typescript/
│   └── HML.md  <-- Detailed explanation of HML features
├── Perplexity/
├── Pre-trained Model-based/
└── Traditional Feature-based/
```
1. **Dataset: `WildDeclCode/`**
   * **Contents:** The raw dataset files, strictly partitioned into `ai_generated_code` and `human_written_code` subsets. It covers six mainstream programming languages (C, C++, Java, JavaScript, Python, TypeScript) and comprises 11,258 source files.
   * **Paper Reference:** Fully detailed in **Section 3.1: Dataset Construction**. The specific collection, pairing, and validation methodologies are discussed in **Section 3.1.5** (Human-Written Code Collection) and **Section 3.1.6** (Dataset Statistics and Granularity Division).

2. **Proposed Framework: `HybridSense/`**
   * **Contents:** Contains the experimental and ablation data for our multi-module ensemble framework. This folder includes:
     * Ablation data for the individual feature modules: Traditional Lexical and Syntactic Features (LSF), Deep Semantic Features (DSE), and Human Micro-Habits (HML).
     * Integrated ensemble results.
     * Single-classifier performance data (HistGB, Random Forest, LightGBM) on the WildDeclCode dataset. 
   * **Paper Reference:** The methodology is introduced in **Section 3.2.4**. The `HML.md` document directly corresponds to the detailed explanation of **Table 1: HML Feature Selection**. The experimental results corresponding to this folder are analyzed in **Section 4.3 (RQ3: Ablation Study of HybridSense Module Combinations)** and summarized in **Table 4**.

3. **Baselines: `Perplexity/`**
   * **Contents:** Experimental results evaluating various perplexity-based methods (e.g., Log-p(x), Entropy, DetectGPT, NPR) on the WildDeclCode dataset. 
   * **Paper Reference:** The baseline setups are described in **Section 3.2.3**. The results are discussed in **Section 4.1 (RQ1: Effectiveness of Existing Detection Methods)** and presented in **Table 2**.

4. **Baselines: `Pre-trained Model-based/`**
   * **Contents:** Experimental results evaluating pre-trained model-based approaches (specifically GPTSniffer) on the WildDeclCode dataset, including their AUCs and ACCs across different programming languages.
   * **Paper Reference:** The baseline setup is described in **Section 3.2.2**. The results and limitations regarding cross-language generalization are analyzed in **Section 4.1 (RQ1)** and presented in **Table 2**.

5. **Baselines: `Traditional Feature-based/`**
   * **Contents:** Experimental results evaluating manually designed lexical and syntactic feature approaches (e.g., Idialu et al. for Python, Bukhari et al. for C) on the WildDeclCode dataset. 
   * **Paper Reference:** The baseline setups are described in **Section 3.2.1**. The results are discussed in **Section 4.1 (RQ1)** and presented in **Table 2**.
