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

#### The Top 10 Most Valued Companies
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

#### The Top 8 Companies With The Highest Funding
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

#### The Top 5 Unicorn Industries by Valuation
```
top5_industries = df.groupby('Industry')['Valuation'].sum().sort_values(ascending= False).head().reset_index(name= 'Valuation')
top5_industries
```
Creating a pie chart to show the 5 Unicorn Industries with the highest valuation

extract the data for the pie chart

```
industries = top5_industries['Industry']
valuation = top5_industries['Valuation']
colors = ['#08306b', '#08519c', '#6F8FAF', '#0096FF', '#2171b5']
```
define explode (to highlight a slice)

```
explode = (0.06, 0.02, 0, 0, 0)  # You can adjust the explosion for the slice you want to highlight
```
create the pie chart with industry names as labels

```
plt.figure(figsize=(8, 8))  # Adjust the figure size as needed
pie, texts, autotexts = plt.pie(valuation, labels=industries, colors= colors, explode=explode, autopct='%1.1f%%', startangle=90)
```
customize the label colors

```
for text, autotext in zip(texts, autotexts):
    text.set(color='black', fontsize=14, fontweight='bold')
    autotext.set(color='white', fontsize=14, fontweight='bold')
```
    
add a title

```
plt.title('Top 5 Industries By Valuation', fontsize=16, fontweight='bold')
```

display the pie chart

```
plt.axis('equal')  # Equal aspect ratio ensures that the pie is drawn as a circle.
plt.show()
```
![image](https://github.com/Ugochukwuodinaka/Exploratory-Data-Analysis-of-Global-Unicorn-Companies/assets/157266999/630e8bf1-e2de-4d80-8cb6-ed9cf8bc1d15)

#### Observation and Summary:

The table presents the top 5 unicorn industries by valuation, showcasing the sectors with the highest cumulative valuations. Here are the key observations and a summary of the findings:

**Fintech** emerges as the highest-valued unicorn industry, with a staggering valuation of **$882 billion**. **Fintech** companies leverage technology to innovate and disrupt traditional financial services, including banking, payments, lending, and insurance. The high valuation of the fintech sector reflects the growing demand for digital financial solutions and the transformative impact of technology on the finance industry.

Following closely behind is the **Internet software & services industry**, with a valuation of **$595 billion**. This sector encompasses a wide range of internet-based software applications and services, including social media platforms, cloud computing services, and online marketplaces. The valuation reflects the immense value generated by companies that facilitate digital connectivity, communication, and commerce on the internet.

The **E-commerce & direct-to-consumer industry** ranks third in valuation, with a total worth of **$426 billion**. E-commerce and direct-to-consumer companies leverage online platforms and digital channels to sell products and services directly to consumers, bypassing traditional retail channels. The valuation underscores the significant growth and potential of online retail as consumers increasingly turn to digital channels for shopping and purchasing goods.

**Artificial Intelligence (AI)** occupies the fourth position with a valuation of **$377 billion**. AI companies develop technologies that enable machines to simulate human intelligence and perform tasks such as data analysis, automation, and decision-making. The valuation reflects the increasing adoption of AI across various industries, driving efficiency, innovation, and productivity enhancements.

The **Other** category encompasses a variety of industries not specifically listed, with a valuation of **$252 billion**. This category likely includes a diverse range of unicorn companies operating in sectors such as healthcare, transportation, energy, and logistics. Despite the lack of specificity, the valuation highlights the cumulative worth of unicorn companies in miscellaneous industries beyond those explicitly mentioned.

In summary, the table illustrates the significant valuation and impact of unicorn companies across various industries, showcasing the transformative power of technology and innovation in reshaping traditional business models and driving economic growth. The dominance of fintech, internet software & services, e-commerce, and AI underscores key trends shaping the modern economy, including digital transformation, online connectivity, and advancements in artificial intelligence. As unicorn companies continue to disrupt and innovate across industries, their influence on global markets and society at large is poised to grow even further in the years to come.

#### The Top 5 Countries with the Most Number of Unicorns
```
top5_countries = df.groupby('Country')['Company'].size().sort_values(ascending= False).head()
top5_countries
```
Creating a pie chart to visualize the top 5 Countries with the highest number of Unicorn Companies

extract the data for the doughnut pie chart
```
countries = top5_countries.index
company_counts = top5_countries.values
```
create the doughnut pie chart with percentage labels inside and black labels outside
```
plt.figure(figsize=(8, 8))  # Adjust the figure size as needed

wedges, texts, autotexts = plt.pie(
    company_counts,
    labels=countries,
    autopct='%1.1f%%',
    pctdistance=0.85,  # Adjust the percentage label position inside the pie
    wedgeprops={'width': 0.4},  # Control the width of the doughnut hole
    startangle=60,
)
```

customize the labels inside and outside the doughnut pie
```
for text, autotext in zip(texts, autotexts):
    text.set(color='black', fontsize=14, fontweight='bold')
    autotext.set(color='white', fontsize=14, fontweight='bold')
```

add a title
```
plt.title('Top 5 Countries With Most No. of Unicorn Companies', fontsize=15, fontweight='bold')
```

display the doughnut pie chart

equal aspect ratio ensures that the pie is drawn as a circle.

```
plt.axis('equal')  
plt.show()
```
![image](https://github.com/Ugochukwuodinaka/Exploratory-Data-Analysis-of-Global-Unicorn-Companies/assets/157266999/1348dc98-6374-4d6f-a034-0a51e3bc1c54)

#### Observation and Summary:

The table presents the top 5 countries with the most number of unicorn companies, highlighting the nations where unicorn ecosystems have flourished. Here are the key observations and a summary of the findings:

**United States** dominates the list with an impressive **562 unicorn companies**. As a global hub for innovation and entrepreneurship, the **United States** boasts a diverse and thriving startup ecosystem, fueled by access to capital, world-class universities, and a culture that celebrates risk-taking and innovation. Silicon Valley, in particular, is renowned for its concentration of technology companies and venture capital investment, making it a hotspot for unicorn creation.

**China** follows the United States with **173 unicorn companies**. **China's** rapid economic growth, large consumer market, and government support for innovation have contributed to the emergence of a vibrant startup scene, particularly in sectors such as technology, e-commerce, and fintech. Cities like Beijing, Shanghai, and Shenzhen have become major hubs for unicorn activity, attracting both domestic and international investment.

**India** ranks third with **65 unicorn companies**. **India's** burgeoning startup ecosystem is driven by a young and tech-savvy population, a growing middle class, and increasing internet penetration. Key sectors driving unicorn growth in **India** include e-commerce, fintech, healthcare, and education. Cities like Bangalore, Mumbai, and Delhi NCR are home to many of India's unicorn companies.

**The United Kingdom** occupies the fourth position with **43 unicorn companies**. **The UK's** startup ecosystem benefits from a combination of factors, including access to capital, world-class universities, and a supportive regulatory environment. London, in particular, has emerged as a leading global fintech hub, attracting unicorn companies in finance, technology, and other sectors.

**Germany** rounds out the top 5 with **26 unicorn companies**. Germany's strong industrial base, engineering expertise, and skilled workforce have laid the foundation for a thriving startup ecosystem. Berlin, Munich, and Hamburg are among the cities driving unicorn growth in sectors such as automotive, software, and e-commerce.

In summary, the table reflects the global distribution of unicorn companies, with the **United States** leading the pack by a significant margin, followed by **China, India, the United Kingdom,** and **Germany**. These countries represent key centers of innovation and entrepreneurship, where unicorn ecosystems have flourished due to a combination of factors such as access to capital, talent, market size, and supportive ecosystems. As the global startup landscape continues to evolve, these countries are likely to remain at the forefront of unicorn creation and innovation in the years to come.

#### The Top 5 Cities with the higest number of Unicorn Companies
```
top5_cities = df.groupby(['City'])['Company'].size().sort_values(ascending=False).head(5)
top5_cities
```
creating a horizontal barplot to show the Top 10 Cities with the highest concentration of Unicorn Companies 
```
plt.figure(figsize=(10, 6))  # Adjust the figure size as needed
sns.set_style("white")
custom_palette = sns.color_palette = ['#08306b', '#08519c', '#6F8FAF', '#0096FF', '#2171b5']

plt.figure(figsize=(12, 6))
sns.barplot(x='City', y='Company', data=top5_cities.reset_index(), palette= custom_palette, dodge=False)
```
add labels for the number of cities for each bar
```
for i in range(len(top5_cities)):
    plt.text(x=i, y=top5_cities.iloc[i]+1, s=top5_cities.iloc[i], ha='center', fontsize=11, fontweight= 'bold')

plt.title('Top 5 Cities with the Most Concentration of Unicorn Companies', fontsize=15, fontweight='bold')
plt.xlabel('Unicorn Cities', fontsize=10, fontweight= 'bold')
plt.ylabel('No. of Unicorn Companies', fontsize=10, fontweight= 'bold')

plt.show()
```
![image](https://github.com/Ugochukwuodinaka/Exploratory-Data-Analysis-of-Global-Unicorn-Companies/assets/157266999/1984ffa0-7f38-48c2-b61a-4b6971102385)

#### Observation and Summary:

The table presents the top 5 cities with the most number of unicorn companies, showcasing the urban centers where unicorn ecosystems have flourished. Here are the key observations and a summary of the findings:

**San Francisco** leads the list with an impressive **152 unicorn companies**. As the heart of Silicon Valley, **San Francisco** has long been synonymous with innovation and entrepreneurship, attracting startups and venture capital from around the world. The city's proximity to leading technology companies, prestigious universities, and a supportive ecosystem of investors and mentors has contributed to its status as a global hub for unicorn creation.

**New York** follows closely behind with **103 unicorn companies**. **New York City's** diverse economy, access to capital, and vibrant startup scene have propelled its growth as a major center for unicorn activity. The city's strengths in industries such as finance, media, e-commerce, and technology have fostered the development of unicorn companies across various sectors.

**Beijing** ranks third with **63 unicorn companies**. As the capital of China, **Beijing** is a key player in the country's rapidly expanding startup ecosystem. The city's dynamic economy, government support for innovation, and concentration of tech talent have made it a fertile ground for unicorn creation, particularly in sectors such as technology, e-commerce, and artificial intelligence.

**Shanghai** follows **Beijing** with **44 unicorn companies**. **Shanghai's** status as a global financial hub and its strategic location on China's eastern coast have attracted a diverse array of unicorn companies across industries such as finance, e-commerce, logistics, and technology. The city's modern infrastructure, international connectivity, and access to talent have fueled its growth as a unicorn hotspot.

**London** rounds out the top 5 with **34 unicorn companies**. As the capital of the United Kingdom, **London** is a leading global financial center and a hub for innovation and entrepreneurship. The city's diverse economy, world-class universities, and vibrant cultural scene have fostered a thriving startup ecosystem, attracting unicorn companies in finance, technology, e-commerce, and other sectors.

In summary, the table reflects the concentration of unicorn companies in key cities around the world, with **San Francisco** and **New York** leading the pack followed by **Beijing, Shanghai**, and **London**. These cities serve as epicenters of innovation and entrepreneurship, offering access to capital, talent, and a supportive ecosystem that fosters unicorn creation and growth. As the global startup landscape continues to evolve, these cities are likely to remain at the forefront of unicorn activity, driving innovation and economic growth in their respective regions.

#### Unicorn Companies Distribution Across Continent

Plotting a barplot

create a vertical barplot showing the top 8 companies that with the highest funding

```
unicorn_cont = df.groupby('Continent')['Company'].size().sort_values(ascending= False).head(10)
unicorn_cont

unicorn_cont = df.groupby('Continent')['Company'].size().sort_values(ascending=False).head(10)

plt.figure(figsize=(10, 6))
sns.countplot(x='Continent', data=df, order=unicorn_cont.index)
plt.title('Unicorn Companies Distribution Across Continents',fontsize=15, fontweight= 'bold')
plt.xlabel('Continent', fontsize=10, fontweight= 'bold')
plt.ylabel('No. of Unicorn Companies', fontsize=10, fontweight= 'bold')
```
add labels for the number of companies for each bar

```
for i in range(len(unicorn_cont)):
    plt.text(x=i, y=unicorn_cont.iloc[i]+1, s=unicorn_cont.iloc[i], ha='center', fontsize=10, fontweight= 'bold')

plt.show()
```
![image](https://github.com/Ugochukwuodinaka/Exploratory-Data-Analysis-of-Global-Unicorn-Companies/assets/157266999/6fac8733-8f36-42fb-9cad-48d95eb28f04)

#### Observation and Summary:

The table illustrates the distribution of unicorn companies across continents, providing insights into the geographic spread of unicorn ecosystems globally. Here are the key observations and a summary of the findings:

**North America** dominates the list with a significant presence of **589 unicorn companies**. This includes the United States and Canada, which are home to some of the world's largest and most dynamic startup ecosystems, particularly in cities like San Francisco, New York, and Toronto. The region's strengths in technology, finance, and innovation have contributed to its leading position in unicorn creation.

**Asia** follows **North America** with **310 unicorn companies**. **Asia's** rising prominence as a global economic powerhouse is reflected in its growing number of unicorn companies, particularly in countries like China and India. Cities like Beijing, Shanghai, Bangalore, and Singapore have emerged as key hubs for unicorn activity, driven by factors such as rapid urbanization, technological advancement, and government support for innovation.

**Europe** ranks third with **143 unicorn companies**. **Europe's** diverse startup ecosystem spans countries from the United Kingdom and Germany to Sweden and France. Cities like **London, Berlin, Stockholm, and Paris have cultivated vibrant entrepreneurial communities, attracting investment and talent from around the world. While Europe's unicorn ecosystem is smaller compared to North America and Asia, it continues to grow steadily, fueled by a culture of innovation and a strong tradition of entrepreneurship.

**South America** follows with 21 unicorn companies. While **South America's** unicorn ecosystem is relatively smaller compared to other continents, countries like Brazil and Argentina have seen the emergence of unicorns in sectors such as fintech, e-commerce, and transportation. Cities like São Paulo and Buenos Aires are leading centers for startup activity, driven by a growing middle class, increasing internet penetration, and a supportive regulatory environment.

**Oceania** and **Africa** have fewer unicorn companies, with 8 and 3 unicorns respectively. Despite their smaller numbers, countries like Australia and New Zealand in Oceania, and Nigeria and South Africa in Africa, have seen the emergence of unicorns in sectors such as fintech, e-commerce, and logistics. Cities like Sydney, Melbourne, Lagos, and Cape Town are emerging as hubs for innovation and entrepreneurship, attracting investment and talent from both domestic and international sources.

In summary, the table highlights the global distribution of unicorn companies across continents, showcasing the diversity and dynamism of startup ecosystems around the world. While North America and Asia lead in terms of the sheer number of unicorn companies, Europe, South America, Oceania, and Africa also play important roles in driving innovation and economic growth through entrepreneurship. As the global startup landscape continues to evolve, the distribution of unicorn companies is likely to shift and expand, reflecting changing economic, technological, and social trends across regions.

#### Unicorn Companies Distribution across Industrie
```
company_spread = df.groupby('Industry')['Company'].size().sort_values(ascending= False).reset_index(name= 'Total Companies')
company_spread
```

Plotting a horizontal Barplot

```
plt.figure(figsize=(10, 6))
plt.barh(company_spread['Industry'], company_spread['Total Companies'])
plt.title('Unicorn Companies Distribution Across Industries', fontsize=14, fontweight= 'bold')
plt.xlabel('Total No. of Unicorn Companies', fontsize=10, fontweight= 'bold')
plt.ylabel('Unicorn Industries', fontsize=10, fontweight= 'bold')
plt.grid(False)
```
add labels for the number of companies for each industry

```
for i in range(len(company_spread)):
    plt.text(x=company_spread['Total Companies'][i], y=i, 
             s=company_spread['Total Companies'][i], ha='left', va='center', fontsize=10, fontweight= 'bold')

plt.show()
```
![image](https://github.com/Ugochukwuodinaka/Exploratory-Data-Analysis-of-Global-Unicorn-Companies/assets/157266999/6cd7e198-b3ad-45bb-86be-e77fa9612ccb)

#### Observation and Summary:

The table provides insights into the distribution of unicorn companies across various industries, shedding light on the sectors where unicorn ecosystems have flourished. Here are the key observations and a summary of the findings:

**Fintech** emerges as the leading industry, with a total of **224 unicorn companies**. **Fintech** companies leverage technology to innovate and disrupt traditional financial services, including banking, payments, lending, and insurance. The significant number of fintech unicorns underscores the growing demand for digital financial solutions and the transformative impact of technology on the finance industry.

**Internet software & services** follows closely behind, with **205 unicorn companies**. This industry encompasses a wide range of internet-based software applications and services, including social media platforms, cloud computing services, and online marketplaces. The abundance of unicorn companies in this sector reflects the pervasive role of the internet in modern life and the continued growth of digital platforms and services.

**E-commerce & direct-to-consumer** ranks third with **111 unicorn companies**. **E-commerce** and direct-to-consumer** companies leverage online platforms and digital channels to sell products and services directly to consumers, bypassing traditional retail channels. The popularity of e-commerce unicorns highlights the shift towards online shopping and the increasing importance of digital commerce in today's economy.

**Artificial Intelligence (AI)** occupies the fourth position with **84 unicorn companies**. AI companies develop technologies that enable machines to simulate human intelligence and perform tasks such as data analysis, automation, and decision-making. The emergence of AI unicorns underscores the growing adoption of AI across various industries, driving innovation and efficiency through intelligent automation and predictive analytics.

**Health:** Rounding out the top five with **74 unicorn companies**, the **health** industry includes companies operating in sectors such as biotechnology, pharmaceuticals, healthcare IT, and telemedicine. The presence of health unicorns reflects the increasing focus on healthcare innovation, personalized medicine, and digital health solutions to address global health challenges.

**Other:** This category includes a diverse range of industries not specifically listed, with **58 unicorn companies**. It likely encompasses sectors such as energy, real estate, and agriculture, among others. Despite the lack of specificity, the number of unicorn companies in this category highlights the broad range of opportunities attracting investment and innovation in various sectors.

**Supply chain, logistics, & delivery:** With **57 unicorn companies**, this sector focuses on optimizing supply chain operations, logistics management, and last-mile delivery services. The presence of unicorn companies in this industry underscores the importance of efficient logistics and delivery networks in supporting global trade and commerce.

**Cybersecurity:** Featuring **50 unicorn companies**, the **cybersecurity** sector addresses the growing threats posed by cyberattacks and data breaches. Unicorn companies in this industry develop innovative solutions to safeguard digital assets, protect sensitive information, and ensure the security of online transactions and communications.

**Data management & analytics:** With **41 unicorn companies**, this industry focuses on leveraging data to drive business insights, decision-making, and value creation. Unicorn companies in this sector develop advanced analytics tools, data visualization platforms, and data management solutions to help organizations unlock the value of their data assets.

**Mobile & telecommunications:** This industry, with **38 unicorn companies**, encompasses companies operating in mobile technology, telecommunications infrastructure, and wireless communication services. Unicorn companies in this sector drive innovation in mobile devices, network technologies, and digital connectivity, shaping the future of communication and connectivity.

**Hardware:** With **34 unicorn companies**, the hardware industry focuses on designing and manufacturing physical devices, electronics, and hardware components. Unicorn companies in this sector develop innovative hardware solutions for consumer electronics, IoT devices, and industrial applications, driving advancements in technology and engineering.

**Auto & transportation:** Featuring **31 unicorn companies**, this sector focuses on transforming the automotive and transportation industries through innovations in electric vehicles, autonomous driving technology, and mobility-as-a-service solutions. Unicorn companies in this industry are reshaping the future of transportation, promoting sustainability, safety, and efficiency.

**Edtech:** With **28 unicorn companies**, the **edtech** sector addresses the evolving needs of education and learning through technology-driven solutions. Unicorn companies in this industry develop online learning platforms, educational content, and digital tools to enhance access to quality education, promote lifelong learning, and drive educational outcomes.

**Consumer & retail:** This industry, with **25 unicorn companies**, focuses on meeting consumer needs and preferences through innovative products, services, and retail experiences. Unicorn companies in this sector disrupt traditional retail models, introduce new consumer products, and leverage technology to enhance the retail customer experience.

**Travel:** Rounding out the list with **14 unicorn companies**, the **travel industry** encompasses companies operating in travel booking, accommodation, transportation, and tourism services. Unicorn companies in this sector leverage technology to streamline travel planning, improve booking experiences, and enhance the overall travel journey for consumers.

In summary, the distribution of unicorn companies across industries reflects the diverse range of opportunities and challenges shaping the modern economy. From fintech and internet software to e-commerce, AI, and health, unicorn companies are driving innovation, disruption, and value creation across various sectors, shaping the future of business and society.

#### The Top 10 Select Investors that have invested the highest funds in Unicorn Companies
```
def format_funding(funding):
    if funding >= 1000000000:
        return f'${funding/1000000000:.1f}B'
    elif funding >= 1000000:
        return f'${funding/1000000:.1f}M'
    else:
        return f'${funding}'

top10_investors = df.groupby('Select Investors')['Funding'].sum().sort_values(ascending=False).head(10)
top10_investors = top10_investors.apply(format_funding)
top10_investors
```


# Create a Bar plot as a Table for Top 10 Select Investors by Funding

def format_funding(funding):
    if funding >= 1000000000:
        return f'${funding/1000000000:.1f}B'
    elif funding >= 1000000:
        return f'${funding/1000000:.1f}M'
    else:
        return f'${funding}'

top10_investors = df.groupby('Select Investors')['Funding'].sum().sort_values(ascending=False).head(10)
top10_investors = top10_investors.apply(format_funding)

Create a figure and axes for the table-like graph
```
fig, ax = plt.subplots(figsize=(8, 5))
```
create a bar plot as a table background

```
ax.axis('off')
ax.bar(0, 0, color='white')
ax.set_xlim(0, 1)
ax.set_ylim(0, 1)
```

create a table using the 'table' function

```
cell_text = []
for label, value in top10_investors.items():
    cell_text.append([label, value])

table = ax.table(cellText=cell_text, cellLoc='center', colLabels=['SELECT INVESTORS', 'FUNDING'])
```

style the table

```
table.auto_set_font_size(False)
table.set_fontsize(12)
table.scale(2, 2)  # Adjust the table size
plt.title("Top 10 Select Investors by Funding", fontsize=20, fontweight='bold')

plt.show()
```
### Top 10 Select Investors By Funding
![Unicorn 5](https://github.com/Ugochukwuodinaka/Exploratory-Data-Analysis-of-Global-Unicorn-Companies/assets/157266999/8406ccee-73d4-4adc-84a3-36e07a78db42)

#### Observation and Summary:

The table provides valuable insights into the top 10 select investors by funding, showcasing the investment firms and groups that have made significant contributions to unicorn companies through substantial funding rounds. Here's the observation and summary:

**Diverse Investor Landscape:** The list encompasses a diverse array of investors, including prominent venture capital firms, multinational corporations, and investment groups. This diversity reflects the broad spectrum of players involved in funding unicorn companies, ranging from traditional VC firms like **Sequoia Capital and Founders** Fund to corporate giants like **Tencent Holdings and Softbank Group**.

**Strategic Syndicates:** Several entries in the list feature syndicates of investors collaborating to fund unicorn companies. For instance, the second entry includes **Sequoia Capital China, SIG Asia Investments, Sina Weibo, and Softbank Group**, highlighting the strategic alliances formed by investors to leverage their combined resources and expertise in supporting high-growth startups.

**Global Reach:** The presence of investors from various regions underscores the global nature of unicorn funding. Investors like **Tiger Global Management, KKR,** and **Hillhouse Capital Management** operate on a global scale, providing capital to unicorn companies across different continents and industries, further enriching the global startup ecosystem.

**Significant Funding Amounts:** The funding amounts allocated by these investors are substantial, ranging from **$4 billion to $14 billion**. This underscores the immense financial backing required by unicorn companies to fuel their growth, scale operations, and compete in rapidly evolving markets.

**Strategic Investment Focus:** Each investor brings its unique investment thesis and strategic focus to the table. For example, **Tencent Holdings**, a leading Chinese conglomerate, strategically invests in technology and internet companies, while **Sequoia Capital China** focuses on early-stage investments in innovative startups.

**Impact on Unicorn Ecosystem:** Collectively, these top investors play a critical role in shaping the unicorn ecosystem, driving innovation, and facilitating the growth of disruptive startups. Their investments provide crucial capital, mentorship, and networking opportunities that enable unicorn companies to achieve their ambitious growth targets and disrupt traditional industries.

In summary, the top 10 select investors by funding represent a diverse and influential group of stakeholders that contribute significantly to the success and growth of unicorn companies worldwide. Their strategic investments, extensive networks, and deep pockets play a pivotal role in fueling innovation, driving market disruption, and shaping the future of the global economy.

#### The Top 10 Countries with the Most Select Investors
```
top10_investors = df.groupby(['Country'])['Select Investors'].size().sort_values(ascending= False).head(10)
top10_investors
```
Create a Bar plot for the Top 10 Countries with the most Select Investors
```
top10_investors = df.groupby('Country')['Select Investors'].size().sort_values(ascending=False).head(10)

plt.figure(figsize=(11, 6))
sns.countplot(x='Country', data=df, order=top10_investors.index)
plt.title('Top 10 Countries With The Most Select Investors', fontsize=14, fontweight= 'bold')
plt.xlabel('Country', fontsize=10, fontweight= 'bold')
plt.ylabel('No. of Select Investors', fontsize=10, fontweight= 'bold')
```
add labels for the number of companies for each bar

```
for i in range(len(top10_investors)):
    plt.text(x=i, y=top10_investors.iloc[i]+1, s=top10_investors.iloc[i], ha='center', fontsize=10, fontweight= 'bold')

plt.show()
```
![image](https://github.com/Ugochukwuodinaka/Exploratory-Data-Analysis-of-Global-Unicorn-Companies/assets/157266999/cf857f93-4eb9-4f54-b057-68804205e07b)

#### Observation and Summary:

The table highlights the top 10 countries with the most select investors, providing insights into the global distribution of investor activity and the geographic concentration of investment ecosystems. Here's the observation and summary:

**Dominance of the United States:** The **United States** leads the list by a significant margin, with **562 select investors**. This dominance underscores the country's status as the world's leading hub for venture capital and startup investment. With Silicon Valley as its epicenter, the U.S. boasts a robust ecosystem of investors, including venture capital firms, angel investors, corporate investors, and family offices, contributing to its vibrant startup culture and entrepreneurial spirit.

**Rise of China and India:** **China** and **India** follow the United States with **173** and **65 select investors**, respectively. Both countries have witnessed rapid economic growth and technological advancement in recent years, leading to the emergence of thriving startup ecosystems. Chinese investors, in particular, have played a pivotal role in funding the country's booming tech sector, while Indian investors have fueled the growth of India's burgeoning startup landscape, especially in sectors like e-commerce, fintech, and software development.

**European Representation:** The **United Kingdom, Germany, France**, and **Israel** represent Europe's strong presence in the global investment landscape. These countries have well-established startup ecosystems supported by a mix of government initiatives, academic research, and private sector investment. London, Berlin, Paris, and Tel Aviv serve as key hubs for investment activity, attracting both domestic and international investors looking to tap into Europe's diverse pool of talent and innovation.

**Emerging Markets:** **Brazil** and **South Korea** make the list, signaling the growing importance of emerging markets in the global investment landscape. Both countries have seen an uptick in venture capital investment in recent years, driven by increasing entrepreneurship, government support for innovation, and a rising middle class. Investors are drawn to the growth potential and untapped opportunities offered by these dynamic emerging economies.

**Canada's Contribution:** **Canada** rounds out the top 10 with **19 select investors**. While smaller in scale compared to the United States and China, Canada's startup ecosystem has seen steady growth, particularly in cities like Toronto, Vancouver, and Montreal. Canadian investors are actively supporting the country's burgeoning tech sector, investing in a wide range of industries including artificial intelligence, clean tech, and biotechnology.

In summary, the top 10 countries with the most select investors reflect the global distribution of investment activity and the diversity of startup ecosystems around the world. While the United States remains the dominant player in venture capital and startup funding, countries like China, India, and those in Europe are quickly gaining ground, fueled by a combination of innovation, entrepreneurship, and investor support. As the global economy continues to evolve, these countries are likely to remain key players in shaping the future of entrepreneurship and innovation on a global scale.

#### Unicorn Companies Trend By Year Joined

```
total_companies = df.groupby('Date Joined')['Company'].size().reset_index(name= 'Total Companies')
total_companies
```

Plotting a Line chart

extract year from the 'Date Joined' column

```
total_companies['Year'] = total_companies['Date Joined'].dt.year
```

sum the total companies by the year they joined

```
total_companies_by_year = total_companies.groupby('Year')['Total Companies'].sum().reset_index()
```

create a line plot

```
plt.figure(figsize=(12, 6))  # Adjust the figure size as needed
sns.set_style("white")
```

create the line plot
```
ax = sns.lineplot(x='Year', y='Total Companies', data=total_companies_by_year, marker='o', color='b', label='Total No. of Unicorn Companies')
```

add labels with the count on top of each data point

```
for index, row in total_companies_by_year.iterrows():
    ax.text(row['Year'], row['Total Companies'], f'{row["Total Companies"]}', ha='center', va='bottom', fontsize=10, color='black', fontweight= 'bold')
```
customize the plot

```
ax.set(xlabel="Year Joined", ylabel="Total Companies")
plt.title(" Unicorn Companies Trend By Year Joined", fontsize=14, fontweight= 'bold')

plt.show()
```
![image](https://github.com/Ugochukwuodinaka/Exploratory-Data-Analysis-of-Global-Unicorn-Companies/assets/157266999/8316f545-6391-43c2-9f4d-10cac0aeed61)

#### Observation and Summary:

The initial years when companies started becoming unicorns was preceded by a significant spark of innovation which birthed the first unicorn company, Veepee In 2007. Vice Media and Klarna became the second and third companies to become unicorns in 2011, followed by Trendy Group International, Space X, Fanatics and Avant all in 2012. A sudden surge was witness between 2014 and 2015 when 48 companies became unicorn. A slight slide downwards was happened in 2016 when 21 companies joined the unicorns which dropped from 35 in 2015. A commendable
growth was witnessed from 2017 when 44 companies joined the unicorns to 2018 when 103 companies also joined the billionaires club. 

The explosive growth and emergence of unicorn companies continued its steady rise in 2020 with 108 companies joining the unicorns to 2021 when it peaked at a mind-blowing 520. A sudden decline downwards was happened in 2022 when 116 companies joined the unicorn. The negative impact of the pandemic had a significant impact on this trend which slowed down consumer spending and this resulted to decreased investment.

The effect of this decline came as a result of increased volatility in the financial markets which made it more difficult for startups to raise capital. This resulted to a decrease in valuation. This massive surge in the emergence of unicorn companies across the globe can be attributed to technological advancement, favorable market conditions, and entrepreneurial zeal. This journey through the years of the emergence of unicorns is truly a testament to the unrelenting pursuit of transformative ideas shaping the future of businesses.

