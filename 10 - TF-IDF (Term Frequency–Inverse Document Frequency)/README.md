📘 **What is TF-IDF?**

This is a fundamental concept in Natural Language Processing (NLP) and information retrieval, used to evaluate how important a word is to a document within a collection of documents (often called a corpus).

Think of it this way: TF-IDF helps you find the words that are most representative of a particular document, filtering out common words that appear everywhere.

It's made up of two distinct parts:
____________________________________________________________________

TF - IDF. (Term Frequency - Inverse document Frequency)

s1 ---> good  boy             |  TF = No of repeatation of words in sentence 
s2 ---> good  girl            |       ______________________________________
s3 ---> boy   girl good       |       No of words in sentence 

                              |  IDF =      No of sentences  
s2 ---> good  girl            |        log  ______________________________________
s3 ---> boy   girl good       |             No of sentences containing the word  

TF-IDF  is the comnination of tf and IDF ()

***Term Frequency***               *         ***IDF***

         s1      s2      s3                     Words      IDF     

good  |  1/2 |   1/2  |  1/3                   good       log(3/3) = 0
      |      |        |
boy   |  1/2 |   0    |  1/3                   boy        log(3/2)
      |      |        |  
girl  |  0   |   1/2  |  1/3                   girl       log(3/2) 

   ***Final TF - IDF*** 

           good         boy                  girl 

s1.         0           1/2  * log(3/2)       0

s2.         0            0                    1/2 * log(3/2)

s3.         0          1/3 * log(3/2)         1/3 * log(3/2)  

![alt text](image.png)

Advantages                                      Disadvantages
1. Intutive                                     1. Sparsity 
2. Fixed Size - Vocub size                      2. Out of vocublary (OOV)    
3. Word importance is getting captured(IMP)     3. 
____________________________________________________________________

1. Term Frequency (TF)
2. Inverse Document Frequency (IDF)

1. *** Term Frequency (TF) ***

What it measures: How often a specific word (term) appears in a single document.

***The intuition:*** If a word appears frequently in a document, it's likely to be important to the topic of that document. For example, if the word "galaxy" appears many times in a document, that document is probably about astronomy.

***How it's calculated:***
There are a few ways to calculate TF, but a common one is:

TF(t,d) =   Total number of terms in document d
            ____________________________________________
            Number of times term t appears in document d
​
 
This formula gives a normalized frequency, preventing a bias towards longer documents (which naturally might have higher raw counts of words).

Sometimes, to dampen the effect of very high counts (where a word appearing 100 times isn't necessarily 10 times more important than a word appearing 10 times), a logarithmic scale is used:


            TF(t,d)=log(1+raw count of t in d)

**Example:**

Consider Document 1: "The cat sat on the mat. The cat is black."

1. Term t = "cat"
2. Number of times "cat" appears in Document 1 = 2
3. Total number of terms in Document 1 = 10
4. TF("cat", Document 1)= 2/10 = 0.2


2. ***Inverse Document Frequency (IDF)***

What it measures: How common or rare a word is across the entire collection of documents (corpus). It gives more weight to rarer words and less weight to common words.

The intuition:

Words that appear in many documents (e.g., "the", "a", "is") are not very useful for distinguishing between documents. They have low informational content for this purpose.
Words that appear in only a few documents are likely more specific and can help differentiate those documents.
How it's calculated:

IDF(t,D)=log (  Total Number of document in corpus(N)  / Number of document containing term t (dft) )

Where:

N = Total number of documents in the corpus.

df t = Document frequency of term t (i.e., the number of documents that contain the term t).

***Why the logarithm?***

The log is used to dampen the effect. A term appearing in 10 documents isn't ten times rarer or more significant than a term appearing in 100 documents if the corpus size is, say, 1000. The logarithm helps to scale this effect.

Important Note on IDF:

* If a term appears in all documents (dft=N), then IDF(t,D)=log(N/N)=log(1)=0. This means the term has no discriminatory power according to IDF.

* To prevent division by zero if a term isn't in any document (which shouldn't happen if your vocabulary is built from the corpus), and to avoid giving too much weight to extremely rare words (that might be typos), sometimes a smoothed version is used, such as:

IDF(t,D)=log( N+1 / dft + 1 ) + 1

***Combining TF and IDF: The TF-IDF Score***

The TF-IDF score for a term in a document is simply the product of its TF and IDF values:

TF-IDF(t,d,D)=TF(t,d)×IDF(t,D)

What the TF-IDF score tells you:

A high TF-IDF score is achieved when a term has a high frequency in a specific document (high TF) AND a low frequency in the overall corpus (high IDF). This means the term is very characteristic of that particular document.
A low TF-IDF score can result from:
The term having a low frequency in the document (low TF).
The term being very common across all documents (low IDF), like "and", "is", "of".
A zero TF-IDF score means the term does not appear in the document at all, or it appears in all documents (if IDF becomes zero).


***Why is TF-IDF useful? (Applications)***

TF-IDF is a cornerstone in many NLP and text analysis tasks:

Information Retrieval & Search Engines: When you type a query, search engines can calculate the TF-IDF scores for query terms in all documents. Documents with higher TF-IDF scores for those terms are considered more relevant and ranked higher.

***Keyword Extraction:*** Identifying terms with the highest TF-IDF scores in a document can help pinpoint its main topics or keywords.

***Text Summarization:*** Sentences containing words with high TF-IDF scores might be considered more important for inclusion in a summary.

***Document Classification and Clustering:*** TF-IDF vectors (where each component is the TF-IDF score of a word in the vocabulary) can represent documents numerically. These vectors can then be fed into machine learning algorithms to categorize or group documents.

***Stop-word Filtering (implicitly):*** Common words like "the," "is," "a" naturally receive very low IDF scores (and thus low TF-IDF scores), reducing their impact without needing a predefined stop-word list (though using one is still common practice).


***Advantages of TF-IDF***

Simple to Understand and Compute: The underlying concepts are intuitive, and the calculations are straightforward.
Effective Baseline: Provides a good starting point for many text-based tasks and often yields reasonable results.
Reduces Importance of Common Words: Automatically gives lower weight to terms that are frequent across all documents.

***Limitations of TF-IDF***

***Ignores Word Order:*** TF-IDF is a "bag-of-words" model, meaning it only considers the presence and frequency of words, not their sequence or grammatical relationships. "Man bites dog" and "Dog bites man" would have very similar TF-IDF representations if they use the same words.
***No Semantic Understanding:*** It doesn't capture the meaning of words or relationships between them (e.g., synonyms like "car" and "automobile" are treated as completely different terms).
***Sparsity:*** For large vocabularies, the resulting TF-IDF vectors for documents are often very sparse (containing many zeros), which can be computationally intensive for some algorithms.
***Corpus Dependent:*** The IDF values are calculated based on the specific corpus you are using. They will change if the corpus changes.
***Not as Advanced as Modern Techniques:*** While foundational, for tasks requiring deeper understanding of language, more advanced techniques like word embeddings (e.g., Word2Vec, GloVe, FastText) and transformer models (e.g., BERT, GPT) often perform better as they can capture semantic meanings and contextual relationships.


Text Preprocessing is important for every technique.

![alt text](Text-Preprocessing.png)