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

rename the 'Valuation Decimal' and 'Funding Decimal' back to 'Valuation' and 'Funding'

```
df.rename(columns={'Valuation Decimal' : 'Valuation'}, inplace= True)
df.rename(columns={'Funding Decimal' : 'Funding'}, inplace= True)
```

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

### Further Exploratory Data Analysis after Data Cleaning

Data Profiling

recheck the data size
```
df.shape
```

recheck the data size
```
df.size
```

recheck the data columns
```
df.columns
```

recheck the data information
```
df.info()
```

recheck for null values
```
df.isnull().sum()
```

check for negative values in 'Valuation'
```
df[df['Valuation'] < 0]
```

check for negative values in 'Valuation'
```
df[df['Funding'] < 0]
```

check the dataframe description for objects
```
df.describe(include= ['object'])
```

recheck the data description

you can see the the Valuation and Funding are now showing up
```
int_columns = df['Year Founded'].describe().astype(int)
float_columns = df[['Valuation','Funding']].describe().astype(float)
```

concatenate/ join the'Year Funded' to show as int, and 'Valuation' and 'Funding' to show as float 
```
joined_columns = pd.concat([float_columns, int_columns], axis= 1)
joined_columns
```
![image](https://github.com/Ugochukwuodinaka/Exploratory-Data-Analysis-of-Global-Unicorn-Companies/assets/157266999/07838266-8dc5-44b2-9145-be024ec95098)

checking for Outliers

the calculation summary statistics of 'Valuation' and 'Funding' columns 
```
summary = df[['Valuation', 'Funding']].describe().astype(float)
```

create a box plot of the 'Quantity' and 'UnitPrice' columns
```
fig, axs = plt.subplots(nrows=1, ncols=2, figsize=(10, 5))

axs[0].boxplot(df['Valuation'])
axs[0].set_title('Valuation')

axs[1].boxplot(df['Funding'])
axs[1].set_title('Funding')
```

add the summary statistics to the box plots
```
for i, ax in enumerate(axs):
    ax.text(0.95, 0.95, f"Min: {summary.iloc[3,i]}\nQ1: {summary.iloc[4,i]}\nMedian: {summary.iloc[5,i]}\nQ3: {summary.iloc[6,i]}\nMax: {summary.iloc[7,i]}", transform=ax.transAxes, fontsize=10, va='top', ha='right', bbox=dict(boxstyle='round', facecolor='white', alpha=0.8))
```

adjust the spacing between subplots
```
fig.tight_layout()
```
show the box plot
```
plt.show()
```
![image](https://github.com/Ugochukwuodinaka/Exploratory-Data-Analysis-of-Global-Unicorn-Companies/assets/157266999/747039b5-952a-43a4-bc53-3bdde91c0f81)

check the number of Unicorn Company locations by continent
```
new_size = df.groupby(['Continent', 'Country']).size()
new_size
```

recheck for distinct industries
```
df.Industry.unique()
```

### KEY PERFORMANCE INDICATORS (KPIs)

#### Total Valuation of Unicorn Companies
```
valuation_sum = df['Valuation'].sum()
new_valuation = '${:,.3f}.T'.format(valuation_sum/ 10**12)
new_valuation
```

#### Total Number of Unicorn Companies
```
companies = df.Company.nunique() - -1
companies
```

#### Total Number of Unicorn Industries
```
industries = df.Industry.nunique()
industries
```

#### Total Number of Unicorn Continents
```
continents = df.Continent.nunique()
continents
```

#### Total No of Unicorn Countries
```
countries = df.Country.nunique()
countries
```

#### Total Number of Unicorn Cities
```
cities = df.City.nunique()
cities
```

#### Total Amount Received by Unicorn Companies
```
funding_sum = df['Funding'].sum()
new_funding = '${:,.3f}.B'.format(funding_sum/ 10**9)
new_funding
```

### Visualization and Oobservations

#### Univariate Analysis

the Decriptive Statistics of the Numerical Columns
```
int_columns = df['Year Founded'].describe().astype(int)
float_columns = df[['Valuation','Funding']].describe().astype(float)
```

concatenate/ join the'Year Funded' to show as int, and 'Valuation' and 'Funding' to show as float  
```
joined_columns = pd.concat([float_columns, int_columns], axis= 1)
joined_columns
```
![Unicorn 4](https://github.com/Ugochukwuodinaka/Exploratory-Data-Analysis-of-Global-Unicorn-Companies/assets/157266999/02febdc2-5aa6-42d3-bad7-23d27ededf12)

#### Observation and Summary:

**Valuation:**

The dataset includes information on the valuation of 1074 unicorn companies. The mean valuation of these companies is approximately $3.46 billion, indicating that, on average, unicorn companies are valued quite high in the market. The standard deviation of valuations is relatively large, indicating significant variability in the valuations of different companies. The minimum valuation observed is $1 billion, which is the threshold for achieving unicorn status. The maximum valuation in the dataset is an impressive $180 billion, showcasing the immense value some unicorn companies have accrued. The interquartile range (IQR) of valuations spans from $1 billion to $3 billion, indicating that most companies fall within this range, with some outliers having much higher valuations.

**Funding:**

The dataset also provides information on the funding received by each unicorn company. The mean funding raised by these companies is approximately $551 million, highlighting the substantial investment capital these companies have attracted. The standard deviation of funding amounts is relatively high, indicating significant variability in the amounts of funding raised by different companies. The minimum funding amount observed is $0, suggesting that some companies may not have raised any external funding. The maximum funding amount in the dataset is $14 billion, indicating the substantial financial backing received by some unicorn companies. The IQR of funding amounts spans from $218 million to $603 million, indicating that most companies fall within this range, with some outliers having received much larger amounts of funding.

**Year Founded:**

The dataset includes the year in which each unicorn company was founded. The mean year of founding for these companies is approximately 2012, suggesting that many unicorn companies are relatively young, having been founded in the past decade. The standard deviation of founding years is 5 years, indicating some variability in the ages of unicorn companies. The earliest founding year observed is 1919, indicating that some unicorn companies have been around for over a century. The most recent founding year observed is 2021, indicating that new unicorn companies continue to emerge even in the present year. The majority of unicorn companies in the dataset were founded between 2011 and 2016, as indicated by the interquartile range.

In summary, the descriptive statistics provide valuable insights into the characteristics of unicorn companies, including their valuations, funding amounts, and founding years. Overall, the data suggests that unicorn companies are highly valued, attract significant investment capital, and are relatively young, with many having been founded in the past decade. However, there is also significant variability among unicorn companies, with some outliers having exceptionally high valuations and funding amounts.

#### Bivariate Analysis

The Top 10 Most Valued Companies
```
top10_companies = df.groupby('Company')['Valuation'].sum().sort_values(ascending= False).head(10).reset_index(name= 'Valuation')
top10_companies
```
Plotting a hbarplot

create a figure and axis
```
fig, ax = plt.subplots(figsize=(10, 6))
```
create the horizontal barplot with a custom color palette
```
sns.barplot(x="Valuation", y="Company", data=top10_companies, palette=['#08306b', '#08519c', '#08519c', '#2171b5',  '#4292c6', '#6baed6', '#6baed6', '#9ecae1', '#c6dbef', '#c6dbef'], ax=ax)
```

add 'Valuation' labels to the bars
```
for index, row in top10_companies.iterrows():
    valuation = row["Valuation"]
    if valuation >= 1e9:
        label = f"${valuation/1e9:.1f}B"
    else:
        label = f"${valuation/1e6:.1f}M"
    ax.text(valuation, index, label, ha="left", va="center", fontsize=10, color="black", fontweight= 'bold')
```

customize the plot
```
ax.set(xlabel="Total Valuation", ylabel="Company")
plt.title("Top 10 Most Valuable Unicorn Companies", fontsize=14, fontweight= 'bold')
plt.xticks(rotation=0)

plt.show()
```
![image](https://github.com/Ugochukwuodinaka/Exploratory-Data-Analysis-of-Global-Unicorn-Companies/assets/157266999/b246a84b-327f-4865-9e9f-eb540e54eb41)

#### Observation and Summary:

**Bytedance** stands out as the highest-valued unicorn company, with an astonishing valuation of **$180 billion**. **Bytedance** is known for its flagship product, TikTok, a popular short-form video-sharing app.

Following closely behind **Bytedance** is **SpaceX** and **SHEIN**, both valued at **$100 billion** each. **SpaceX**, founded by Elon Musk, is a leading aerospace manufacturer and space transportation company, while SHEIN is an e-commerce platform specializing in fast fashion.

**Stripe** secures the fourth position with a valuation of **$95 billion**. **Stripe** is a fintech company that provides online payment processing services for businesses.

**Klarna, Checkout.com,** and **Canva** share the next positions with valuations of **$46 billion, $40 billion,** and **$40 billion,** respectively. **Klarna** is a Swedish fintech company offering buy now, pay later services, while **Checkout.com** is a global payment processing platform. **Canva** is a graphic design platform that allows users to create various types of visual content.

**Instacart** follows closely with a valuation of **$39 billion**. **Instacart** is an online grocery delivery and pickup service that has gained significant traction, especially during the COVID-19 pandemic.

Lastly, **JUUL Labs** and **Databricks** complete the top 10 with valuations of **$38 billion** each. **JUUL Labs** is a controversial e-cigarette company, while **Databricks** is a data analytics platform used by organizations for big data processing and machine learning.

In summary, the table showcases the immense valuations attained by the top unicorn companies, reflecting their significant influence and market dominance across various industries. These companies have disrupted traditional business models, introduced innovative technologies, and capitalized on changing consumer preferences to achieve remarkable growth and valuation milestones. Their success underscores the dynamism and potential of the unicorn ecosystem, where visionary entrepreneurs and innovative startups continue to redefine the global business landscape.

The Top 8 Companies With The Highest Funding
```
top8_companyF = df.groupby('Company')['Funding'].sum().sort_values(ascending= False).head(8)
top8_companyF
```
Plotting a barplot

create a vertical barplot showing the top 8 companies that with the highest funding
```
plt.figure(figsize=(10, 6))  # Adjust the figure size as needed
sns.set_style("white")
```
create a custom sequential color palette using seaborn
```
custom_palette = ['#08306b', '#08519c', '#08519c', '#08519c', '#2171b5', '#2171b5', '#2171b5', '#2171b5', '#6baed6', '#6baed6']
```
create the barplot with explicit palette setting
```
ax = sns.barplot(x=top8_companyF.index, y=top8_companyF, palette=custom_palette)
```
add 'Total Funding' labels to the bars with custom formatting
```
for index, value in enumerate(top8_companyF):
    if value >= 1e9:
        label = f"${value/1e9:.1f}B"
    else:
        label = f"${value/1e6:.1f}M"
    ax.text(index, value, label, ha="center", va="bottom", fontsize=10, color="black", fontweight='bold')
```
customize the plot
```
ax.set(xlabel="Company", ylabel="Total Funding")
plt.title("Top 8 Unicorn Companies With Most Funding", fontsize=15, fontweight='bold')
plt.xticks(rotation=45)

plt.show()
```
![image](https://github.com/Ugochukwuodinaka/Exploratory-Data-Analysis-of-Global-Unicorn-Companies/assets/157266999/b21260fb-3bdf-47dc-885a-87b86c62cef5)

#### Observation and Summary:

**JUUL Labs** secures the top position with the highest funding amount of **$14 billion**. **JUUL Labs** is a company known for its e-cigarette products, although it has faced significant scrutiny and regulatory challenges.

Following **JUUL Labs** is **Bytedance** with **$8 billion** in funding. **Bytedance** is a Chinese technology company known for its popular short-form video-sharing app, TikTok, among other digital products.

**Epic Games** and **SpaceX** share the third position with funding amounts of **$7 billion** each. **Epic Games** is a video game developer and publisher, best known for its hit game Fortnite. **SpaceX**, founded by Elon Musk, is a pioneering aerospace manufacturer and space transportation company.

The next four companies - **Global Switch, Xingsheng Selected, Swiggy**, and **J&T Express** - all share the same funding amount of **$5 billion** each.

- **Global Switch** is a leading provider of data center services.
  
- **Xingsheng** Selected is a Chinese grocery chain operator.
  
- **Swiggy** is an Indian online food delivery platform.
  
- **J&T Express** is a logistics and delivery services company based in Southeast Asia.
  
In summary, the table highlights the significant funding received by these top companies, which reflects investor confidence in their business models, growth potential, and ability to disrupt their respective industries. These companies have used their substantial funding to fuel expansion, innovation, and market dominance, solidifying their positions as key players in the global business landscape. Additionally, the diversity of industries represented among the top-funded companies underscores the broad range of opportunities attracting investment in today's dynamic market environment.
