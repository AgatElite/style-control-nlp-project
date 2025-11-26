# CTRL + Style: An Analysis of Literary Representation and Style Transfer

[](https://www.python.org/downloads/release/python-390/) [](https://opensource.org/licenses/MIT)

## Abstract

The ability to understand and replicate nuanced human expression is a key challenge for large language models. This project explores the intersection of natural language processing and literary analysis by investigating how modern transformer models internally represent the distinct authorial voices of Fyodor Dostoevsky and Charles Dickens. By examining the vector space representations of their works and attempting controlled style transfer, we aim to shed light on both the capabilities and the inherent biases of these models when confronted with the subtleties of literary art.

-----

## Relevant Files

```
.
├── CTRL_Style_Analysis.ipynb     # The main Jupyter/Colab notebook with all code.
├── Project-Paper.pdf             # The final 6-page research paper.
├── Presentation.md               # The source file for the final presentation.
└── README.md                     # You are here.
```

-----

## Running the Notebook

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/AgatElite/style-control-nlp-project/blob/main/Style%2BControl.ipynb)

  * **To Run from Scratch**: Execute the cells sequentially. Note that **Cell 2 (Data Acquisition)** and **Cell 3 (Embedding Generation)** are time-consuming and only need to be run once.
  * **Recommended Quick Start**:
    1.  Run Cells 2 and 3 once to generate `final_corpus.csv` and `stylistic_embeddings.npz`.
    2.  Run Cell 4 to save these artifacts to your Google Drive.
    3.  In future sessions, you can **start at Cell 5** to load the pre-processed data and embeddings directly from your Drive, skipping the long initial steps.
