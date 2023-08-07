# EDA Report

## Introduction

**Summary of the Data Set**: 
The automobile dataset contains information concerning 205 observations and 26 attributes. 
It encompasses information about various cars including make, model, fuel type, engine size, horsepower, and price, among other variables. 
There is a mix of continuous and categorical variables, as well as missing values which require cleaning and imputation before analysis.

## Data Cleaning

### Summary of Methods and Visualizations

During data cleaning, the following methods and visualizations were used:
* Imported required packages
* Loaded the dataset into a Pandas dataframe
* Used `.info()` to find the data types and null fields
* Noted object datatypes where int was expected and noted ‘?s’ in the data and replaced all instances of '?' with NaN using `.replace()`
* Checked for missing values using `.isnull().sum()` and noted that 'normalized-losses' had 41 missing datapoints; which is close to ¼ of the data
* Dropped the 'normalized-losses' column since it was not going to be used in the analysis

### Handling Missing Data

Remaining missing data were addressed as follows:

**Handling 'num-of-doors'**:
* Visualized the distribution of the 'num-of-doors' column using a countplot
* Found the mode of the 'num-of-doors' column using `.mode().iloc[0]`
* Filled the missing values in 'num-of-doors' column with the mode using `.fillna(mode, inplace=True)`

**Addressing 'bore', 'stroke', 'horsepower', 'peak-rpm', 'price'**:
* Visualized the respective columns using histograms for each column using a for loop and based on this decided to use medians to replace Nans
* Grouped the dataframe by 'make' and calculated the median values for each group for columns 'bore', 'stroke', 'horsepower', 'peak-rpm', and 'price' 
* Iterated over the group names and filled the missing values with corresponding medians using a for loop and `.fillna()`
* To address horsepower and peak-rpm that still had NaNs, noted that the missing horsepower and peak-rpm did not have corresponding data based on their make to calculate medians from
* Filled the missing values in 'horsepower' and 'peak-rpm' columns with the medians of the entire dataset (not make specific) using `.fillna()`

Lastly, before starting with data exploration, the columns with the missing values now filled in were converted to usable variable types; i.e. float and integer

## Data Stories and Visualizations

### Correlation Heatmap

The heatmap provides a brief overview of the correlations between variables by measuring how strongly two variables are related, ranging from -1 to 1.
A positive correlation indicates that as one variable increases, the other variable also tends to increase. 
A negative correlation means that as one variable increases, the other variable tends to decrease. A correlation of zero indicates little to no correlation.
From this particular heatmap, we can observe the strongest positive correlations (in descending order) as follows:
* City-mpg and Highway-mpg (correlation = 0.97)
* Curb-weight and Length (correlation = 0.88)
* Price and Engine-size & Wheel-base and Length (correlations both = 0.87)
Similarly, we can identify the strongest negative correlations (in descending order) as follows:
* Curb-weight and Highway-mpg & Horsepower and City-mpg (correlations both = -0.8)
* Horsepower and Highway-mpg (correlation = -0.77)
* Curb-weight and City-mpg (correlation = -0.76)
Based on these observations, we can extrapolate which numerical variables may be relevant to explore further. H
eatmaps are particularly useful for large datasets, and even though the automobile dataset only contains 205 vehicles, we can still gain a general understanding
from the heatmap.

### Frequency by Make

A barplot displays the distribution of cars in the dataset based on their make. Toyota is the most represented make in the dataset, with 33 cars,
while Mercury has the lowest representation with only one car.

### Mean Price by Make

The bar graph displays the average price of a car for each make. The graph shows that Jaguar has the highest average price,
while Chevorlet has the lowest. Exploring all variables in relation to make may reveal other interesting data stories. 
However, it's important to keep in mind that the dataset contains only three Jaguars and three Chevrolets, whereas there are 33 Toyotas. 
Therefore, due to the small sample size of some makes, our conclusions might be biased when comparing makes with a lot of data to those with very few data.

### Fuel Systems Analysis

A pie chart illustrates different fuel system usage, with "mpfi" and "2bbl" being the most prevalent.

### Box Plot - Horsepower by Fuel System

The box plot and averages offer additional insights into the relationship between the fuel system used and the vehicle's horsepower, 
reinforcing the association between "mpfi" and higher horsepower values.

### Bar Plot - Fuel System and Fuel Type

This bar plot not only indicates that most vehicles in the dataset operate on gas, but also provides insight into the distribution of
fuel systems based on fuel type, notably showcasing the exclusive use of "idi" for diesel-fueled vehicles.

## Conclusion

This EDA report primarily focused on data cleaning and conducting basic exploratory analysis to gain an initial understanding of relationships 
and patterns within the dataset. Further analysis could be conducted on variables including price or other categorical variables to gain deeper insights. 
Improvement to the EDA could be achieved by adding more advanced statistical analyses, such as regression models, hypothesis testing, or clustering techniques.
When drawing conclusions from the dataset, it is essential to recognize its limitations, including the small number of cars for some makes. 
Moreover, it is crucial to be mindful of potential biases in the data, such as selection bias or measurement error.




