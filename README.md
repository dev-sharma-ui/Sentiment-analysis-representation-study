📊 Comparative Sentiment Analysis: Sparse vs Dense Text Representations

A comprehensive Natural Language Processing (NLP) project that compares classical machine learning techniques with deep learning approaches for sentiment classification.

This project investigates how different text representation techniques influence model performance on the IMDB Movie Review Dataset (50,000 reviews).

🚀 Project Highlights

Built a complete end-to-end NLP pipeline

Compared sparse vs dense text representations

Implemented both classical ML models and neural networks

Visualized embeddings using t-SNE

Performed systematic error analysis

📂 Dataset

IMDB Movie Review Dataset

Property	Value
Total Reviews	50,000
Classes	Positive / Negative
Training Samples	25,000
Testing Samples	25,000

This dataset is a widely used benchmark for sentiment analysis.

⚙️ Project Pipeline
Raw Text Reviews
        ↓
Text Preprocessing
        ↓
Train-Test Split
        ↓
Text Representation
   ├── TF-IDF
   ├── Word2Vec
   └── FastText
        ↓
Model Training
   ├── Logistic Regression
   └── LSTM
        ↓
Evaluation
        ↓
t-SNE Visualization
        ↓
Error Analysis
🧹 Text Preprocessing

The following preprocessing steps were applied:

Lowercasing text

Removing HTML tags

Removing punctuation and numbers

Removing extra spaces

Preserving stopwords to maintain sentiment context

Example:

Original: "This movie was NOT good!!!"
Cleaned:  "this movie was not good"
🤖 Models Implemented
1️⃣ TF-IDF + Logistic Regression (Baseline)

TF-IDF converts text into sparse high-dimensional vectors representing word importance.

Logistic Regression learns which words contribute to positive or negative sentiment.

Example features:

"good" → positive weight
"terrible" → negative weight
"not good" → negative weight
Performance

Accuracy: 89.3%

This model performed the best.

2️⃣ Word2Vec + Logistic Regression

Word2Vec generates dense semantic word embeddings.

Sentence embeddings were created by averaging word vectors.

Performance

Accuracy: 86.3%

Averaging embeddings loses word order and phrase structure.

3️⃣ FastText + Logistic Regression

FastText extends Word2Vec using character n-grams to handle rare words.

Performance

Accuracy: 86.3%

Since the dataset vocabulary is clean, FastText did not significantly outperform Word2Vec.

4️⃣ LSTM + Word2Vec Embeddings

An LSTM neural network was implemented to capture sequential dependencies.

Advantages:

Preserves word order

Handles negation patterns

Models contextual information

Performance

Accuracy: 87.8%

5️⃣ LSTM + FastText Embeddings

FastText embeddings were used within the LSTM embedding layer.

Performance

Accuracy: 87.7%

📊 Model Comparison
Model	Accuracy
TF-IDF + Logistic Regression	89.3%
Word2Vec + Logistic Regression	86.3%
FastText + Logistic Regression	86.3%
LSTM + Word2Vec	87.8%
LSTM + FastText	87.7%
📈 Embedding Visualization (t-SNE)

To understand representation quality, sentence embeddings were visualized using t-SNE dimensionality reduction.

Observations:

Positive and negative embeddings showed significant overlap

Word embeddings capture semantic similarity but not strong sentiment polarity

Class separation emerges after classification models learn decision boundaries

🔍 Error Analysis

Misclassified reviews revealed common patterns:

Contrast Clauses

Example:

"The story is interesting, but the execution is terrible."

Models struggle with sentiment flips after "but".

Mixed Sentiment Reviews

Reviews containing both positive and negative opinions confuse models.

Sarcasm

Sarcasm remains challenging for most NLP models.

💡 Key Insights

This project demonstrates that:

Sparse representations like TF-IDF can outperform deep learning models for structured sentiment classification tasks.

Reasons:

Sentiment is often expressed through short phrases

Bigram features capture patterns like “not good”

Linear models perform well in high-dimensional sparse spaces

🛠 Tech Stack

Python

NumPy

Pandas

Scikit-learn

Gensim (Word2Vec, FastText)

TensorFlow / Keras

Matplotlib

Seaborn

Jupyter Notebook

📌 Future Improvements

Possible extensions include:

Using BERT or Transformer models

Implementing BiLSTM with attention

Hyperparameter tuning

Building a web application or API

👨‍💻 Author

Dev Sharma

GitHub
https://github.com/dev-sharma-ui

LinkedIn
https://www.linkedin.com/in/dev-sharma786/

⭐ If you found this project interesting, consider giving it a star!
