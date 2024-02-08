# Exploratory-Data-Analysis-of-Global-Unicorn-Companies
![](images/Unicorn_image.jpg)

## Table of Contents
- [Project Overview](#project-overview)
- [Tools Used](#tools-used)
- [Dataset Overview](#dataset-overview)
- [Global Unicorn Companies Data EDA In Python](#global-unicorn-companies-data-eda-in-python)
- [Data Analysis and Visuals in Power BI](#data-analysis-and-visuals-in-power-bi)
- [Factors That Influences The Emergence of Unicorns](#factors-that-influences-the-emergence-of-unicorns)
- [Recommendations Towards The Growth of Unicorn Companies](#recommendations-towards-the-growth-of-unicorn-companies)
- [View Power BI Dashboard Report](#view-power-bi-dashboard-report)


## Project Overview
### Introduction:

The emergence of "unicorn" companies, private startups valued at over $1 billion, has reshaped the global economy and investment landscape. This data analysis project aims to explore the evolution, evolvement, and growth of these unicorns from 1919, marking the inception of the first unicorn, through to 2021. By analyzing historical data, trends, and significant events, this project seeks to provide insights into the factors contributing to the rise of unicorn companies and their impact on various industries and economies.

### Problem Statement
- What is the total valuation of Unicorns by 2022?
- What are tyhe total number of industries and unicorn companies in this analysis?
- Which companies are the most valued unicorns?
- Which countries host a majority of the unicorns?
- Which companies has the highest funding from investors?
- Which industries are the mostr valued?
- Which cities have the most concentration of unicorn companies?
- When was this Unicorn companies founded? Show a yearly trend.
- When did these companies emerge as unicorns? Show a yearly trend.
- What is the valuation trend of these companies?
- How are these unocorn companies spread across industries and locations?
  
#### Objectives:
- Determine the total valuation of unicorn companies by 2022.
- Identify the total number of industries represented by unicorn companies and quantify the total count of unicorn companies within this analysis.
- Rank and highlight the most valued unicorn companies based on their valuation metrics.
- Analyze and map the distribution of unicorn companies across countries to identify regions hosting the majority of unicorns.
- Identify and analyze the unicorn companies receiving the highest funding from investors.
- Evaluate and determine the most valued industries among unicorn companies.
- Utilize spatial analysis to identify cities with the highest concentration of unicorn companies.
- Present a yearly trend analysis showcasing the founding dates of unicorn companies to understand their emergence over time.
- Provide a yearly trend analysis illustrating the emergence of unicorn companies over time.
- Analyze the valuation trend of unicorn companies to identify patterns and fluctuations.
- Explore and visualize the distribution of unicorn companies across industries and locations to understand their spread and concentration dynamics.

### Tools Used
1. Python (Was used for Data Cleaning, profilling and Exploratory Data Analysis)
    - The following Python Features were incorporated:
        1. Jupiter Notebook
        2. Numpy
        3. pandas
        4. Visualization
             - Matplotlib
             - Seaborn
             - Plotly
        5. Integration With Other tools
           
2. Power BI (Was used to create reports and dashboard for this analysis)
    - The following Power BI Features were incorporated:
        1. Bookmarking
        2. DAX
        3. Quick Measures
        4. Page Navigation
        5. Modelling
        6. Filters
        7. Tooltips
        8. Button

### Methodology (Python):
- Data Collection: Gather historical data on unicorn companies from reputable sources.
- Data Cleaning and Validation: Ensure accuracy and consistency of the collected data through rigorous validation and cleaning processes.
- Descriptive Analysis: Perform descriptive statistics to analyze trends in the number of unicorn companies over time, geographical distribution, and industry sectors.
- Time Series Analysis: Utilize time series techniques to identify patterns, cycles, and fluctuations in unicorn company growth.
- Comparative Analysis: Compare the characteristics and performance of unicorn companies across different regions and industries.
- Regression Analysis: Conduct regression analysis to identify factors influencing the valuation and success of unicorn companies.

**Data Preprocessing:**
1. Convert the Funding Column from a "string" to a "float".
2. Define a custom function to convert the string to Decimal
3. Remove the '$' signs from the string
4. Extract the numerical part of the string
5. Get the last character to determine the scale (Billion or Million)
6. Multiply the numeric value based on the scale
7. Re-add back the '$' sign and return as a Decimal object

- Exploratory Data Analysis (EDA): Conduct EDA to gain insights into Global Unicorn Companies emergence, evolvement over the years, industries, funding, locations and valuation with line charts, bar charts, doughnut charts, pie charts, funnels and maps.

### Statistical Analysis:

- Calculate descriptive statistics, including mean, median, standard deviation, and correlation coefficients, to quantify Global Unicorn Companies valuation and funding trends over the years.

### Expected Findings:

- Growth Trajectory: A steep increase in the number of unicorn companies, especially in technology and finance sectors, with notable spikes following periods of economic growth and technological innovation.

- Geographical Distribution: Concentration of unicorn companies in tech hubs such as Silicon Valley, but with a rising presence in other regions globally, reflecting the globalization of entrepreneurship and venture capital.

- Industry Trends: Dominance of technology-related sectors, including e-commerce, fintech, and software, but also significant presence in healthcare, transportation, and energy industries.

- Funding Dynamics: Shifts in funding sources and strategies, from early-stage venture capital to late-stage private equity and crossover investments, influencing unicorn company valuations and exit strategies.

- Impact on Economy: Contribution of unicorn companies to job creation, wealth generation, and innovation, but also concerns about market concentration, regulatory challenges, and potential bubble risks.

### Dataset Overview
The primary dataset used in this analysis is the "Unicorn_Companies.csv" and "Data_Dictionary-1.csv" files. This dataset was released by [Quantum Analytics](https://www.quantumanalyticsco.org/). The Data Dictionary can be viewed or downloaded [here](Data_Dictionary.csv) while the main dataset can also be viewed and downloaded [here](Unicorn_Companies.csv). The main dataset is made up of data for Global Unicorn Companies from the founding of the first Unicorn  companyin 1919 to the year 2022. The Data Dictionary file gives an explanation of the fields in the main dataset. The main dataset has the columns: Company, Valuation, Date Joined, Industry, City, Country, Continent, Year Founded, Funding, and Select Investors.

The dataset contains 8 columns and 1,075 columns, here's a breakdown of what each column represents:

- Company: This column contains the names of the unicorn companies included in the dataset.

- Valuation: This column contains the valuation of each unicorn company, measured in terms of billion dollars ($1 billion or more), which represents the estimated worth of the company in the market.

- Date Joined: This column contains the date when each company achieved unicorn status, which means the date when their valuation exceeded $1 billion.

- Industry: This column contains the industry or sector to which each unicorn company belongs. It specifies the primary area of business or the market in which the company operates.

- City: This column contains the city where each unicorn company is headquartered or has a significant presence.

- Country: This column contains the country where each unicorn company is based or founded.

- Continent: This column contains the continent where each unicorn company's country is located.

- Year Founded: This column contains the year when each unicorn company was established or founded.

- Funding: This column contains information about the total funding raised by each unicorn company, which represents the cumulative amount of investment capital received from investors.

- Select Investors: This column contains the names of notable investors or investment firms that have provided funding to each unicorn company. It may include venture capital firms, private equity investors, or other institutional investors.


#### Conclusion:

The evolution of unicorn companies from 1919 to 2022 represents a transformative force in the global economy, reshaping industries, driving innovation, and attracting unprecedented levels of investment. By understanding the factors driving their growth and success, policymakers, investors, and entrepreneurs can better navigate the opportunities and challenges presented by the unicorn phenomenon. This analysis provides valuable insights into the past, present, and future of unicorn companies and their impact on the world economy.

## Global Unicorn Companies Data EDA In Python:

Top 10 Most Valued Unicorns                   | Top 8 Unocorns With Most Funding        
:--------------------------------------------:|:--------------------------------------------:|
![](images/Top_10_Most_Valuable_Unicorns.png) | ![](images/Top_8_Unicorn_With_Most_Funding.png)


Top 10 Countries With Most Select Inveastors               |Top 10 Select Investors By Funding 
:---------------------------------------------------------:|:------------------------------------------------------:|
![](images/Top_10_Countries_With_Most_Select_Investors.png)|![](images/Top_10_Select_Investors_by_Funding.png)  

Top 5 Cities With Most Unicorns Concentration                  |Top 5 Countries With Most Unicorms 
:-------------------------------------------------------------:|:--------------------------------------------------:|
![](images/Top_5_Cities_With_Most_Unicorn%20_Concentration.png)|![](images/Top_5_Countries_With_Most_Unicorns.png)


Top 5 Industries By Valuation                |Unicorns Distribution Across Industries 
:-------------------------------------------:|:----------------------------------------------------------------:|
![](images/Top_5_Industries_By_Valuation.png)|![](images/Unicorns_Distribution_Across_Industries.png)


Unicorns Trend By Year Founded                |Unicorns Trend By Year Joined 
:--------------------------------------------:|:----------------------------------------------------------------:|
![](images/Unicorns_Trend_By_Year_Founded.png)|![](images/Unicorns_Trend_By_Year%20_Joined.png)
 

To view the complete Exploratory Data Analysis (EDA) of this project in python Jupiter Notebook, please click [here](Unicorn_Companies_Exploratory_Data_Analysis.ipynb)

## Data Analysis and Visuals in Power BI:
![](images/Unicorn_Companies_Analysis_Project_Dashboard_page-%201.jpg)
![](images/Unicorn_Companies_Analysis_Project_Dashboard_page-%202.jpg)

1. From the dashboard, it is observed that the total Uunicorn Valuation as of 2022 is $3.711T 
2. The Total number of Unicorn Companies is 1074 and total number of industries is 15
3. For Location, the total number of Unicorn Cities is 257, while the number of Unicorns Countries is 46.
5. The top Unicorn Industries happens to be in the Tech Industry. The Fintech tops this list with 224 Unicorns, nternet Software & Services has 205, E-Commerce & Direct-To-Consumer has 111, while Artificial Intelligence has 84.
6. Bytedance sits at the top of the most valued Unicorns with a valuation of $180bn, Shein and SpaceX follows with $100bn, Stripe comes next with $95bn.
7. From 1 Company emerging as a Unicorn in 2007 to 2021 when the number of Companies that became Unicorns just in that same year peaked at 520. Factors that brought this this disruption can be attributed to advancement of technology of the global economy, the tech industries advantage, the edge of innovative startups, the prevailing market condition of that period and more.
8. 2022 saw a downward trend and a decline in the number of Companies that emerged as Unicorns with 112 Companies joining. This downward trend can be attributed to the negative effects of the pandemic which slowed down consumer spending and this resulted to decreased investment. The effect of this also came as a result of the volatility in the financial markets which made it difficult for startups to raise capital.
9. A complete PowerPoint Prentation in PDF of this project analysis can be viewed [here](EDA%20OF%20GLOBAL%20UNICORNS%20USING%20PYTHON%20-%20ODINAKACHUKWU%20UGOCHUKWU%20NNANNA.pdf)

## Factors That Influences The Emergence of Unicorns

**1. Timeline Variation:**
The emergence of a company into the league of unicorn companies can depend on factors such as their industry, their market conditions, their business model and the availability of funding.

**2 The Technology Advantage:**
In recent years, the technology sector have witnessed a speedy growth. Areas such as software development, e-commerce, internet services, and artificial intelligence have witnessed a rapid revolution, disruption and rapid development. Investors are more likely to invest in the technology sector.

**3 Innovative Startup Edge:**
The last decade have witnessed a surge in founding of a good number of innovative startups globally. This surge has also attracted a good number of investors into raising capital funding for these startups thereby helping many startups to hit and surpass the $1 billion mark.

**4 The Global Economy:**
With the rapid advancement of technology, the inter-connective nature of the global economy has been on a rapid rise and this have enhanced the growth of companies with the potential to emerge as unicorns. The ability to reach global audience, have access to international investors and take advantage of digital platforms for marketing and distribution has played a great role in making it possible for companies to achieve the unicorn status.

**5 Prevailing Market Conditions:**
Market and economic conditions plays a vital role. Periods of economic growth and increased investor confidence may be advantageous to companies by having easier access to funding which can aid their rapid growth towards attaining the status of a unicorn company.

## Recommendations Towards The Growth of Unicorn Companies
**1.Strategic Vision and Clarity:**
Maintain a clear and compelling vision for the company's future. This vision should guide strategic decisions, resonate with stakeholders, and inspire the team. Clearly define long-term goals and the path to achieving them

**2 Strategic Partnerships and Alliances:**
Explore strategic partnerships and alliances that can accelerate growth. Collaborating with complementary businesses, alliances with industry leaders, or entering into joint ventures can provide access to new markets, technologies, or resources.

**3 Scalability and Operational Efficiency:**
Ensure that the company's operations are scalable. Invest in technologies and processes that allow for efficient scaling without compromising quality. Operational excellence is vital for managing growth effectively.

**4 Data-Driven Decision-Making:**
Embrace data-driven decision-making. Leverage data analytics to gain insights into customer behavior, market trends, and internal operations. Informed decision-making can lead to more effective strategies and resource allocation.

**5 Financial Discipline:**
Maintain financial discipline and transparency. Implement robust financial management practices, monitor key performance indicators, and allocate resources strategically. Strong financial health is fundamental to sustaining growth.

**6 Global Expansion and Internationalization:**
Consider opportunities for global expansion. Unicorn companies often have the potential to operate on a global scale. Expanding internationally can unlock new markets, customer bases, and revenue streams.


## View Power BI Dashboard Report
Here’s a link to a [Dsshboard Report](https://app.powerbi.com/view?r=eyJrIjoiNTgxOTQ1N2QtM2RmOS00OTQzLWFiOTgtMTY4YjEwMzY4NTlmIiwidCI6IjdlYzI5NjU5LTNjZjItNGYzZi1hYmIzLWE3MjJlZGY3ZmYyZCJ9) I created in the second phase of this project. This dashboard report displays a vivid visual of this analysis on Global Unicorn Compoanies in Power BI Report.

