# Hugging Face

## Overview

**Hugging Face** is the central hub of the open-source AI and NLP ecosystem. It is simultaneously a model repository, a dataset library, a deployment platform, and a Python framework suite. Over 500,000 pre-trained models and 100,000 datasets are hosted on the Hub, covering NLP, computer vision, audio, tabular data, and multimodal tasks.

For data scientists, Hugging Face is most commonly the entry point to:
- downloading and using state-of-the-art pre-trained models in a few lines of code
- fine-tuning those models on custom datasets
- deploying models as hosted APIs or interactive demos

- **Made by:** Hugging Face Inc.
- **Type:** Open-source AI platform + Python library ecosystem
- **Website:** [huggingface.co](https://huggingface.co)
- **GitHub:** [github.com/huggingface](https://github.com/huggingface)
- **Pricing:** Free for public models and datasets; paid plans for private repos, hosted inference, and compute

---

## Core Libraries

Hugging Face is not a single tool — it is an ecosystem of libraries that work together:

| Library | Purpose |
|---|---|
| `transformers` | Load, fine-tune, and run pre-trained models for NLP, vision, audio, and multimodal tasks |
| `datasets` | Load, stream, and preprocess datasets from the Hub or local files |
| `evaluate` | Compute standard ML metrics (accuracy, F1, BLEU, ROUGE, etc.) |
| `tokenizers` | Fast, Rust-backed tokenizers for text preprocessing |
| `accelerate` | Simplify training across CPUs, GPUs, and TPUs with minimal code changes |
| `peft` | Parameter-Efficient Fine-Tuning — LoRA, QLoRA, prompt tuning for large models |
| `trl` | Reinforcement Learning from Human Feedback (RLHF), SFT, DPO for LLM alignment |
| `diffusers` | State-of-the-art image generation pipelines (Stable Diffusion, FLUX, etc.) |
| `timm` | Pre-trained computer vision models (ViT, ResNet, EfficientNet, etc.) |
| `sentence-transformers` | Generate sentence embeddings for semantic search, clustering, RAG |
| `gradio` | Build and share interactive ML demos and web apps |

---

## Capabilities

### 1. Model Hub
A public registry of 500,000+ pre-trained models across every modality and task. Models can be loaded in one line using the `transformers` library. Supports filtering by task, language, library, and licence.

```python
from transformers import pipeline
classifier = pipeline("sentiment-analysis")
classifier("Hugging Face is amazing!")
# [{'label': 'POSITIVE', 'score': 0.9998}]
```

### 2. The `pipeline` API
The highest-level abstraction in `transformers`. Load a model for a specific task and run inference without touching model architecture or tokenization details. Supported tasks include:

| Task | Pipeline name |
|---|---|
| Text classification / sentiment | `text-classification` |
| Named entity recognition | `ner` |
| Question answering | `question-answering` |
| Text generation | `text-generation` |
| Summarization | `summarization` |
| Translation | `translation` |
| Zero-shot classification | `zero-shot-classification` |
| Image classification | `image-classification` |
| Object detection | `object-detection` |
| Audio classification | `audio-classification` |
| Automatic speech recognition | `automatic-speech-recognition` |
| Image-to-text / captioning | `image-to-text` |

### 3. AutoClasses
When you don't want to hard-code a specific model class, `Auto` classes detect the right architecture from the model config and load it automatically:

```python
from transformers import AutoTokenizer, AutoModelForSequenceClassification

tokenizer = AutoTokenizer.from_pretrained("distilbert-base-uncased")
model = AutoModelForSequenceClassification.from_pretrained("distilbert-base-uncased", num_labels=6)
```

Common AutoClasses:

| AutoClass | Use |
|---|---|
| `AutoTokenizer` | Tokenizer matching any model |
| `AutoModel` | Base model (no task head) |
| `AutoModelForSequenceClassification` | Text classification |
| `AutoModelForTokenClassification` | NER, POS tagging |
| `AutoModelForQuestionAnswering` | Extractive QA |
| `AutoModelForCausalLM` | Generative language models (GPT-style) |
| `AutoModelForSeq2SeqLM` | Encoder-decoder models (T5, BART) |
| `AutoModelForImageClassification` | Vision classifiers |

### 4. Fine-Tuning with the `Trainer` API
The `Trainer` class handles the full training loop — gradient accumulation, evaluation, checkpointing, mixed precision, distributed training — with a simple configuration object (`TrainingArguments`):

```python
from transformers import TrainingArguments, Trainer

training_args = TrainingArguments(
    output_dir="./results",
    num_train_epochs=3,
    per_device_train_batch_size=16,
    eval_strategy="epoch",
    learning_rate=2e-5,
    weight_decay=0.01,
)

trainer = Trainer(
    model=model,
    args=training_args,
    train_dataset=tokenized_train,
    eval_dataset=tokenized_val,
    compute_metrics=compute_metrics,
    data_collator=data_collator,
)

trainer.train()
```

### 5. Dataset Loading with `datasets`
Load any dataset from the Hub — or from local CSV/JSON/Parquet files — with a unified API. Supports streaming for datasets too large to fit in memory:

```python
from datasets import load_dataset

# From Hub
dataset = load_dataset("emotion")

# From local CSV
dataset = load_dataset("csv", data_files="my_data.csv")

# Streaming (no download)
dataset = load_dataset("wikipedia", "20220301.en", streaming=True)
```

### 6. Metrics with `evaluate`
```python
import evaluate

accuracy = evaluate.load("accuracy")
f1 = evaluate.load("f1")

def compute_metrics(eval_pred):
    predictions, labels = eval_pred
    predictions = np.argmax(predictions, axis=1)
    return {
        "accuracy": accuracy.compute(predictions=predictions, references=labels)["accuracy"],
        "f1": f1.compute(predictions=predictions, references=labels, average="weighted")["f1"]
    }
```

### 7. Parameter-Efficient Fine-Tuning (PEFT)
Fine-tune large models (7B, 13B, 70B+ parameters) on consumer hardware by only updating a small fraction of parameters using LoRA or QLoRA:

```python
from peft import get_peft_model, LoraConfig, TaskType

peft_config = LoraConfig(
    task_type=TaskType.SEQ_CLS,
    r=8,
    lora_alpha=32,
    lora_dropout=0.1,
)
model = get_peft_model(model, peft_config)
model.print_trainable_parameters()
# trainable params: 294,912 || all params: 66,955,530 || trainable%: 0.44%
```

### 8. Hugging Face Hub — Push & Share Models
Save and upload fine-tuned models directly to the Hub for reuse or sharing:

```python
trainer.push_to_hub("my-username/my-distilbert-emotion-classifier")
```

### 9. Spaces — Deploy Interactive Demos
Hugging Face Spaces lets you deploy `gradio` or `streamlit` apps for free. A Gradio demo for a classifier takes ~10 lines:

```python
import gradio as gr
from transformers import pipeline

classifier = pipeline("text-classification", model="my-username/my-model")

def predict(text):
    return classifier(text)[0]

gr.Interface(fn=predict, inputs="text", outputs="label").launch()
```

### 10. Inference API
Every public model on the Hub has a hosted Inference API endpoint — no GPU or deployment required. Query it with a simple HTTP request or the `huggingface_hub` client.

---

## Use Cases

### 1. Sentiment Analysis & Text Classification
Fine-tune BERT, DistilBERT, or RoBERTa on labelled text data for tasks like product review classification, customer support ticket routing, or social media monitoring.

### 2. Named Entity Recognition (NER)
Extract entities (people, organisations, locations, dates) from unstructured text using pre-trained NER models or fine-tuned ones on domain-specific data.

### 3. Semantic Search & RAG
Use `sentence-transformers` to generate dense embeddings and build semantic search, document retrieval, or Retrieval-Augmented Generation (RAG) pipelines over private knowledge bases.

### 4. Summarization & Translation
Run state-of-the-art abstractive summarization (BART, Pegasus, T5) or translation (Helsinki-NLP, NLLB) on long-form documents — reports, articles, legal text — in one pipeline call.

### 5. Zero-Shot Classification
Classify text into any set of categories without labelled training data:

```python
classifier = pipeline("zero-shot-classification")
classifier(
    "The quarterly earnings exceeded analyst expectations.",
    candidate_labels=["finance", "sports", "politics", "technology"]
)
# {'labels': ['finance', ...], 'scores': [0.97, ...]}
```

### 6. Computer Vision
Load vision models for image classification, object detection, image segmentation, or visual question answering using the same `AutoModel` and `pipeline` pattern.

### 7. Audio & Speech
Transcribe audio with `whisper-large-v3`, classify sound events, or run speaker diarization — all through the `pipeline` API.

### 8. Emotion Classification via Fine-Tuning *(this repo's example)*

Fine-tuned **DistilBERT** (`distilbert-base-uncased`) on the **`emotion` dataset** (16,000 train / 2,000 val / 2,000 test) from the Hugging Face Hub to classify text into 6 emotions: sadness, joy, love, anger, fear, and surprise.

**Full pipeline:**

| Step | Detail |
|---|---|
| **Dataset** | `load_dataset("emotion")` — Twitter messages, 6-class emotion labels |
| **Tokenizer** | `AutoTokenizer` — padding + truncation to 128 tokens |
| **Model** | `AutoModelForSequenceClassification` — DistilBERT with 6-label classification head |
| **Collator** | `DataCollatorWithPadding` — dynamic padding per batch |
| **Training** | 2 epochs, batch 32, lr 2e-5, weight decay 0.01 — training loss: **0.396** |
| **Metrics** | Accuracy + Weighted F1 evaluated after each epoch |
| **Inference** | `pipeline("text-classification")` with `id2label` mapping |

**Sample predictions:**

| Input | Predicted Emotion | Confidence |
|---|---|---|
| "I cannot believe I finally finished this project!" | joy | 0.88 |
| "I'm so worried about the interview tomorrow." | fear | 0.89 |
| "I'm so frustrated I can't find my keys anywhere!" | anger | 0.98 |
| "I can't find the key" *(ambiguous)* | joy | 0.42 ← low confidence |

**Key finding:** The model performs strongly on emotionally expressive text (tweets) but produces low-confidence, unreliable predictions on neutral or ambiguous inputs — expected, as it was trained on expressive social media text. A production version would apply a confidence threshold or add a "neutral" class.

> See [`examples/HF_SentimentAnalysisModel.ipynb`](./examples/HF_SentimentAnalysisModel.ipynb) for the full notebook with training outputs.

---

## When to Use Hugging Face vs Other Tools

| Scenario | Recommendation |
|---|---|
| Need a pre-trained NLP model fast | `pipeline` API — done in 3 lines |
| Fine-tuning on custom labelled data | `Trainer` + `AutoModel` |
| Large model, limited GPU | `peft` with LoRA/QLoRA |
| Building a shareable demo | Hugging Face Spaces + Gradio |
| Need embeddings for search/RAG | `sentence-transformers` |
| Working with images or audio | `timm`, `diffusers`, or `pipeline` with vision/audio tasks |
| No-code AI analysis | Use Julius AI or Hex instead |

---

## Pricing

| Plan | Price | Key Details |
|---|---|---|
| Free | $0 | Unlimited public models/datasets, community Spaces, Inference API (rate-limited) |
| Pro | $9/month | Private repos, ZeroGPU Spaces, higher Inference API limits |
| Enterprise Hub | From $20/user/month | SSO, audit logs, private deployments, SLA |
| Inference Endpoints | Pay-per-use | Dedicated GPU endpoints for production inference |

---

## Links

- Hub: [huggingface.co](https://huggingface.co)
- Documentation: [huggingface.co/docs](https://huggingface.co/docs)
- `transformers` GitHub: [github.com/huggingface/transformers](https://github.com/huggingface/transformers)
- `datasets` GitHub: [github.com/huggingface/datasets](https://github.com/huggingface/datasets)
- `peft` GitHub: [github.com/huggingface/peft](https://github.com/huggingface/peft)
- Course (free): [huggingface.co/learn/nlp-course](https://huggingface.co/learn/nlp-course/chapter1/1)
- Papers With Code integration: [paperswithcode.com](https://paperswithcode.com)
