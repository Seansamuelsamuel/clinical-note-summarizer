# Clinical Note Summarizer using FLAN‑T5

This project focuses on summarizing medical conversations between doctors and patients into short, readable clinical notes. The goal was to automate the note-taking process using natural language processing, with a fine-tuned FLAN‑T5 model.

The code was written and tested locally in Python using the MTS-Dialog dataset. The data files were used as-is from the original source.



## 📁 Dataset Used

I used the **MTS-Dialog** dataset, which contains real doctor–patient conversations paired with human-written summaries. The dataset is split across several CSV files (main set + augmented variations).

> 🔒 The dataset is provided under the **CC BY 4.0 license**, which allows reuse with credit. All usage here complies with that license.



## 🧠 Model Used

- `google/flan-t5-small` from Hugging Face Transformers
- Fine-tuned using my local dataset
- Preprocessing done using Hugging Face `datasets` + `tokenizers`
- Evaluated using ROUGE score



## 🛠 How I Built It

1. Loaded and explored the CSV files from the dataset
2. Standardized column names to `"dialogue"` and `"summary"`
3. Preprocessed text with prompt formatting (`summarize: ...`)
4. Tokenized everything using FLAN‑T5's tokenizer
5. Trained using Hugging Face `Trainer` API
6. Evaluated using `evaluate` library (ROUGE)
7. Finally, tested on my own custom input



## 🧪 Sample Inference


Input:
Doctor: Are you experiencing any chest pain?
Patient: Yes, especially when I take deep breaths.

Output:
Patient reports chest pain when breathing deeply.




## 📊 ROUGE Evaluation (on test set)

- ROUGE-1: ~0.45  
- ROUGE-L: ~0.41  

(Scores vary slightly depending on the sample and training seed.)

---

## 📸 Screenshots

Screenshots of the training output, ROUGE results, and an example inference are included in the `screenshots/` folder.

---

**Evaluation and ROUGE**

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

**REQUIREMENTS AND HOW TO RUN**
Hi, this is just a small note on how to run the project and what things you need. I’ve tried to keep it simple.


1. WHAT YOU NEED INSTALLED

You’ll need a few Python packages to make the code run properly. These are the ones I used:

  - transformers
  - datasets
  - evaluate
  - torch
  - pandas
  - numpy
  - scikit-learn

To install all of them in one go, just run this:

pip install transformers datasets evaluate torch pandas numpy scikit-learn

I ran everything in Jupyter Notebook, but you can also use VS Code or Colab if you want.



2. WHAT FILES ARE IN THIS PROJECT

Here’s what you’ll see in the main folder:

  * clinical_summary_generator.ipynb  (this is the main notebook I used)
  * dataset/  (this folder has all the CSV files from the MTS Dialog dataset)
  * screenshots/  (has the sample output and ROUGE score pics)
  * README.md  (short overview of the project)
  * requirements_run.txt  (this file)



3. HOW TO RUN THE PROJECT

Once you’ve downloaded everything and you’re inside the folder:

  1. Open the notebook:

     jupyter notebook clinical_summary_generator.ipynb

  2. Run each cell one by one. First the data loads, then the model, then it trains and finally shows some example summaries and ROUGE scores.



NOTE:

The data is already in CSV format and doesn’t need to be merged or cleaned or anything. It’s ready to use. The model is FLAN-T5-small so it should work fine on most machines.

Hope this helps :)



