# Data Preprocessing

## why needed
- data in real world is dirty
- incomplete, lacking certain attributes of interest
	- NA values
- noisy
	- errors
	- outliers
- inconsistent

## why important
- no quality data, no quality mining results
	- duplicate or missing data may cause incorrect or even misleading statistics
	- data warehouse needs consistent integration of quality data
- data extraction, cleaning, transformation comprises majority of work of maintaining data warehouse

## multi dimensional measure of data quality
1. accuracy: correct or wrong
2. completeness: not recorded or unavailable
3. consistency
4. timeliness: latest
5. believability: trust
6. interpretability: understandable or not

## major tasks in data preprocessing
- data cleaning
	- filling missing values
	- smooth noisy data
	- identify and remove outliers
	- resolve inconsistencies
- data integration
	- integration of multiple databases, data cubes or files
- data transformation
	- normalization and aggregation
- data reduction
	- reduced representation in volume but produce the same or similar analytics
- data discretization

## data summarization
- done before preprocessing
- obtain overall picture of data
- identify prop of data and highlight data values which should be treated as noise or outliers
- central tendencies and dispersions are used

### measures of central tendencies
- **mean**
	- only for interval or ratio levels of measurement
	- impacted by outliers
- **median**
	- only when data is ordinal, interval or ratio levels of measurement
- **mode**
	- most applicable for nominal level of measurement
	- nominal data is classified into mutually exclusive categories
	- tells the most popular category
	- not helpful for continuous variable

### types of measures
- **distributive measure**
	- computed for a dataset by partitioning into subsets
	- results is of smaller subsets
	- results are merged to arrive at measure for original data
	- *eg*: sum, count, max, min
- **algebraic measure** 
	- apply algebraic functions to one of more distributive measures
	- *eg*: mean, weighted arithmetic mean, trimmed mean
- **holistic measure**
	- computed on entire dataset as a whole
	- cannot be applied on subsets of dataset
	- *eg*: median

>[!NOTE]
>$$mean-mode = 3 \times (mean-median)$$

### midrange
- average of the largest and smallest values in the dataset
- another central tendency measure

### how distributions depends on central tendencies
- data is either normal or skewed
- normal
	- data is symmetrically distributed
	- no skew
	- most values cluster around a center value
	- mean = median = mode
- skewed
	- more values fall on one side of center than the other
	- mean, median, mode not equal anymore
	- positvely skewed
		- to the right
		- mode < median < mean
	- negatively skewed
		- to the right
		- mean < median < mode

---
