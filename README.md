# CTRL + Style: Disentangling Literary Style from Semantic Content in Vector Space

[](https://www.python.org/downloads/release/python-390/) [](https://opensource.org/licenses/MIT)

## Abstract

This study investigates how literary style is encoded in the vector space of Large
Language Models (LLMs). I specifically look at whether I can separate the dis-
tinct writing styles of Jane Austen and Herman Melville. Using a dataset of
non-parallel texts and the BGE embedding model, I show that authors form dis-
tinct clusters in high-dimensional space (99% classification accuracy). However, I
find that ”style” is not a single point but a broad cloud. I also performed a style
transfer experiment using Gemini-2.5-Flash. My results show a conflict between
content and style: the final semantic layers of the model focus on the original
content and fail to detect the style change. In contrast, the lower layers (Layer
2) successfully identify the new style. This suggests that literary style is encoded
in the early structural layers of the model, separate from the high-level meaning
found in later layers.

-----

## Relevant Files

```
.
├── CTRL_Style_Analysis.ipynb     # Colab notebook with all code.
├── Paper.pdf                     # The final research paper.
└── README.md                     # You are here.
```

-----

## Running the Notebook

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/AgatElite/style-control-nlp-project/blob/main/Style%2BControl.ipynb)

