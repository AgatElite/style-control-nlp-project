<!-- slide bg="[[dickvsdosto.png]]" data-background-opacity="0.3" -->
# CTRL + Style

## An Analysis of Literary Representation and Style Transfer in Transformer Models

**Alex Tulip**

Natural Language Processing

Prof. Alfio Ferrara

---

## The Challenge of "Style"

What is literary style? It's more than just words. It's an author's unique voice.<!-- element class="fragment" -->

It's intuitive for us to tell the difference between the psychological intensity of Dostoevsky and the descriptive social commentary of Dickens.<!-- element class="fragment" -->

But how does a machine perceive this? Can a model truly learn to understand something as abstract as style?<!-- element class="fragment" -->

note:

Start with the big picture. Why is this an interesting problem? This sets the stage for your research question.

---

## Research Question

This project investigates a specific question:

> How do transformer models internally represent the stylistic differences between Dostoevsky and Dickens, and can we manipulate these representations for controlled text style transfer?

<!-- element class="fragment" -->

note:

State your goal clearly and concisely. This is taken directly from your project paper and frames the entire presentation.

---

## Methodology: A Three-Step Approach

My process was divided into three main phases:

::: block
1. **Data Curation:**
	- Build a high-quality, clean dataset of the authors' works.
:::<!-- element class="fragment" -->
::: block
2. **Text Embedding:**
	- Use a pre-trained RoBERTa model to convert text into numerical vectors, or 'embeddings'.
:::<!-- element class="fragment" -->
::: block
3. **Analysis & Style Transfer:**
	- Analyze the embeddings for stylistic separation and then attempt to rewrite text from one style to another.
:::<!-- element class="fragment" -->

note:

Give a high-level overview of your process before diving into the details. This acts as a roadmap for the audience.

---

## Step 1: Building a Clean Corpus

The foundation of my project is a clean dataset, sourced directly from Project Gutenberg.<!-- element class="fragment" -->
::: block
- **Fyodor Dostoevsky:** *Crime and Punishment*, *The Brothers Karamazov*.
- **Charles Dickens:** *A Tale of Two Cities*, *Great Expectations*, *Oliver Twist*.
:::<!-- element class="fragment" -->
A rigorous cleaning pipeline was essential to remove non-authorial content like publisher's notes, prefaces, and tables of contents.<!-- element class="fragment" -->

note:

Explain where your data came from and why the cleaning was important. This shows you've been meticulous from the start.

---

## Step 2: From Words to Vectors
::: block
To make style 'visible' to a machine, we use **embedding**.
:::<!-- element class="fragment" -->

::: block
-  I fed the cleaned texts, paragraph by paragraph, into a **RoBERTa-base** model.
:::<!-- element class="fragment" -->
::: block
- The model converts each paragraph into a 768-dimensional vector.
:::<!-- element class="fragment" -->
::: block
- **Our Hypothesis:** The vectors for Dostoevsky's paragraphs will be mathematically different from the vectors for Dickens's paragraphs.
:::<!-- element class="fragment" -->

note:

Explain the embedding process in simple terms. The key is to convey the idea of converting text into a format a machine can understand.

---

## Results Part 1: Representation

### Do the Styles Form Distinct Clusters?

First, I visualized the embeddings using t-SNE to see if the styles were separable.<!-- element class="fragment" -->

![[t-SNE Visualisation.png|500]]<!-- element class="fragment" -->

The plot shows significant overlap between the two representations, but distinct clusters are evident, providing some visual evidence that the model has learned to separate the styles.<!-- element class="fragment" -->

note:

This is your first results slide. Start with the visual evidence. Explain what the plot shows and what it means. The light background helps the plot stand out.

---

## Results Part 1: Quantification

::: block

To move beyond visual intuition, I quantified this separation with a classifier. The model achieved an overall **accuracy of 92%**, proving that a clear mathematical boundary exists between the styles.

:::<!-- element class="fragment" -->

::: block

**Classification Report**

|                   | precision | recall | f1-score |
|:---------------- |:-------: |:----: |:------: |
| Dostoevsky &nbsp; |   0.93    |  0.91  |   0.92   |
| Dickens           |   0.92    |  0.94  |   0.93   |

:::<!-- element class="fragment" -->

--

**Confusion Matrix**

![[Confusion Matrix.png]]

note:

This slide now shows both the summary statistics and the visual breakdown of the classifier's performance. You can point out the high numbers on the diagonal of the matrix to show correct predictions.

---

## Results Part 1: Interpretation

*How* does the model separate the two stlyles?
::: block
I used Concept Activation Vectors (CAV) to test for alignment with literary themes.
:::<!-- element class="fragment" -->

![[CTAV Scores.png|600]]

<!-- element class="fragment" -->

The results show a clear divergence: Dostoevsky's texts align with "Psychological Focus," while Dickens's texts align with "Social Commentary." This suggests the model's separation is not arbitrary but is linked to the core themes of each author.<!-- element class="fragment" -->

note:

This slide answers the "why". It shows you're not just reporting numbers but interpreting what they mean in a literary context.

---

## Results Part 2: Style Transfer

::: block

The second part of my research was on style manipulation. Is it possible to rewrite a piece of text from one author in the style of the other?

I used a **prompt-engineered LLM** (`gemini-2.5-flash`) to perform the transfer.

:::<!-- element class="fragment" -->

--

**Example: Dostoevsky to Dickens**

::: block

- **Original (Dostoevsky):**

	> "what do you want?" asked raskolnikov, numb with terror. the man was still silent, But suddenly he bowed down almost to the ground, touching it with his finger.
:::<!-- element class="fragment" -->

::: block

- **Stylized (Dickens):**

	> "What is it you desire, pray?" demanded Raskolnikov, his very sinews turned to ice, his spirit quite benumbed by a terror that clawed at his very soul…
:::<!-- element class="fragment" -->

note:

Transition to the second part of your project. The qualitative example is powerful because it's a very clear and intuitive demonstration of a successful transfer. You don't need to read the whole stylized text, just point out a key difference.

---

## Results Part 2: Quantitative Evaluation

I then evaluated this process quantitatively on 50 samples.<!-- element class="fragment" -->

|                           | Style Accuracy | self-BLEU | Perplexity |
| ------------------------- |:------------: |:-------: |:--------: |
| **Dostoevsky to Dickens** |    **0.84**    |   0.069   |   45.72    |
| **Dickens to Dostoevsky** |    **0.20**    |   0.066   |   70.79    |

<!-- element class="fragment" -->

The table reveals a fascinating asymmetry…<!-- element class="fragment" -->

note:

Present the final quantitative results. This slide sets up your main discussion point. Don't interpret it fully here; just point out the asymmetry and lead into the next slide.

--

## Discussion: The Key Finding

The results show it is much harder for the LLM to imitate Dostoevsky (20% accuracy) than Dickens (84% accuracy).<!-- element class="fragment" -->

Why?<!-- element class="fragment" -->

::: block

- **Imitating Dickens is an *Additive* Task:** It involves adding descriptive words and clauses, which aligns with an LLM's natural tendency to be verbose.
:::<!-- element class="fragment" -->
::: block
- **Imitating Dostoevsky is a *Constrictive* Task:** It requires adopting a stark, minimalist, and psychologically tense prose, which forces the model to go against its default behavior.
  :::<!-- element class="fragment" -->

This asymmetry is the most significant finding that emerged from my experiments.<!-- element class="fragment" -->

note:
This is your most important analytical slide. Clearly explain the "why" behind the numbers. The additive vs. constrictive framework is a strong, clear way to frame your discovery.

---

## Conclusion

1)  We **successfully demonstrated** that a transformer's embeddings can represent and separate literary styles with high accuracy (92%).
2)  We **successfully performed style transfer**, but discovered a key limitation: the model excels at additive style changes but struggles with constrictive ones.

note:
Summarize your key achievements and briefly mention future directions. This shows you're thinking beyond the current project. End on a strong, confident note.