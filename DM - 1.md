# data mining
- use of efficient techniques for *analysis* of very large collection of data and the *extraction* useful and possibly unexpected *patterns* in data
- why do we need data mining
	- huge amount of raw data maintained due to cheap storage (cloud storage)
	- we need to analyse this *raw data* to extract *knowledge*

# raw data
- multiple types
	- tables
	- time series
	- images
	- graphs, etc
- spatial and temporal aspects
- interconnected data of different types

## transaction data
- data regarding different kinds of transactions
- companies collect the information about the trasnactions generated from the users

## document data
- web pages
- articles
- online new portals
- short message form - twitter
- each document is like a vector
	- each term is a component (attribute) of the vector
	- value of each component is the number of times the corresponding term occurs in the document
	- in *bag-of-words* representation, there is no ordering

## network data
- web pages inks via hyperlinks
- the network traffic from one user to another over the internet

## genomic sequences
- sequences of genes

## environmental data
- database of different types of data for temperature, precipitation, pressure, etc.
- managed by government bodies

## behavioural data
- mobile phones capturing user behavioural data 
- human habits, tendencies, etc. 

# types of attributes
1. categorical
	- nominal - categories not having any ranking among them
	- ordinal - categories are ordered, but not comparable
	- special type - binary
2. numerical
	- discrete
	- continuous

# what can you do with data?
- query reformation for search engine data
- clustering, correlation and value prediction from stock data
- important nodes. shortest path, sentiment analysis from social network data

>[!NOTE]
>- streamed data: before analysing, the data is stored, which is called streamed data
>- unstreamed dat: directly taken from source for analysis

>Data Mining is analysis of observational data sets to find unsuspected relationships and to summarize the dat in novel ways that are both understandable and useful to the data analyst 
>- Hand, Mannila, Smyth

# KDD Process
- knowledge discovery in data
![[Pasted image 20230718124025.png|600]]

# architecture of data mining
![[Pasted image 20230718124605.png|400]]

# what can you do with data mining?
- coverage 
- clustering
- classification
- ranling
- exploratory analysis

# frequent itemsets and association rules
- given a set of records each contain some number of items from a given collection
- identify set of *items occurring frequently together*
- produce *dependency rules* which will predict occurrence of an item based on occurrences of other items
- applications
	- **frequent itemsets**
		- *text mining*
			- finding associated phrases in text
		- *recommendations*
			- users buying/using items together frequently
			- engines make use of item and user similarity
	- **association rules**
		- *supermarket shelf management*


