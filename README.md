# Exploratory-Data-Analysis-of-Global-Unicorn-Companies

## Project Screenshot From Power Bi Dashboard
![Unicorn_Companies_Analysis_Project_Dashboard_page- 1](https://github.com/Ugochukwuodinaka/Exploratory-Data-Analysis-of-Global-Unicorn-Companies/assets/157266999/d35e957d-8082-4c86-9f2a-d381917ff0ef)

## Project Overview
Global unicorn companies refer to privately-held startup companies valued at over $1 billion. These companies are often characterized by rapid growth, disruptive innovation, and the potential to transform industries. The term "unicorn" was coined by venture capitalist Aileen Lee in 2013 to describe the rarity of such companies, as they were once considered mythical creatures in the business world due to their scarcity.

The evolution of global unicorn companies has been remarkable, with their rise closely tied to advancements in technology and changes in consumer behavior. Over the past few decades, especially with the advent of the internet and digital technologies, the number of unicorn companies has grown significantly, spanning various sectors such as e-commerce, fintech, healthcare, transportation, and beyond.

Some notable examples of global unicorn companies include:

**Uber:** Founded in 2009, Uber revolutionized the transportation industry by introducing a peer-to-peer ridesharing platform accessible via a mobile app. 

**Airbnb:** Launched in 2008, Airbnb disrupted the hospitality industry by enabling individuals to rent out their homes or spare rooms to travelers.

**Stripe:** Founded in 2010, Stripe provides online payment processing solutions for businesses, allowing them to accept payments over the internet. 

**SpaceX:** Founded in 2002 by Elon Musk, SpaceX is on a mission to revolutionize space exploration and make humanity a multi-planetary species. 

**ByteDance:** ByteDance, founded in 2012, is a Chinese technology company known for its flagship product, TikTok, a short-form video-sharing app. 

**Palantir Technologies:** Founded in 2003, Palantir Technologies specializes in big data analytics and software solutions for government agencies, financial institutions, and other organizations. 

These are just a few examples of the many global unicorn companies that have emerged in recent years, each making significant contributions to their respective industries and reshaping the way we live, work, and interact in the modern world.

Moving forward to the main aim of this project, we will be analyzing the emergence, evolvement and funding trends of Global Unicorn Companies.

## Dataset Overview
The primary dataset used in this analysis is the "Unicorn_Companies.csv" and "Data_Dictionary-1.csv" files. These dataset was released by [Quantum Analytics](https://www.quantumanalyticsco.org/). It is made up of CSV files for Global Unicorn Companies from the founding of the first Unicorn in 1919 to the year 2021. The Data_Dictionary.csv file gives an explanation of the fields in the main dataset Unicorn_Companies.csv, while the main dataset comes with the columns: Company, Valuation, Date Joined, Industry, City, Country, Continent, Year Founded, Funding, and Select Investors.

## Metadata
The dataset contains 8 columns and here's a breakdown of what each column represents:

**Company:** This column contains the names of the unicorn companies included in the dataset.

**Valuation:** This column contains the valuation of each unicorn company, measured in terms of billion dollars ($1 billion or more), which represents the estimated worth of the company in the market.

**Date Joined:** This column contains the date when each company achieved unicorn status, which means the date when their valuation exceeded $1 billion.

**Industry:** This column contains the industry or sector to which each unicorn company belongs. It specifies the primary area of business or the market in which the company operates.

**City:** This column contains the city where each unicorn company is headquartered or has a significant presence.

**Country:** This column contains the country where each unicorn company is based or founded.

**Continent:** This column contains the continent where each unicorn company's country is located.

**Year Founded:** This column contains the year when each unicorn company was established or founded.

**Funding:** This column contains information about the total funding raised by each unicorn company, which represents the cumulative amount of investment capital received from investors.

**Select Investors:** This column contains the names of notable investors or investment firms that have provided funding to each unicorn company. It may include venture capital firms, private equity investors, or other institutional investors.

## Data Cleaning and Exploratory Data Analysis using Python

### EXPLORATORY DATA ANALYSIS STEPS
- Importing the required Libraries for EDA
- Acquiring the dataset
- Data Preparation
- Data Profiling
- Data Cleaning
- Dropping Duplicates
     - Removing Missing Values
     - Finding Outliers
- Finding Correlations
- Visualizations

Importing the required Libraries for EDA
```
import pandas as pd
import os
import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np
import plotly.express as px
```
Assign df as pandas DataFrame
```
df = pd.DataFrame()
```
Acquire the dataset
```
df = pd.read_csv(r"Unicorn_Companies.csv")
```
The dataset in a DataFrame
```
df
```
![Unicorn 1](https://github.com/Ugochukwuodinaka/Exploratory-Data-Analysis-of-Global-Unicorn-Companies/assets/157266999/19a53090-cbff-4a1d-bfa7-6aa8e2ef2413)

Check first 10 rows of data
```
df.head(10)
```
Last 10 rows of data
```
df.tail(10)
```

### DATA PROFILING STEPS
- Data profiling utilizes methods of descriptive statistics such as:
  1. Data type
  2. Quantile statistics (central tendecies)
  3. Length (length and shape of the dataset)
  4. Discrete values
  5. Uniqueness (unique values)
  6. Occurence of null values and etc.

shape of the data
```
df.shape
```
size of data
```
df.size
```

check the columns
```
df.columns.tolist()
```
check for the data information
```
df.info()
```
Check for missing values
```
df.isnull().sum()
```
check for numerical columns
```
categorical_cols = df.select_dtypes(include = [int, float]).columns.tolist()
categorical_cols
```
check for categorical columns
```
numerical_cols = df.select_dtypes(include = ['category', 'object']).columns
numerical_cols
```
```
df.describe(include= ['object'])
```
check for distinct or duplicate continents
```
df.Continent.unique()
```
check for distinct or duplicate industries
```
df.Industry.unique().tolist()
```
check for distinct or duplicate countries
```
df.Country.unique().tolist()
```

### Data Cleaning Processes
- Convert the Date Joined column from a "string" to a "Datetime"

- Fill the missing values in City with "Uknown"

- Fill the missing value in Select Investors with "Uknown"

- Replace the "Artificial intelligence" in Industry column with "Artificial Intelligence"

- Replace the string "Unknown" in Funding with "0"

- Convert the Valuation Column from a "string" to a "float" with the "$" sign

- Convert the Funding column from a "string" to a "float" with the "$" sign

convert the 'Date Joined' column from a 'string' to a 'Datetime'
```
df['Date Joined'] = pd.to_datetime(df['Date Joined'])
```
check if Date Joined data type has been changed to Datetime
```
df.dtypes
```
replace the "Artificial intelligence" in **Industry** column with "Artificial Intelligence"
```
df['Industry'] = df['Industry'].replace('Artificial intelligence', 'Artificial Intelligence')
```
check if the change has been effected
```
df.Industry.unique().tolist()
```
fill the missing values in city with 'Uknown'
```
df['City'] = df['City'].fillna('Unknown')
```
fill the missing value in 'Select Investors' with 'Unknown'
```
df['Select Investors'] = df['Select Investors'].fillna('Unknown')
```
re-ceck to confirm that no column now has null values
```
df.isnull().sum()
```
find the column data row with string data type 'Unknown' in the 'Funding' column
```
df[df['Funding'] == 'Unknown'].head(12)
```
replace the string "Unknown" in Funding with "0"
```
df['Funding'] = df['Funding'].replace('Unknown', '0')
```
check to confirm that the "Fudning" column no longer has the string "Uknown"
```
df[df['Funding'] == 'Unknown'].head()
```
confirm that the column "Funding" now has the numerical value 0
```
df[df['Funding'] == '0'].head(12)
```
follow these next steps in code order:
- convert the Valuation Column from a "string" to a "float".
- define a custom function to convert the string to float
- remove the '$' signs from the string
- extract the numerical part of the string
- get the last character to determine the scale (Billion or Million)
- multiply the numeric value based on the scale
- re-add the '$' sign and return as a Decimal object
```
def convert_valuation(valuation_str):
    valuation_num = valuation_str.replace('$', ' ')
    numeric_part = valuation_num[:-1]
    scale = valuation_num[-1]

    if  scale == 'B':
        valuation_float = float(numeric_part) * 1e9
    elif scale == 'M':
        valuation_float = float(numeric_part) * 1e6
    else:
        raise ValueError('Invalid scale: {}', format(scale))
        
    
    return float(valuation_float)
```
apply the custom function to the "Funding" column and create a new column 'Funding Decimal'
```
df['Valuation Decimal'] = df['Valuation'].apply(convert_valuation)    
df.head()
```
confirm data type changes
```
df.dtypes
```
follow these next steps in code order:
- convert the Funding Column from a "string" to a "float".
- define a custom function to convert the string to Decimal
- remove the '$' signs from the string
- extract the numerical part of the string
- get the last character to determine the scale (Billion or Million)
- multiply the numeric value based on the scale
- re-add back the '$' sign and return as a Decimal object
```
def convert_funding(funding_str):
    funding_num = funding_str.replace('$', ' ')
    numeric_part = funding_num[:-1]
    
    scale = funding_num[-1]
    
    if  scale == 'B':
        funding_float = float(numeric_part) * 1e9
    elif scale == 'M':
        funding_float = float(numeric_part) * 1e6
    elif scale == '0':
        funding_float = '0'
    else:
        raise ValueError('Invalid scale: {}', format(scale))
        
    return float(funding_float)
```
apply the custom function to the "Funding" column and create a new column 'Funding Decimal'
```
df['Funding Decimal'] = df['Funding'].apply(convert_funding)  
df.head()
```
re-confirm data types
```
df.dtypes
```
drop the 'Valuation' and 'Funding' columns so that we can use the new one created
```
df.drop(columns= ['Valuation', 'Funding'], inplace= True)
df.dtypes
```
reename the 'Valuation Decimal' and 'Funding Decimal' back to 'Valuation' and 'Funding'
```
df.rename(columns={'Valuation Decimal' : 'Valuation'}, inplace= True)
df.rename(columns={'Funding Decimal' : 'Funding'}, inplace= True)
``
re-confirm column names and data types
```
df.dtypes
```
follow these next steps in code order:
- change the position of the column 'Valuation' back to where it was initially
- remove the 'Valuation' column from the current position
- insert the 'Valuation' column at the desired position
- reindex the dataframe with the new column order
```
column_names= df.columns.tolist()
valuation_col = column_names.pop(column_names.index('Valuation'))
column_names.insert(1, valuation_col)

df = df.reindex(columns= column_names)    
df.head()
```
follow these next steps in code order:
- change the positions of the columns 'Funding' back to where they were initially
- remove the 'Valuation' column from the current position
- insert the 'Valuation' column at the desired position
- reindex the dataframe with the new column order
```
column_names= df.columns.tolist()
valuation_col = column_names.pop(column_names.index('Funding'))
column_names.insert(8, valuation_col)

df = df.reindex(columns= column_names)    
df.head()
```
check all changes with the top 10 rows of data
```
df.head(10)
```
![Unicorn 3](https://github.com/Ugochukwuodinaka/Exploratory-Data-Analysis-of-Global-Unicorn-Companies/assets/157266999/7c4c9623-2aed-4845-a5be-90a44065dff6)
