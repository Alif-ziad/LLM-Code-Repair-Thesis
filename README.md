# Confidence-Guided Adaptive Repair for Reliable LLM-Based Code Debugging

This is the overview page for my undergraduate thesis in Computer Science and Engineering at AIUB. It has no code of its own. It states the question, the setup and the current status, and links the repositories that hold the experiment files.

The thesis is in progress. No final results are reported here.

## Question

When a language model suggests a fix for buggy Python code, can a calibrated confidence score decide whether the system should accept the fix, retry, add more context or abstain?

## Setup

- Benchmark: 25,097 buggy/fixed Python code pairs from several sources, split into 20,077 training, 2,510 validation and 2,510 test rows.
- Models: 13 open models from six families (Qwen, Gemma, Phi, DeepSeek, Llama and StarCoder2).
- Training: QLoRA fine-tuning, one run per model.
- Retrieval: FAISS, used for retrieval-augmented repair.
- Evaluation: a hidden-test evaluation that runs every generated fix.

## Status

| Work package | Status |
|---|---|
| Multi-source dataset construction and current resplit | Completed |
| Model-specific QLoRA training and baseline evaluation | Completed foundation |
| Historical and unified retrieval-augmented diagnostics | Completed foundation |
| Hidden behavioral evaluation infrastructure | Implemented and validated |
| Confidence-data collection and labeling | In progress |
| Confidence calibration | Provisional, in progress |
| Adaptive threshold tuning and controller comparison | Not yet completed |
| Final statistical analysis and thesis write-up | Remaining |

## Experiment repositories

Only some of the experiments are published. The runs for the DeepSeek and StarCoder2 families are not.

| Repository | Model | What it holds |
|---|---|---|
| [Qwen2.5-Coder-3B-Instruct-QLoRA-RAG_Testing](https://github.com/Alif-ziad/Qwen2.5-Coder-3B-Instruct-QLoRA-RAG_Testing) | Qwen2.5-Coder-3B-Instruct | Row-level results for the 2,510 test rows, bug-type analysis, packaged QLoRA artifacts |
| [Qwen2.5_Coder1.5B_Instruct_QLORA-RAG_testing](https://github.com/Alif-ziad/Qwen2.5_Coder1.5B_Instruct_QLORA-RAG_testing) | Qwen2.5-Coder-1.5B-Instruct | RAG evaluation results (2,510 / 2,510 rows) |
| [Qwen2.5_1.5B](https://github.com/Alif-ziad/Qwen2.5_1.5B) | Qwen2.5-Coder-1.5B-Instruct | LoRA adapter (rank 16) and training checkpoints |
| [Gemma-4-E2B-it-QLoRA-RAG_testing](https://github.com/Alif-ziad/Gemma-4-E2B-it-QLoRA-RAG_testing) | Gemma 4 E2B IT | QLoRA + RAG results (2,510 / 2,510 rows) |
| [Gemma4_E2B_trained_model_eval_results](https://github.com/Alif-ziad/Gemma4_E2B_trained_model_eval_results) | Gemma 4 E2B | Validation results CSV |
| [Phi4_mini_3.8B_QLoRA-RAG](https://github.com/Alif-ziad/Phi4_mini_3.8B_QLoRA-RAG) | Phi-4-mini | Adapter, checkpoints and a partial test-result CSV |
| [LLAMA-3.2-3B-INSTRUCT_QLORA_Testing](https://github.com/Alif-ziad/LLAMA-3.2-3B-INSTRUCT_QLORA_Testing) | Llama-3.2-3B-Instruct | Generated fixes for 2,510 / 2,510 rows and per-bug-type metrics |
| [Calidebug_Hybrid_Dataset](https://github.com/Alif-ziad/Calidebug_Hybrid_Dataset) | None | Placeholder for the dataset. The data files are not published yet. |

## Read these before citing any number

- The experiment repositories are archives of outputs. The training and evaluation notebooks are not published, so the runs cannot be reproduced from these repositories alone.
- Some retrieval experiments use gold-reference gating to decide whether retrieval produced a rescue. Those are diagnostic upper bounds, not performance a deployed system would reach.
- Files named like `..._partial_*samples.csv` or `..._checkpoint_*.csv` are progress snapshots, not separate final evaluations.
- The Phi-4-mini test results are partial.
- The dataset is not yet public.

## Author

MD Alif Ziad Sarkar, final-year BSc in Computer Science and Engineering, American International University-Bangladesh (AIUB).
[LinkedIn](https://www.linkedin.com/in/alif-ziad) · [Portfolio](https://sites.google.com/view/alifziad/home)
