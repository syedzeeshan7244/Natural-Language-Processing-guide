📚 *** What Is Part-of-Speech Tagging ? ***

Part-of-Speech tagging is the process of labeling each word in a sentence with its grammatical role, like:

1. Noun (NN)
2. Verb (VB)
3. Adjective (JJ)
4. Adverb (RB)
5. Pronoun (PRP)
6. Preposition (IN), etc.

🧠 ***Why Use POS Tagging ?***
POS tagging helps computers understand the structure of a sentence. It's useful for:

1. Syntax analysis
2. Named Entity Recognition (NER)
3. Machine translation
4. Text-to-speech systems
5. Information extraction

🔧 ***How to Do POS Tagging in Python (with NLTK)***
Step-by-Step Example:

import nltk

# Download required resources (only once)
nltk.download('punkt')
nltk.download('averaged_perceptron_tagger')

# Example sentence
sentence = "Dr. APJ Abdul Kalam inspired millions through his vision for India."

# Tokenize the sentence into words
words = nltk.word_tokenize(sentence)

# Perform POS tagging
pos_tags = nltk.pos_tag(words)

# Show result
print(pos_tags)


🔎 ***Output Explained:***
Example output:
[('Dr.', 'NNP'), ('APJ', 'NNP'), ('Abdul', 'NNP'), ('Kalam', 'NNP'),
 ('inspired', 'VBD'), ('millions', 'NNS'), ('through', 'IN'),
 ('his', 'PRP$'), ('vision', 'NN'), ('for', 'IN'), ('India', 'NNP'), ('.', '.')]
