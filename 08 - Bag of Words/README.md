🧠 ***Bag of Words (BoW)***

🔷 ***1. What is Bag of Words?***
Bag of Words is a text representation technique used in Natural Language Processing (NLP) and Machine Learning.

   "It converts text into numerical vectors by counting how many times each word appears in a document."

"Bag" = we ignore grammar and word order.

Only focus on which words appear and how often.

***********************************************************

s1. He is a good boy                                    s1.  good boy
s2. she is a good girl      -----> Lower all the words  s2.  good girl 
s3. Boy and girl are good          Apply stopwords      s3.  boy girl good 

Vocublary       Frequency           
  good              3               good   boy   girl                 
  boy               2         s1   [ 1      1      0 ]
  girl              2         s2   [ 1      0      1 ]  
                              s3   [ 1      1      1 ]
  Binar Bow   and       Bow 
  {1 and 0}       { Count will get updated base on frequencey}    
***********************************************************
🔷 ***2. Why Use BoW?***

Most ML algorithms require numeric input, but text is inherently non-numeric.

BoW helps by:

Converting text into fixed-length vectors

Making it possible to use classic ML models (like logistic regression, SVM, etc.)

🔷 ***3. How Does It Work?***

Imagine we have 2 simple sentences:

1. "I love NLP"
2. "NLP loves me"

***Step-by-Step:8**

Vocabulary Building

First, collect all unique words from the dataset.

Vocabulary: ["i", "love", "nlp", "loves", "me"]

Vector Representation

For each sentence, create a vector based on word count.

| Word  | "I love NLP" | "NLP loves me" |
| ----- | ------------ | -------------- |
| i     | 1            | 0              |
| love  | 1            | 0              |
| nlp   | 1            | 1              |
| loves | 0            | 1              |
| me    | 0            | 1              |

🔷 4. Key Characteristics

| Feature              | Description                                                 |
| -------------------- | ----------------------------------------------------------- |
| 🔢 Numeric Output    | Converts text into numbers.                                 |
| 📏 Fixed-Length      | Every document is the same size (length = vocabulary size). |
| ❌ No Order Retention | The order of words is not preserved.                        |
| ✅ Simple             | Very easy to understand and implement.                      |


🔷 5. Limitations of BoW

| Limitation                | Why it matters                                             |
| ------------------------- | ---------------------------------------------------------- |
| Ignores grammar           | "Dog bites man" vs. "Man bites dog" → same vector!         |
| No semantic meaning       | Doesn’t capture word similarity (e.g., "happy" ≠ "joyful") |
| High-dimensional & sparse | Large vocabularies create big sparse vectors               |
| Doesn't handle synonyms   | Each word treated as independent                           |


Advantages                 and             Disadvantages 
Simple and intuitive                       Sparse matrix and array  --- >  Overfitting 
Fixed Size I/P -> ML                       Ordering of the word getting change 
                                           Out of vocublary (OOV)
                                           Semantic meaning is still not getting captured      


The food is good     [1  1  1  0  1 ]
The food is not good [1  1  1  1  1 ]