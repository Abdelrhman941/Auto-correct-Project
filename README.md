# Natural Language Correction System

## Overview
This project implements a **Natural Language Correction System** focused on spelling and grammar correction using advanced NLP techniques. It consists of two main components:
1. A GUI-based application (`NLP_gui.ipynb`) for correcting text using the Gramformer model.
2. A comprehensive correction pipeline (`natural-language-correction-system.ipynb`) that combines multiple correction methods, including Gramformer, PySpellChecker, and a custom bigram model.

The system is designed to process raw text, correct grammatical and spelling errors, and present results in an organized format. It leverages libraries like NLTK, PyTorch, and Transformers for NLP tasks.

---

## Project Structure

| File                          | Description                                      |
|-------------------------------|--------------------------------------------------|
| `NLP_gui.ipynb`              | A Gradio-based GUI app for text correction.      |
| `natural-language-correction-system.ipynb` | A detailed pipeline for spelling and grammar correction with bigram modeling. |

---

## Features

### 1. GUI Application (`NLP_gui.ipynb`)
- Interactive interface using Gradio.
- Corrects grammar in input text or uploaded `.txt` files.
- Displays results in an HTML table with "Before" and "After" columns.
- Uses the Gramformer model for grammar correction.

### 2. Correction Pipeline (`natural-language-correction-system.ipynb`)
- Combines multiple correction methods:
  - **PySpellChecker**: For spelling correction.
  - **Gramformer**: For grammar correction.
  - **Custom Bigram Model**: For contextual word correction.
- Processes a dataset of sentences and additional test sentences.
- Highlights differences between original and corrected sentences.
- Includes vectorization for potential seq2seq model training.

---

## Requirements
To run the project, ensure you have the following libraries installed:

| Library              | Purpose                          |
|----------------------|----------------------------------|
| `gramformer`         | Grammar correction model        |
| `gradio`             | GUI for the application         |
| `nltk`               | Text tokenization and processing|
| `pyspellchecker`     | Spelling correction             |
| `language-tool-python`| Additional grammar checking     |
| `torch`              | PyTorch for model operations    |
| `transformers`       | For NLP models                  |
| `pke`                | Keyphrase extraction (if used)  |

### Installation
Run the following commands to install the required libraries:

```bash
pip install git+https://github.com/PrithivirajDamodaran/Gramformer.git -q
pip install gradio -q
pip install nltk -q
pip install language-tool-python -q
pip install python-Levenshtein -q
pip install pyspellchecker -q
pip install torch -q
pip install transformers -q
pip install git+https://github.com/boudinfl/pke.git -q
```

Additionally, download NLTK data:
```python
import nltk
nltk.download('punkt')
nltk.download('punkt_tab')
```

---

## Usage

### 1. Running the GUI Application (`NLP_gui.ipynb`)
1. Open the notebook in Jupyter or Google Colab.
2. Run all cells to install dependencies and launch the Gradio interface.
3. Input text in the textbox or upload a `.txt` file.
4. The corrected text will be displayed in an HTML table with "Before" (red) and "After" (green) columns.

### 2. Running the Correction Pipeline (`natural-language-correction-system.ipynb`)
1. Open the notebook in Jupyter or Google Colab.
2. Run the cells sequentially:
   - Install dependencies.
   - Load and preprocess the dataset.
   - Apply spelling and grammar correction.
3. The output will display corrected sentences with highlighted differences.

---

## Methodology

### Grammar Correction Flow
1. **Input**: Raw text with potential errors.
2. **Tokenization**: Split text into sentences using NLTK's `sent_tokenize`.
3. **Spelling Correction**: Apply PySpellChecker to fix spelling errors.
4. **Grammar Correction**: Use Gramformer to correct grammar.
5. **Contextual Correction**: Apply a bigram model to improve word choice based on context.
6. **Output**: Display corrected text with highlighted changes.

### Vectorization (for Future Training)
- Text is converted to numerical sequences (`text_seqs` for incorrect text, `clean_seqs` for corrected text).
- Split into training and validation sets for potential seq2seq model training (e.g., LSTM or Transformer).

---

## Results
The system processes a dataset of sentences and additional test cases. Example output:

| Before                          | After                          |
|---------------------------------|--------------------------------|
| I doesnt no how to spel corectly. | I don't know how to spell correctly. |
| She buyed a new car yesturday.  | She bought a new car yesterday.    |

---

## Future Improvements
- Train a seq2seq model (LSTM/Transformer) using the vectorized data.
- Integrate more advanced grammar models (e.g., T5 or BERT-based).
- Add support for multiple languages.
- Optimize the bigram model for larger datasets.

---
- Asem Ahmed Mohamed

---

## License
This project is licensed under the MIT License. Feel free to use, modify, and distribute the code for educational purposes.
