# Contradiction Scoring Model - README

This notebook implements an algorithm to score the level of contradiction between pairs of statements using a pre-trained language model. Below is a breakdown of the functionality, inputs, outputs, and usage instructions.

## Overview
The algorithm preprocesses text data and uses a pre-trained `roberta-large-mnli` model to detect contradictions between pairs of statements. It first cleans and tokenizes the text by removing symbols, stopwords, and applying lemmatization. The model then takes both the original and preprocessed text to compute contradiction scores. 

The notebook reads data from a CSV file, processes each statement pair, and returns the contradiction scores, allowing comparison between raw and cleaned text for better insights.

## Requirements
The following libraries are required to run the notebook:
- `transformers`
- `pandas`
- `numpy`
- `scipy`
- `sklearn`
- `spacy`
- `nltk`
- `re`

You can install the necessary packages by running:

pip install transformers pandas numpy scipy scikit-learn spacy nltk

## Inputs
The main inputs to this notebook are pairs of text statements that are compared for contradiction.

- **CSV File**: The notebook expects a CSV file containing pairs of statements to analyze.
- **Corpus 1**: The first block of text to compare (from the CSV).
- **Corpus 2**: The second block of text to compare (from the CSV).

The notebook applies preprocessing to both corpora, including:
- Lowercasing
- Tokenization
- Stopwords removal
- Lemmatization
- Removal of punctuation (except for 'CO2').

## Outputs
The notebook outputs a **Contradiction Score** between the two corpora for both the original and preprocessed versions of the text. This is generated using the `roberta-large-mnli` model from the Hugging Face Transformers library.

The model assigns one of three possible labels to the comparison:
- **Contradiction**: The two texts are contradictory.
- **Neutral**: There is no strong contradiction or agreement.
- **Entailment**: The two texts agree with each other.

## Usage
1. **Read Data from CSV**:
   The notebook reads pairs of statements from a CSV file for processing.

2. **Preprocess the text**: 
   The function `preprocess_text` is used to clean and prepare the text inputs before passing them to the model.

   Example:
   ```python
   preprocessed_text = preprocess_text(corpus)

3.	Score Contradiction:
The function get_contradiction_score computes the contradiction score between the two corpora for both raw and preprocessed text.
Example:
result = get_contradiction_score(corpus1, corpus2)

4.	Interpret the Result:
The result will contain a label and a score indicating the level of contradiction, neutrality, or agreement between the texts for both original and cleaned versions.

Notes

	•	This notebook uses the RoBERTa model fine-tuned on a natural language inference task.
	•	Ensure that the inputs are preprocessed appropriately for accurate results.

Example
corpus1 = "The sky is blue."
corpus2 = "The sky is not blue."
result = get_contradiction_score(corpus1, corpus2)
print(result)

The output would be a classification label, for instance:
[{'label': 'CONTRADICTION', 'score': 0.99}]

##Author

This notebook was created for use in natural language processing tasks related to contradiction detection, allowing detailed comparison between raw and cleaned text.

   
