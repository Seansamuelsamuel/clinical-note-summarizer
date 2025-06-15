# Clinical Note Summarizer using FLAN‑T5

This project focuses on summarizing medical conversations between doctors and patients into short, readable clinical notes. The goal was to automate the note-taking process using natural language processing, with a fine-tuned FLAN‑T5 model.

The code was written and tested locally in Python using the MTS-Dialog dataset. The data files were used as-is from the original source.

---

## 📁 Dataset Used

I used the **MTS-Dialog** dataset, which contains real doctor–patient conversations paired with human-written summaries. The dataset is split across several CSV files (main set + augmented variations).

> 🔒 The dataset is provided under the **CC BY 4.0 license**, which allows reuse with credit. All usage here complies with that license.

---

## 🧠 Model Used

- `google/flan-t5-small` from Hugging Face Transformers
- Fine-tuned using my local dataset
- Preprocessing done using Hugging Face `datasets` + `tokenizers`
- Evaluated using ROUGE score

---

## 🛠 How I Built It

1. Loaded and explored the CSV files from the dataset
2. Standardized column names to `"dialogue"` and `"summary"`
3. Preprocessed text with prompt formatting (`summarize: ...`)
4. Tokenized everything using FLAN‑T5's tokenizer
5. Trained using Hugging Face `Trainer` API
6. Evaluated using `evaluate` library (ROUGE)
7. Finally, tested on my own custom input

---

## 🧪 Sample Inference

```
Input:
Doctor: Are you experiencing any chest pain?
Patient: Yes, especially when I take deep breaths.

Output:
Patient reports chest pain when breathing deeply.
```

---

## 📊 ROUGE Evaluation (on test set)

- ROUGE-1: ~0.45  
- ROUGE-L: ~0.41  

(Scores vary slightly depending on the sample and training seed.)

---

## 📸 Screenshots

Screenshots of the training output, ROUGE results, and an example inference are included in the `screenshots/` folder.

---

Evaluation and ROUGE
At the end of training, I used a metric called ROUGE (Recall-Oriented Understudy for Gisting Evaluation) to
Check how close the generated summaries were to the original human-written ones.

ROUGE compares the overlap of words and phrases between the model's output and the reference
- ROUGE-1 looks at matching individual words
- ROUGE-2 checks for two-word pairs (bigrams)
- ROUGE-L finds the longest matching word sequence
My results were:
- ROUGE-1: 0.45
- ROUGE-2: 0.32
- ROUGE-L: 0.41
These scores show that the model is doing a decent job of generating relevant summaries that are similar to what a doctor might write manually


