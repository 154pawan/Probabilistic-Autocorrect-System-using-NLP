# Probabilistic Autocorrect System using NLP

In this project, I've implemented a probabilistic autocorrect system from scratch using Python and the Natural Language Toolkit (NLTK). My model takes a misspelled word as input and suggests the most likely correct spellings based on word probabilities I calculate from a text corpus.

## 📝 Overview

The core of this autocorrect tool is built upon the principles of **edit distance** and **word frequency**. By analyzing a large text file, my program builds a vocabulary and calculates the probability of each word's occurrence. When a user enters a word, I generate a set of candidate corrections that are a small "edit distance" away from the original word. I then rank these candidates by their pre-calculated probabilities to find the most likely correct spelling.

## ✨ Features

  - **Corpus-Based Learning:** I built the system to learn its vocabulary and word probabilities from any user-provided text file (`.txt`).
  - **Edit Distance Algorithm:** I generate potential corrections by performing four types of single-character edits:
      - **Deletes:** Removing one letter (e.g., `athem` -\> `them`).
      - **Swaps:** Swapping adjacent letters (e.g., `athem` -\> `tahem`).
      - **Replaces:** Replacing one letter with another (e.g., `athem` -\> `athen`).
      - **Inserts:** Adding one letter (e.g., `athem` -\> `anthem`).
  - **Two-Level Edit Distance:** If no valid words are found at an edit distance of 1, I expand the search to an edit distance of 2 for a wider range of suggestions.
  - **Probabilistic Ranking:** I sort all suggestions based on their frequency in the source corpus, ensuring the most common and contextually likely words are suggested first.
  - **Customizable Suggestions:** I made it easy to change the number of top suggestions to be displayed.

## 🛠️ How It Works

My autocorrect process follows these logical steps:

1.  **Data Loading & Preprocessing:** First, I read a large text corpus, convert it to lowercase, and tokenize it into a list of words to build a vocabulary set.
2.  **Frequency and Probability Calculation:** Next, I count the occurrences of each word to create a frequency map. From this, I calculate the probability $P(w)$ of each word $w$ appearing in the text.
    $$P(w) = \frac{\text{count}(w)}{\text{Total number of words}}$$
3.  **Candidate Generation:** When a user inputs a misspelled word, my system generates all possible words that are one or two edits away.
4.  **Filtering and Ranking:** I filter the generated candidates against the vocabulary to keep only real, known words. These valid words are then ranked by their probability, and the top suggestions are presented to the user.

## 🚀 Getting Started

### Prerequisites

  - Python 3.x
  - Jupyter Notebook or Google Colab
  - NLTK library

### Installation

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/your-username/your-repository-name.git
    cd your-repository-name
    ```
2.  **Install the required Python library:**
    ```bash
    pip install nltk
    ```
3.  **Prepare your dataset:**
      - You will need a large text file to serve as your corpus. You can use any `.txt` file (e.g., a book from Project Gutenberg or a collection of articles).
      - Name your file `final.txt` or update the filename in the notebook.

### Usage

1.  Open my `AutoCorrect.ipynb` notebook in Jupyter or Google Colab.
2.  Run the cells in sequential order.
3.  When prompted, upload your `final.txt` corpus file.
4.  In the final cell, enter a word you want to correct at the prompt. The program will output the top suggestions.

#### Example

```
Enter a word for autocorrection: athem

Top suggestions:
them
athe
athes
```

## 💡 Future Improvements

  - **Context-Aware Corrections:** I plan to implement n-gram models (bigrams or trigrams) to suggest corrections that fit the context of a full sentence.
  - **Performance Optimization:** I want to use more efficient data structures to speed up the generation of candidate words, especially for the second-level edits.
  - **Advanced Edit Models:** I'm considering incorporating a phonetic algorithm (like Soundex) to catch mistakes that sound similar but are spelled differently.
