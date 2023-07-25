>[!NOTE]
>- Case study
>- 2 ppl

# Intro
- for NLP, there are 3 stages
	- **Lexical Processing**
		- you will be required to do text preprocessing and text cleaning
		- steps such as tokenization, stemming, lemmatization, correcting the spellings, etc
	- **syntax processing**
		- you will be required to extract more meaning from the content by using ... instead of just blankly looking at what the words are 
		- will be looking at the syntactic structure, i.e., the grammar of the language to understand what the meaning is 
	- **semantic processing**
		- above processings do not suffice when it comes to advance NLP processing such as language translation, chatbot, etc.

# Tokenization
- We need to break the text corpus into different words or sentences or paragraphs.
- The NLTK Python library has various tokenizers:
	- Word Tokenizer
		- Used to break the text corpus into a list of words.
  - Sentence Tokenizer
	- Used to break the text corpus into different sentences.
  - Tweet Tokenizer
	- Used to tokenize the text corpus into different words. This also tokenizes social media elements such as emojis and hashtags correctly unlike the word tokenizer.
  - Regexp
	- Used to tokenize the text corpus using a regular expression.

## Stemming and Lemmatization:
- After tokenizing the document and removing the stop words (is, and, etc.), the next step is to reduce the words to their base form.

### Stemming:
  - It is a rule based technique that just chops off the suffix of a word to get its root form which is called the stem.
  - Example:
	- driver -> driv
	- racing -> rac

### Lemmatization:
  - This is a more sophisticated technique in the sense that it does not just chop off the suffix of a word.
  - Instead, it takes an input word and searches for its base word by going recursively through all variations of the dictionary words.
  - Example:
    - driver -> drive
    - racing -> race

## Bag of Words:
- Document 1: Gangs of Wasseypur is a great movie.
- Document 2: The success of a movie depends on the performance of the actors
- Document 3: There are no new movies releasing this week

# Canonical
- phonetic hashing
	- there are certain words have different pronunciation in different languages
	- as a result they end up being spelled differently
	- eg of such words: names of people, city names, etc.
	- using soundex (NLTK, an algo), we can reduce all the words to a 4 digit code 
	- all the words with same soundex can be mapped to a common word 
	- eg: soundex of Bangalore and Bengaluru is B524
	- the algo is as follows
		1. retain the first letter of the word
		2. replace consonants with digits according to the following
			- b,f,p,v $\rightarrow$ 1
			- c,g,j,k,q,s,x,z $\rightarrow$ 2
			- d,t $\rightarrow$ 3
			- l $\rightarrow$ 4
			- m,n $\rightarrow$ 5
			- r $\rightarrow$ 6
			- h,w,y $\rightarrow$ unencoded
		3. remove all the vowels and unencoded letters and then merge the consecutive numbers
		4. continue till the code has one letter and 3 numbers
		5. if the length of code is greater than 4, then truncate
		6. in case the code is shorter than 4, pad it with zeroes
		- `mississippi`
		- M,i,2,2,i,2,2,i,1,1,i
		- M,2,2,2,2,1,1
		- M210
- spell character

$tf_{t,d} = \text{freq of term t in doc d}$


# text encoding
- all the non num char were encoded to numbers using a code
- also, the encoding technique had to be in the standard form so that different computer manufacture would not use different encoding techniques

# regex
- very powerful programming tool that are used for a variety of purposes such as feature extraction, string replacement and other string manipulation

