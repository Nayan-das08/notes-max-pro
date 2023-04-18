---
subject: 
category: lab-file
---
>%%Links: [[Lab Files]]%%

# Experiment 9
Mar 23, 2023

## Objective
To do text pre-processing - Tokenization, Stop word removal, Stemming/Lemmatization, Parts of speech tagging, Rule Generation for Parsing

## Theory
<u>Tokenization</u> - Sentence tokenization refers to the process of separating the lines of a paragraph using a delimiter. Word tokenization means separating words of a sentence into its constituent words, example “She is a girl” will be tokenized to ‘She’, ‘is’, ‘a’, ‘girl’, ‘.’.

<u>Stop word removal</u> - This entails the process of discarding the words which do not incur significant meaning from a sentence so that more importance and weightage is imparted to the words which hold significant meaning, example words like ‘is’, ‘are’.

<u>Stemming</u> - Process of converting a word to its root form to find patterns and relations among different words, for example caring converted to car and cared converted to care.

<u>Lemmatization</u> - Process of converting a word to root or base form but this method, unlike stemming, takes care of meaning perseverance, for example caring is changed to care and not car.

<u>Parts of speech tagging</u> - This is the process of tagging words of a sentence into different parts of speech, example boy will be tagged as noun and dancing as a verb. They are used for syntax analysis and parsing in Natural Language Processing.

---
## Source Code
### 1.  Tokenization
```
import nltk
from nltk.tokenize import sent_tokenize
from nltk.tokenize import word_tokenize
text = “My name is John. I am 20 years old. I live in New York.”
print(sent_tokenize(text))
print(word_tokenize(text))
word_tokens = word_tokenize(text)
['My name is John.', 'I am 20 years old.', 'I live in New York.']
['My', 'name', 'is', 'John', '.', 'I', 'am', '20', 'years', 'old', '.', 'I', 'live', 'in', 'New', 'York', '.']
```

### 2. Stop word removal
```
nltk.download('stopwords')
from nltk.corpus import stopwords
stop_words = set(stopwords.words('english'))
filtered_sentence = []
for w in word_tokens:
    if w not in stop_words:
        filtered_sentence.append(w)
print(filtered_sentence)
['My', 'name', 'John', '.', 'I', '20', 'years', 'old', '.', 'I', 'live', 'New', 'York', '.']
```

### 3. Lemmatization
```  
from nltk.corpus import wordnet as wn
from nltk.stem.wordnet import WordNetLemmatizer
from nltk.stem import WordNetLemmatizer
lemmatizer = WordNetLemmatizer()
lemmatised_text = [lemmatizer.lemmatize(token) for token in word_tokens]
display(f"lemmatised nltk text: {lemmatised_text}")
lemmatised nltk text: ['My', 'name', 'is', 'John', '.', 'I', 'am', '20', 'year', 'old', '.', 'I', 'live', 'in', 'New', 'York', '.']

```

### 4. Stemming
```  
from nltk.stem import PorterStemmer
porter = PorterStemmer()
stemmed_words = [porter.stem(token) for token in word_tokens]
display(f"stemmed nltk text: {stemmed_words}")
stemmed nltk text: ['my', 'name', 'is', 'john', '.', 'i', 'am', '20', 'year', 'old', '.', 'i', 'live', 'in', 'new', 'york', '.']

```

### 5. Parts of speech tagging
```
nltk.download('averaged_perceptron_tagger')
tagged = nltk.pos_tag(word_tokens)
print(tagged)
[('My', 'PRP$'), ('name', 'NN'), ('is', 'VBZ'), ('John', 'NNP'), ('.', '.'), ('I', 'PRP'), ('am', 'VBP'), ('20', 'CD'), ('years', 'NNS'), ('old', 'JJ'), ('.', '.'), ('I', 'PRP'), ('live', 'VBP'), ('in', 'IN'), ('New', 'NNP'), ('York', 'NNP'), ('.', '.')]
```

### 6. Parse tree generation
```
import nltk
# Define the updated grammar
grammar = nltk.CFG.fromstring("""
    S -> NP VP
    NP -> 'There' | N P
    VP -> V V NP PP
    V -> 'have' | 'been' | 'saw' 
    PP -> PRP V PRP
    P -> 'since'
    N -> 'centuries'
    DET -> 'a' | 'an' | 'the'
    ADJ -> 'old' | 'long'
    PRP -> 'I' | 'her'
""")
# Define the input sentence
sentence = "There have been centuries since I saw her"
# Create a parser
parser = nltk.ChartParser(grammar)
# Parse the sentence and print the parse tree
for tree in parser.parse(sentence.split()):
print(tree)
```

---
## Output
```
(S
  (NP There)
  (VP
    (V have)
    (V been)
    (NP (N centuries) (P since))
    (PP (PRP I) (V saw) (PRP her))))
```