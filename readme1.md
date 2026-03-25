# IIT Jodhpur Word Embedding Project
**Course:** CSL 7640: Natural Language Understanding  
**Assignment:** 2, Problem 1  

This project implements a complete pipeline for domain-specific NLP: from crawling institutional data to training custom Word2Vec embeddings (Skip-gram and CBOW) from scratch.

---

## 📂 Project Structure

- **`corpus_gen.py`**: An automated web scraper and document parser. It performs a depth-2 crawl of the IIT Jodhpur domain to build the training corpus.
- **`ques1.ipynb`**: A comprehensive PyTorch implementation of Word2Vec architectures, including training loops, hyperparameter grid searches, and evaluation metrics.
- **`corpus.txt`**: (Generated) The final cleaned and merged text dataset.
- **`corpus_stat.txt`**
- **`wordcloud.png`**

---

## 🛠️ Phase 1: Corpus Generation

The `corpus_gen.py` script is designed to collect textual data from official IIT Jodhpur sources, including departments, academic programs, and faculty pages.

### Prerequisites
```bash
pip install requests beautifulsoup4 pdfplumber python-docx
```
How to RunExecute the script:Bashpython corpus_gen.py

Behavior:Starts at depth 0 using seed URLs (History, Academics, etc.).Follows internal iitj.ac.in links up to depth 2.Downloads and extracts text from .pdf, .doc, and .docx files.Cleans, deduplicates, and saves the result to corpus.txt.

🧠 Phase 2: Model Training & EvaluationThe training logic is contained within the Jupyter Notebook, implemented using PyTorch.Architectures ImplementedSkip-gram with Negative Sampling (SGNS): Predicts context words given a center word. Uses a unigram distribution raised to $3/4$ power for noise sampling.Continuous Bag of Words (CBOW): Predicts a center word based on the aggregate (average) of its surrounding context vectors.

How to RunOpen ques1.ipynb in Google Colab or Jupyter Lab.Ensure corpus.txt is uploaded to the working directory.Run the Dataset Class cell to tokenize the text and build the vocabulary (minimum count = 2).Run the Experiment Runner: This will iterate through a grid search of:Dimensions: 50, 100, 300Context Windows: 2, 5, 10Negative Samples: 5, 10View the generated Loss Curves to monitor convergence.

📊 Evaluation & AnalysisIntrinsic EvaluationThe notebook includes a get_similarity function to perform cosine similarity searches. This allows you to verify if the model has captured institute-specific semantics:Python# Example: Finding words related to 'phd'
get_similarity(model_embeddings, word2idx, "phd", top_k=5)

