# POS Tagging using Hidden Markov Model (HMM) with Viterbi Algorithm

## Project Overview

This project implements Part-of-Speech (POS) tagging using Hidden Markov Models with the Viterbi algorithm for sequence decoding. The system processes input sentences and assigns grammatical tags to each word using statistical probabilities learned from the Brown Corpus.

## Team Members

- **Shruti Patel** (24M0825, CSE)
- **Kaustubh Shivshankar Shejole** (24M2109, CSE)  
- **Tushar Katakiya** (24M2110, CSE)
- **Kush Mangukiya** (24M0769, CSE)

**Course**: CS626 - Speech, Natural Language Processing, and the Web  
**Date**: September 7, 2024

## Problem Statement

Given a sequence of words, the system produces the corresponding POS tag sequence using HMM-Viterbi algorithm.

**Example:**
- **Input**: "The quick brown fox jumps over the lazy dog"
- **Output**: 
  ```
  The     -> DET
  quick   -> ADJ
  brown   -> ADJ
  fox     -> NOUN
  jumps   -> VERB
  over    -> ADP
  the     -> DET
  lazy    -> ADJ
  dog     -> NOUN
  ```

## Dataset and Tags

- **Dataset**: Brown Corpus
- **Tag Set**: Universal Tag Set (12 tags)
  - `ADJ` (Adjective)
  - `ADP` (Adposition) 
  - `ADV` (Adverb)
  - `CONJ` (Conjunction)
  - `DET` (Determiner)
  - `NOUN` (Noun)
  - `NUM` (Number)
  - `PRON` (Pronoun)
  - `PRT` (Particle)
  - `VERB` (Verb)
  - `.` (Punctuation)
  - `X` (Other)

## Features

### Data Preprocessing
- **Lowercasing**: Standardizes input text for consistency
- **Tokenization**: Splits input into individual tokens
- **Laplace Smoothing**: Handles unseen words by adding constant (1) to frequency counts

### Algorithm Implementation
- **HMM Training**: Learns transition and emission probabilities from Brown Corpus
- **Viterbi Decoding**: Uses dynamic programming to find most likely tag sequence
- **Unknown Word Handling**: Manages out-of-vocabulary words using smoothing techniques

### Evaluation
- **5-fold Cross Validation**: Ensures robust performance measurement
- **Comprehensive Metrics**: Precision, Recall, F1-score for each POS tag
- **Confusion Matrix Analysis**: Detailed error analysis and interpretation

## Performance Results

### Overall Performance
- **Precision**: 94.42%
- **Recall**: 94.33%
- **F1-Score**: 94.31%
- **F0.5-Score**: 94.34%
- **F2-Score**: 94.31%

### Per-Tag Performance
| Tag   | Precision | Recall | F1-Score |
|-------|-----------|--------|----------|
| DET   | 93.82%    | 98.69% | 96.19%   |
| NOUN  | 94.75%    | 92.07% | 93.39%   |
| ADJ   | 89.70%    | 89.18% | 89.44%   |
| VERB  | 96.90%    | 93.62% | 95.23%   |
| ADP   | 92.71%    | 96.92% | 94.77%   |
| .     | 96.59%    | 99.92% | 98.22%   |
| ADV   | 91.03%    | 88.24% | 89.61%   |
| CONJ  | 99.34%    | 99.13% | 99.24%   |
| PRT   | 91.76%    | 85.49% | 88.51%   |
| PRON  | 92.12%    | 95.46% | 93.76%   |
| NUM   | 98.79%    | 85.40% | 91.61%   |
| X     | 84.65%    | 13.92% | 23.92%   |

## Benchmarking Against ChatGPT

Performance comparison on first 100 sentences of TreeBank dataset:
- **HMM Model**: 83.11% accuracy
- **ChatGPT**: 81.78% accuracy

Our HMM model outperformed ChatGPT in overall accuracy, particularly excelling in:
- Punctuation tagging (`.`): 98.8% vs 80.3%
- Adposition tagging (`ADP`): 97% vs 81.5%
- Conjunction tagging (`CONJ`): 100% vs 82.7%
- Verb tagging (`VERB`): 91.6% vs 80.4%

## Error Analysis

### Common Confusion Patterns
1. **ADJ vs NOUN**: Words like "orange" and "light" can function as both adjectives and nouns
2. **ADV vs ADJ**: Context-dependent words like "hard" ("The test was hard" vs "They worked hard")
3. **NOUN vs VERB**: Many English words serve dual roles (e.g., "run", "play")

### Challenges Identified
- **Unseen Words**: Handling out-of-vocabulary terms effectively
- **Viterbi Implementation**: Complex dynamic programming table management
- **Backtracking**: Reconstructing optimal state sequences accurately

## Technical Implementation

### Algorithm Details
1. **Matrix Initialization**: Initialize probability matrices for each state at each time step
2. **Iterative Calculation**: Compute transition probabilities combined with observation likelihoods
3. **Backtracking**: Trace optimal path from final state to reconstruct tag sequence

### User Interface
- **GUI Implementation**: Interactive interface for real-time POS tagging
- **Supported Frameworks**: Gradio, Streamlit, or custom JavaScript/Python frameworks


