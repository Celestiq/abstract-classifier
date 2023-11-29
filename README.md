# abstract-classifier

## Pre-processing
The function 'preprocess_text_with_line_numbers' processes a text file containing abstract samples, where each abstract begins with an ID (starting with "###"), and the target and text are separated by a tab character ("\t"), for example,  'METHODS\tOutcome measures included pain reduction and improvement in function scores and systemic inflammation markers .\n'

The function reads the file, extracts relevant information, and returns a list of dictionaries, where each dictionary represents a line (or sentence) in an abstract. Each dictionary contains the following information about every line:
1. Target
2. Text
3. Line Number
4. Total Lines
The hence obtained list of dictionaries is then converted to a DataFrame.

## Models
| Model | Accuracy | F1-Score |
| ---------|----------|----------|
| Baseline | 72.18 | 0.698 |
| Token + Character Embedding | 73.59 | 0.733 |
| Token + Character + Positional Embedding | 83.26 | 0.831 |

### Model 0: Baseline Model
A baseline model was constructed using Naive Bayes. TF-IDF vectorizer was used before MultinomialNB in a pipeline to assign vectors to every word. The baseline model gave an accuracy of 72.18 with an f1 score of 0.698

### Model 1: Token and Character Level Embedding
Unviersal Sentence Encoder for token level encoding and Tensorflow's TextVectorizer for char level encoding were used.
Firstly, two individual models were created for character and token level embeddings, they were then concatenated then output was obtained. This model gave an accuracy of 73.59 with an f1 score of 0.733

### Model 2: Character and Token Embedding + Positional Embedding
In this model, line numbers and total lines were also One Hot Encoded along with the previous encodings. All these layers models and then trained. This gave the highest accuracy of 83.26 and f1 score of 0.8313
