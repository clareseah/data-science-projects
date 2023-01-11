# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 1: Standardized Test Analysis

## Problem Statement

Standardised test scores (SAT) are used as a benchmark for college admissions in the USA, where high school students are required to partake in a 3-hour examination based on various knowledge. However, due to the emergence of COVID-19 in early 2020, many restrictions were imposed to restrict the spread of the virus.

This project aims to study the participation rates of SAT from 2018 to 2021 and identify if there was an impact on SAT participation rates due to COVID-19.

## Data Dictionary

|Feature|Type|Dataset|Description|
|---|---|---|---|
|state|object|sat_combined.csv|Name of state|
|participation_18|float64|sat_combined.csv|2018 SAT Participation Rate|
|ebrw_18|int64|sat_combined.csv|2018 SAT Evidence-Based Reading and Writing Score|
|math_18|int64|sat_combined.csv|2018 SAT Math Score|
|total_18|int64|sat_combined.csv|2018 SAT Total Score|
|participation_19|float64|sat_combined.csv|2019 SAT Participation Rate|
|ebrw_19|int64|sat_combined.csv|2019 SAT Evidence-Based Reading and Writing Score|
|math_19|int64|sat_combined.csv|2019 SAT Math Score|
|total_19|int64|sat_combined.csv|2019 SAT Total Score|
|participation_20|float64|sat_combined.csv|2020 SAT Participation Rate|
|ebrw_20|int64|sat_combined.csv|2020 SAT Evidence-Based Reading and Writing Score|
|math_20|int64|sat_combined.csv|2020 SAT Math Score|
|total_20|int64|sat_combined.csv|2020 SAT Total Score|
|participation_21|float64|sat_combined.csv|2021 SAT Participation Rate|
|ebrw_21|float64|sat_combined.csv|2021 SAT Evidence-Based Reading and Writing Score|
|math_21|float64|sat_combined.csv|2021 SAT Math Score|
|total_21|float64|sat_combined.csv|2021 SAT Total Score|
|states|object|sat_abs.csv|Name of State|
|test_takers_2021|int64|sat_abs.csv|Total number of SAT takers in 2021|
|num_grads_2021|int64|sat_abs.csv|Total number of High School Graduates in 2021|
|test_takers_2020|int64|sat_abs.csv|Total number of SAT takers in 2020|
|num_grads_2020|int64|sat_abs.csv|Total number of High School Graduates in 2020|
|test_takers_2019|int64|sat_abs.csv|Total number of SAT takers in 2019|
|num_grads_2019|int64|sat_abs.csv|Total number of High School Graduates in 2019|
|state|object|covid_cases_20_22.csv|Name of State|
|tot_cases_20|int64|covid_cases_20_22.csv|2020 Total Number of Covid Cases|
|tot_cases_21|int64|covid_cases_20_22.csv|2021 Total Number of Covid Cases|
|tot_cases_22|int64|covid_cases_20_22.csv|2022 Total Number of Covid Cases|
|tot_deaths_20|int64|covid_cases_20_22.csv|2020 Total Number of Covid Deaths|
|tot_deaths_21|int64|covid_cases_20_22.csv|2021 Total Number of Covid Deaths|
|tot_deaths_22|int64|covid_cases_20_22.csv|2022 Total Number of Covid Deaths|

### Data Cleaning: 
General data cleaning processes:
- Checking of datatypes 
- Defining a function to rename and update columns using list comprehension
- Reseting index of dataframes after data is cleaned
- Merging dataframes into one combined dataframe using `.join()` 

SAT related datasets:
- Non USA states are removed
- Participation rates are changed from a string to float
- Ensured that there are no data abnormally - scores higher/lower than the max/min scores
- Renaming columns to be consistent

COVID related datasets:
- Non USA states are removed
- Irrelevant columns are dropped
- Number of cases and deaths are changed from a string to integer
- Filter for final data submission at end of year per state to create cleaned dataframe
- Map state abbreviations to state name
- Renaming columns to be consistent


### Brief Analysis: 
A negative correlation can be observed between SAT Participation rates and Total Scores.
An increasing trend is observed with participation rate from 2018 to 2020, but in 2021 participation rate had a sudden drop. 
We then further investigate whether COVID-19 was the cause of the rate in participation rate in 2021

### Conclusion and Recommendations
<b>Conclusion</b><br>
From the data, it can be observed that SAT Participation Rates dropped significantly in 2021 compared to 2020. <br>
We hypothesised that COVID-19 was the reason for the significant drop. However, no correlation between participation rates and COVID-19 cases can be found. 

Hence, COVID-19 could be the one of the factors affecting participation rates instead of the main causation of the decrease in participation rates. <br>

Other factors that could have caused SAT Participation Rates to drop in 2021:
- There was a higher number of COVID-19 cases recorded in 2021 which could compel students to forgo partaking in SAT/ACT test for the university admission
    - Based on the given dataset, 93% of the universities made SAT/ACT optional in 2021 college admissions due to COVID-19 restrictions and health concerns from the CDC
    - There are over 1000 accredited universities and colleges that do not require SAT or ACT results as part of the admission process. Hence students might decide not to take SAT if the colleges they're interested in do not require SAT scores.<sup>6</sup>

<b>Limitation</b><br>
- It is reported that COVID-19 has a bigger effect on those aged 30 and above. The COVID numbers that we have may be skewed towards the higher age group resulting in no clear relationships observed.<sup>5</sup>

<b>Recommendation</b><br>
- Further research should take into consideration the influence of other factors such as the median household income by state that may provide greater predictive power of SAT participation rates.
- This project is limited by the sample size as COVID-19 is a relatively new phenomenon, there are only 3 years of data available. Further research should be done in the following years in which COVID-19 is still prevalent.

### Data Sources:
1. 2020 SAT Scores: https://blog.prepscholar.com/what-is-the-average-sat-score
2. 2021 SAT Scores: https://soflotutors.com/blog/sat-scores-by-state/
3. Absolute SAT Participation Rate: https://reports.collegeboard.org/sat-suite-program-results
4. COVID-19 Total Cases & Death by State Over Time: https://data.cdc.gov/Case-Surveillance/United-States-COVID-19-Cases-and-Deaths-by-State-o/9mfq-cb36/data
5. Risk of COVID-19 Infection by Age Group: https://www.cdc.gov/coronavirus/2019-ncov/covid-data/investigations-discovery/hospitalization-death-by-age.html
6. Colleges Don’t Require SAT Or ACT In The US: https://www.uopeople.edu/blog/colleges-that-dont-require-sat-or-act/#:~:text=Standardized%20test%20scores%20were%20once,part%20of%20the%20admission%20process