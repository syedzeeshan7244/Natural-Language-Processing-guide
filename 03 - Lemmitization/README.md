
📚 ***What is Lemmatization in NLP?***

Lemmatization is the process of reducing a word to its base or dictionary form, known as a lemma. Unlike stemming, which simply chops off word endings, lemmatization takes grammatical context into account (like part of speech), making it more linguistically accurate.

| Word    | Lemma | Part of Speech |
| ------- | ----- | -------------- |
| running | run   | Verb           |
| better  | good  | Adjective      |
| studies | study | Noun           |
| was     | be    | Verb           |


✅ Key Characteristics:

Produces valid dictionary words.
Uses a lexicon (dictionary) and morphological analysis.
Considers the part of speech (POS) to get the correct base form.

🧪 Lemmatization vs. Stemming:

| Feature       | Lemmatization                 | Stemming              |
| ------------- | ----------------------------- | --------------------- |
| Accuracy      | High (linguistically correct) | Lower (rule-based)    |
| Output        | Real words                    | May not be real words |
| Context-aware | Yes (uses POS tagging)        | No                    |
| Speed         | Slower                        | Faster                |

from nltk.stem import WordNetLemmatizer
from nltk.corpus import wordnet

lemmatizer = WordNetLemmatizer()

print(lemmatizer.lemmatize("running", pos="v"))  # run
print(lemmatizer.lemmatize("better", pos="a"))   # good
print(lemmatizer.lemmatize("cats"))              # cat