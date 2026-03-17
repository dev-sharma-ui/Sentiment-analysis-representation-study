Comparative Sentiment Analysis: Sparse vs Dense Text Representations

A comprehensive Natural Language Processing (NLP) project that compares classical machine learning techniques with neural network approaches for sentiment classification. This project evaluates how different text representation strategies impact model performance on large-scale movie review data.

Project Overview

Sentiment analysis is a fundamental NLP task used to determine whether a piece of text expresses positive or negative sentiment. While deep learning models are widely used today, classical approaches using sparse representations often perform surprisingly well on structured datasets.

This project investigates the effectiveness of sparse text representations (TF-IDF) compared to dense word embeddings (Word2Vec and FastText) when combined with both traditional machine learning models and neural networks.

Using the IMDB movie review dataset (50,000 labeled reviews), multiple models were implemented and compared to understand performance trade-offs between different representation techniques and learning architectures.

The project includes:

End-to-end NLP pipeline

Multiple representation techniques

Classical and deep learning models

Visualization of embedding space

Systematic error analysis

Dataset

IMDB Movie Review Dataset

50,000 labeled movie reviews

Balanced dataset

Binary sentiment classification

25,000 training samples

25,000 testing samples

Each review is labeled as:

Positive

Negative

This dataset is widely used as a benchmark for sentiment classification tasks.

Project Pipeline

The complete workflow implemented in this project:

Raw Text Reviews
        ↓
Text Preprocessing
        ↓
Train-Test Split
        ↓
Text Representation
   ├── TF-IDF (Sparse Representation)
   ├── Word2Vec (Dense Embedding)
   └── FastText (Subword Embedding)
        ↓
Model Training
   ├── Logistic Regression
   └── LSTM Neural Network
        ↓
Model Evaluation
        ↓
Embedding Visualization (t-SNE)
        ↓
Error Analysis
Text Preprocessing

The following preprocessing steps were applied:

Lowercasing text

Removing HTML tags

Removing punctuation and numbers

Removing extra spaces

Preserving stopwords to retain sentiment context (e.g., "not good")

This ensures the data remains informative while reducing noise.

Models Implemented
1. TF-IDF + Logistic Regression (Baseline)

TF-IDF converts text into a sparse high-dimensional vector representing word importance.

Logistic Regression then learns the relationship between these features and sentiment labels.

Key characteristics:

Captures important sentiment phrases

Uses unigram and bigram features

Efficient and highly interpretable

Performance:

Accuracy: 89.3%

This model served as the baseline benchmark.

2. Word2Vec + Logistic Regression

Word2Vec generates dense word embeddings that capture semantic similarity between words.

Sentence embeddings were created by averaging word vectors.

Logistic Regression was then used for classification.

Performance:

Accuracy: 86.3%

The drop in performance occurs because averaging word embeddings removes phrase structure and word order.

3. FastText + Logistic Regression

FastText extends Word2Vec by using character-level subword information.

This allows the model to better handle rare or morphologically related words.

However, since the IMDB dataset has good vocabulary coverage, FastText did not significantly outperform Word2Vec.

Performance:

Accuracy: 86.3%

4. LSTM + Word2Vec Embeddings

An LSTM neural network was implemented to capture sequential dependencies in text.

Key features:

Word embeddings used as input

Sequence modeling to preserve word order

Ability to handle negation patterns

Performance:

Accuracy: 87.8%

This improved performance compared to averaged embeddings.

5. LSTM + FastText Embeddings

FastText embeddings were used in the embedding layer of the LSTM model.

Performance:

Accuracy: 87.7%

FastText slightly improved recall but did not outperform the TF-IDF baseline.

Model Comparison
Model	Accuracy	Notes
TF-IDF + Logistic Regression	89.3%	Best performing model
Word2Vec + Logistic Regression	86.3%	Dense embedding baseline
FastText + Logistic Regression	86.3%	Similar performance to Word2Vec
LSTM + Word2Vec	87.8%	Sequence modeling improves embeddings
LSTM + FastText	87.7%	Higher recall
Embedding Visualization

To better understand representation quality, sentence embeddings were visualized using t-SNE dimensionality reduction.

Findings:

Positive and negative reviews showed significant overlap

Word embeddings capture semantic similarity but not strong sentiment polarity

Class separation becomes clearer only after classification models learn decision boundaries

Error Analysis

Misclassified reviews were analyzed to identify common patterns.

Key observations:

Contrast Structures

Example:

"The idea is interesting, but the execution is terrible."

Models often struggle with contrast clauses.

Mixed Sentiment Reviews

Some reviews contain both positive and negative opinions, making binary classification difficult.

Sarcasm and Subtle Tone

Sentiment may depend on context or sarcasm that models cannot easily interpret.

Key Insights

The main takeaway from this project:

Classical sparse representations like TF-IDF can outperform deep learning models on structured sentiment datasets.

Reasons:

Sentiment is often expressed through short phrases

Bigram features explicitly capture patterns like “not good”

Linear models work extremely well in high-dimensional sparse spaces

Deep learning models introduce more complexity but require larger datasets to consistently outperform classical approaches.

Tech Stack

Python

NumPy

Pandas

Scikit-learn

Gensim (Word2Vec, FastText)

TensorFlow / Keras

Matplotlib

Seaborn

Jupyter Notebook

Future Improvements

Possible enhancements include:

Using contextual embeddings such as BERT

Implementing BiLSTM with attention mechanisms

Hyperparameter tuning

Deploying the model as an API or web application

Training on larger or multi-domain sentiment datasets

Learning Outcomes

This project helped develop a deeper understanding of:

Text representation techniques in NLP

Sparse vs dense feature engineering

Sequence modeling using LSTM

Model evaluation and comparison

Debugging deep learning pipelines

Interpreting model behavior through visualization and error analysis

Author

Dev Sharma

GitHub: https://github.com/dev-sharma-ui

LinkedIn: https://www.linkedin.com/in/dev-sharma786/
