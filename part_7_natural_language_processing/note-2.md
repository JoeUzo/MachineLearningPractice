## Bag of Words (BoW) Model

**Watch the video: [▶️](https://www.udemy.com/course/machinelearning/learn/lecture/20091386#content)**

The **Bag of Words (BoW)** model is a simple and widely-used technique in **Natural Language Processing (NLP)** for text representation. It transforms textual data into a numerical format, allowing machine learning algorithms to process it.

---

### Table of Contents
- [Introduction to Bag of Words](#introduction-to-bag-of-words)
- [How Bag of Words Works](#how-bag-of-words-works)
- [Example of Bag of Words](#example-of-bag-of-words)
- [Applications](#applications)
- [Advantages](#advantages)
- [Disadvantages](#disadvantages)

---

### Introduction to Bag of Words

The **Bag of Words** model represents text data as a collection of words without considering the order of words or their grammatical structure. It focuses only on the frequency of words in a document or dataset, effectively creating a "bag" of words.

---

### How Bag of Words Works

1. **Tokenization**:
   - Split the text into individual words or tokens.

2. **Vocabulary Creation**:
   - Create a unique list of all words (vocabulary) across the dataset.

3. **Vector Representation**:
   - For each document, create a vector of the same length as the vocabulary.
   - Each element in the vector represents the count of a word from the vocabulary in the document.

---

### Example of Bag of Words

#### Dataset:
Suppose we have the following two sentences:
1. "I love NLP."
2. "I love machine learning."

#### Steps:
1. **Tokenization**:
   - Sentence 1: `["I", "love", "NLP"]`
   - Sentence 2: `["I", "love", "machine", "learning"]`

2. **Vocabulary Creation**:
   - Vocabulary: `["I", "love", "NLP", "machine", "learning"]`

3. **Vector Representation**:
   - Sentence 1: `[1, 1, 1, 0, 0]` (counts of words: "I", "love", "NLP", "machine", "learning")
   - Sentence 2: `[1, 1, 0, 1, 1]`

---

### Applications

1. **Text Classification**:
   - Sentiment analysis, spam detection, and topic classification.

2. **Information Retrieval**:
   - Search engines and document ranking.

3. **Document Similarity**:
   - Measuring how similar two documents are.

---

### Advantages

1. **Simple to Implement**:
   - Straightforward and easy to understand.

2. **Works Well for Smaller Datasets**:
   - Effective when the vocabulary is not too large.

3. **Foundation for Advanced Models**:
   - Used as a baseline for more complex models like TF-IDF and Word Embeddings.

---

### Disadvantages

1. **Ignores Word Order**:
   - Cannot capture relationships between words (e.g., "not good" vs. "good").

2. **High Dimensionality**:
   - Large vocabulary leads to sparse and high-dimensional vectors.

3. **Lacks Context**:
   - Doesn't consider the meaning or context of words.

---

### Code Example in Python

Using **scikit-learn**'s `CountVectorizer`:

```python
from sklearn.feature_extraction.text import CountVectorizer

# Sample data
documents = ["I love NLP", "I love machine learning"]

# Initialize CountVectorizer
vectorizer = CountVectorizer()

# Fit and transform the data
X = vectorizer.fit_transform(documents)

# Display the vocabulary
print("Vocabulary:", vectorizer.get_feature_names_out())

# Display the vector representation
print("Vectors:\n", X.toarray())
```







# Practical Example
See the practical example in the video and the practical notebook **[here](./practical/hierarchical_clustering.ipynb)**.  
**Watch the video: [▶️](https://www.udemy.com/course/machinelearning/learn/lecture/19875774#content)**