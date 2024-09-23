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
