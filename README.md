Probabilistic Autocorrect System using NLP
This project implements a probabilistic autocorrect system from scratch using Python and the Natural Language Toolkit (NLTK). The model takes a misspelled word as input and suggests the most likely correct spellings based on word probabilities calculated from a text corpus.

📝 Overview
The core of this autocorrect tool is built upon the principles of edit distance and word frequency. By analyzing a large text file, the program builds a vocabulary and calculates the probability of each word's occurrence. When a user enters a word, the system generates a set of candidate corrections that are a small "edit distance" away from the original word. These candidates are then ranked by their pre-calculated probabilities to find the most likely correct spelling.

✨ Features
Corpus-Based Learning: Builds its vocabulary and word probabilities from a user-provided text file (.txt).

Edit Distance Algorithm: Generates potential corrections by performing four types of single-character edits:

Deletes: Removing one letter (e.g., athem -> them).

Swaps: Swapping adjacent letters (e.g., athem -> tahem).

Replaces: Replacing one letter with another (e.g., athem -> athen).

Inserts: Adding one letter (e.g., athem -> anthem).

Two-Level Edit Distance: If no valid words are found at an edit distance of 1, the search is expanded to an edit distance of 2 for a wider range of suggestions.

Probabilistic Ranking: Suggestions are sorted based on their frequency in the source corpus, ensuring the most common and contextually likely words are suggested first.

Customizable Suggestions: You can easily change the number of top suggestions to be displayed.

🛠️ How It Works
The autocorrect process follows these logical steps:

Data Loading & Preprocessing: The program first reads a large text corpus, converts it to lowercase, and tokenizes it into a list of words. This list is used to build a vocabulary set.

Frequency and Probability Calculation: It counts the occurrences of each word in the corpus to create a frequency map. From this, it calculates the probability P(w) of each word w appearing in the text.

P(w)= 
Total number of words
count(w)
​
 
Candidate Generation: When a user inputs a misspelled word, the system generates all possible words that are one or two edits away.

Filtering and Ranking: The generated candidates are filtered against the vocabulary to keep only the real, known words. These valid words are then ranked by their probability, and the top suggestions are presented to the user.

🚀 Getting Started
Prerequisites
Python 3.x

Jupyter Notebook or Google Colab

NLTK library

Installation
Clone the repository:

Bash

git clone https://github.com/your-username/your-repository-name.git
cd your-repository-name
Install the required Python library:

Bash

pip install nltk
Prepare your dataset:

You will need a large text file to serve as your corpus. You can use any .txt file (e.g., a book from Project Gutenberg or a collection of articles).

Name your file final.txt or update the filename in the notebook.

Usage
Open the AutoCorrect.ipynb notebook in Jupyter or Google Colab.

Run the cells in sequential order.

When prompted, upload your final.txt corpus file.

In the final cell, enter a word you want to correct at the prompt. The program will output the top suggestions.

Example
Enter a word for autocorrection: athem

Top suggestions:
them
athe
athes
💡 Future Improvements
Context-Aware Corrections: Implement n-gram models (bigrams or trigrams) to suggest corrections that fit the context of a full sentence.

Performance Optimization: Use more efficient data structures or algorithms to speed up the generation of candidate words, especially for the second-level edits.

Advanced Edit Models: Incorporate a phonetic algorithm (like Soundex) to catch mistakes that sound similar but are spelled differently.
