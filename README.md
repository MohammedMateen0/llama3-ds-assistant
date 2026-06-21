# Fine-Tuning Llama 3.2 1B with QLoRA

## Overview

This project demonstrates parameter-efficient fine-tuning of a Large Language Model using QLoRA and Unsloth. A Llama 3.2 1B Instruct model was fine-tuned on a custom Data Science and AI instruction dataset containing 345 question-answer pairs.

The objective was to adapt the model to answer Machine Learning, Deep Learning, NLP, Transformers, LoRA, QLoRA, Prompt Engineering, and LLM Evaluation questions more accurately than the base model.

This project was completed as the Week 13 Saturday Project in the LLM Engineering learning roadmap.

---

## Project Objectives

* Understand LLM fine-tuning workflows
* Apply QLoRA for memory-efficient training
* Fine-tune a real LLM on a custom dataset
* Evaluate model behavior before and after training
* Publish the trained adapter on Hugging Face

---

## Model Information

Base Model:

* Llama 3.2 1B Instruct

Fine-Tuning Method:

* QLoRA
* LoRA Rank = 16
* 4-bit Quantization (NF4)

Frameworks:

* Unsloth
* Transformers
* PEFT
* TRL
* Datasets

Hardware:

* Google Colab Tesla T4 GPU

---

## Dataset

Dataset Type:

* Instruction Tuning Dataset

Dataset Size:

* 345 Instruction-Response Pairs

Topics Covered:

* Machine Learning
* Deep Learning
* Natural Language Processing
* Transformers
* Large Language Models
* LoRA
* QLoRA
* Prompt Engineering
* RLHF
* DPO
* Evaluation Metrics
* RAG Fundamentals

Example Entry:

```json
{
  "instruction": "What is LoRA?",
  "response": "LoRA is a parameter-efficient fine-tuning technique that freezes pretrained weights and learns low-rank adapters."
}
```

---

## Training Configuration

| Parameter             | Value       |
| --------------------- | ----------- |
| Epochs                | 3           |
| Batch Size            | 2           |
| Gradient Accumulation | 4           |
| Effective Batch Size  | 8           |
| Learning Rate         | 2e-4        |
| Optimizer             | AdamW 8-bit |
| LoRA Rank             | 16          |
| LoRA Alpha            | 16          |
| Quantization          | 4-bit NF4   |

---

## Training Results

Training Steps:

* 66

Trainable Parameters:

* 11,272,192

Total Parameters:

* 1,247,086,592

Percentage Trained:

* 0.90%

Training Loss:

| Stage   | Loss         |
| ------- | ------------ |
| Initial | ~1.24        |
| Final   | ~0.35 - 0.50 |

The model successfully learned domain-specific concepts while training less than 1% of the total parameters.

---

## Evaluation

### Before Fine-Tuning

Question:
What is LoRA?

Output:

```text
LoRaWAN is a wireless communication protocol...
```

Question:
What is QLoRA?

Output:

```text
QLoRA is a 3D scanning technology...
```

### After Fine-Tuning

Question:
What is LoRA?

Output:

```text
LoRA stands for Low-Rank Adaptation and is a parameter-efficient fine-tuning method.
```

Question:
What is QLoRA?

Output:

```text
QLoRA combines LoRA with quantization to reduce memory requirements during training.
```

The fine-tuned model demonstrated clear domain adaptation and significantly improved understanding of modern LLM engineering concepts.

---

## Model Files

```text
adapter_config.json
adapter_model.safetensors
tokenizer.json
tokenizer_config.json
chat_template.jinja
```

Adapter Size:

* 44 MB

Repository Size:

* ~60 MB

---

## Hugging Face Model

Model Repository:

https://huggingface.co/mateen-2003/llama3-ds-assistant

---

## Repository Structure

```text
.
├── data/
│   └── ds_qa.json
│
├── notebooks/
│   └── finetune_llama3.ipynb
│
├── outputs/
│   └── evaluation_results.txt
│
├── README.md
├── requirements.txt
└── .gitignore
```

---

## Key Learnings

* Large Language Models can be adapted efficiently using LoRA.
* QLoRA enables fine-tuning on consumer GPUs through 4-bit quantization.
* High-quality datasets are more important than large datasets.
* Domain adaptation can be achieved by training less than 1% of model parameters.
* Evaluation is essential to verify actual behavioral improvements.

---

## Future Improvements

* Increase dataset size with advanced reasoning examples.
* Add more RLHF and DPO examples.
* Train for additional epochs.
* Evaluate using automated benchmarks.
* Export GGUF format for local inference.

---

## Author

Mohammed Mateen

B.Tech Computer Science Engineering

Focused on Machine Learning, Deep Learning, LLM Engineering, and Retrieval-Augmented Generation (RAG) Systems.
