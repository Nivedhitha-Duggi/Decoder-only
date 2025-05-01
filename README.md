# Distractor Ranking with Decoder-Only Language Models

This repository contains code, training configurations, and evaluation results for ranking distractors in multiple-choice questions (MCQs) using **decoder-only transformer models**: GPT-Neo, DistillGPT2, and TinyGPT2. The goal is to analyze how different fine-tuned variants rank incorrect choices based on model confidence (logits).

---

##  Models Used

| Model Name    | Variants                              | Base Model               |
|---------------|----------------------------------------|---------------------------|
| GPT-Neo 125M  | `neo_model1`, `neo_model2`, `neo_model3` | EleutherAI/gpt-neo-125M  |
| DistillGPT2   | `distill-low`, `distill-medium`, `distill-high` | distilgpt2         |
| TinyGPT2      | `tiny-low`, `tiny-medium`, `tiny-high` | sshleifer/tiny-gpt2      |

---

##  Training Setup

Each variant is trained using different configurations of:
- **Batch size**
- **Learning rate**
- **Epochs**
- **Gradient accumulation steps**

These configurations represent three training regimes:
- **Low** – Conservative, stable learning
- **Medium** – Balanced and efficient learning
- **High** – Aggressive learning with faster convergence

Training is performed on a dataset of MCQs formatted in MMLU style:
- `question`
- `option_0` to `option_3`
- `correct_answer` (index of correct choice)

---

##  Evaluation

Evaluation is conducted using `human_ranked.csv` which contains human-annotated distractor rankings.

For each question:
- A prompt is generated with all choices
- The model outputs logits for options A–D
- The predicted choice is the option with the highest logit

**Output columns in predictions:**
- `question`, `option_0`–`option_3`
- `predicted_choice`
- `correct_choice_index`
- `logit_A`, `logit_B`, `logit_C`, `logit_D`
- `variant`, `model_name`

---

##  How to Run

1. Clone this repo and open in Colab or Jupyter Notebook.
2. Upload your `training_data.csv` and `human_ranked.csv`.
3. Run the corresponding notebook (`GPT_Neo_125M.ipynb`, `distillgpt.ipynb`, or `tinygpt.ipynb`).
4. Fine-tuned models and predictions will be saved automatically.

---

##  Contact

Feel free to connect or reach out for questions or collaborations.



