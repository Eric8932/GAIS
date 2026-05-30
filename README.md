# Scaling Agentic Capabilities via Grounded Interaction Synthesis

This repository contains the official implementation for our work **"Scaling Agentic Capabilities via Protocol-Grounded Data Synthesis" (GAIS)**.

## 🛠 Setup

### 1. Environment

The training code in this repository is built upon **[LlamaFactory](https://github.com/hiyouga/LlamaFactory)**. 

To set up the environment, please refer to the installation instructions provided in the original LlamaFactory repository.

---

## 📂 Data Preparation

Please download the following files from [WenHang/GAIS](https://huggingface.co/datasets/WenHang/GAIS) and place them in the `data/` directory of this repository:
* `data/gais_nonthink.json`
* `data/gais_think.json`


### Dataset Field Definitions
Each sample in the original data contains the following fields:

| Field | Description |
| :--- | :--- |
| **experience** | The interaction experience between the user and the agent. |
| **tools** | The set of tools available for each specific sample. |
| **policy** | Domain-specific rules and tool-calling constraints for the sample. |
| **tool_category** | The category of each tool (e.g., Read, Write, Process). |
| **tool_difficulty** | A difficulty score assigned to each tool. |
| **tool_dependency** | A complexity score (1-5) for the toolset and details on internal tool dependencies. |

---

## 🚀 Training

We provide training scripts in the `scripts_train` folder.

### Train Qwen3-8B-Base (Non-thinking mode)
```bash
bash scripts_train/Qwen3-8B-Base-gais_nonthink.sh
```

### Train Qwen3-8B-Base (Thinking mode)

```bash
bash scripts_train/Qwen3-8B-Base-gais_think.sh
```


## 📊 Evaluation

We evaluate the agentic capabilities of the trained models across three major tool-calling benchmarks:

**[tau2-bench](https://github.com/hiyouga/LlamaFactory)**: Covering the Airline, Retail, and Telecom domains.

**[BFCL](https://github.com/ShishirPatil/gorilla/tree/main/berkeley-function-call-leaderboard)**: BFCL (Berkeley Function Call Leaderboard) V3, including Base, Missing Parameters, Missing Functions, and Long Context scenarios.

**[ACEBench](https://github.com/chenchen0103/ACEBench)**: Testing across Normal, Special, and Agent scenarios.

[!NOTE] We have modified the evaluation code for these benchmarks to support both non-thinking and thinking model variants.


## 💐 Acknowledgments
This repository is built upon **[LlamaFactory](https://github.com/hiyouga/LlamaFactory)**. We sincerely thank the authors for their wonderful work.


