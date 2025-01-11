# Part of Speech Tagging using Hidden Markov Models

This project implements a Part-of-Speech (POS) tagger using Hidden Markov Models (HMM) for Turkish language text. The system is trained and evaluated on the Turkish Treebanks dataset from Google Research.

## Overview

The project trains two HMM models:
1. Full model using all 14 POS tags
2. Limited model using only 5 tags (ADJ, ADV, NOUN, VERB, PUNC)


## Dataset

The project uses Turkish Treebanks from Google Research:
- web.conllu: Web domain text
- wiki.conllu: Wikipedia domain text

Data is automatically downloaded from: https://github.com/google-research-datasets/turkish-treebanks

## Implementation Details

### Data Preprocessing
- Combines web and wiki datasets
- 80/20 train/test split
- Handles rare words using `<UNK>` token
- Adds `<START>` and `<END>` tags for sentence boundaries

### HMM Components
1. Maximum Likelihood Estimation (MLE)
   - Transition probabilities
   - Emission probabilities
   - Add-1 smoothing

2. Viterbi Algorithm
   - Predicts optimal tag sequence
   - Uses log probabilities for numerical stability

### Performance: Before Rare Word Handling
####  Full Tag Set (14 tags):
- Accuracy: 75.51%
- F1 Macro: 53.22%
- F1 Weighted: 75.49%
#### Limited Tag Set (5 tags):
- Accuracy: 88.89%
- F1 Macro: 74.78%
- F1 Weighted: 87.92%

### Performance: After Rare Word Handling
#### Full Tag Set (14 tags):
- Accuracy: 75.96% (+0.45%)
- F1 Macro: 53.11% (-0.11%)
- F1 Weighted: 75.83% (+0.34%)
#### Limited Tag Set (5 tags):
- Accuracy: 88.33% (-0.56%)
- F1 Macro: 73.99% (-0.79%)
- F1 Weighted: 87.32% (-0.60%)

## Potential Improvements
- Implement Kneser-Ney smoothing
- Add word prefix/suffix features
- Use bigram/trigram models for better context
- Enhance handling of rare/unknown words

## Limitations
- First-order HMM limits context modeling
- Add-one smoothing penalizes frequent patterns
- `<UNK>` token loses word-specific context

## Future Improvements

### 1. Advanced Smoothing
- Implement Kneser-Ney smoothing
- Add morphological features for Turkish words
- Explore interpolation techniques

### 2. Enhanced Context Modeling
- Implement bigram/trigram HMM models
- Add prefix/suffix feature analysis
- Consider syntactic dependencies

### 3. Improved Rare Word Handling
- Dynamic `<UNK>` threshold based on corpus size
- Character-level embeddings for unknown words
- Morphological analysis for Turkish word stems