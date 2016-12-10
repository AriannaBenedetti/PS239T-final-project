# PS239T-final-project

## Short Description

In this project, I sought to understand the relationship between CEO-to-worker pay ratios and employee satisfaction and well being. In order to do so, I collected a dataset with CEO-to-worker pay ratios for several hundred companies on Glassdoor.com's Economic Research Blog. I then used a API get request with Python to pull employee ratings for each of these companies from Glassdoor's main site. 

Next, I loaded these datasets in R, merged and cleaned them. I removed any observations that did not have the same CEO between the compensation dataset and the ratings dataset. I then ran correlations betweeen CEO-to-worker compensation ratios and several employee ratings and visualized the relationships. Finally, I ran regressions on two variables that significantly correlated with CEO-to-worker pay ratios, controlling for potential confounding variables that may have affected the relationships. Findings indicate that when controlling for company size, profits, and number of Glassdoor ratings, CEO-to-worker compensation ratios are negatively related to employee ratings of Work/Life Balance and Compensation & Benefits.

## Dependencies

1. R, version 3.3.2
2. Python 3.5.2, Anaconda distribution.

## Files

### Data

1. 01_glassdoor_ceo_pay.csv: The Glassdoor compensation dataset, available here: https://www.glassdoor.com/research/ceo-pay-ratio/ (downloaded via Tableau and converted into a csv). Includes a list of 441 companies and their CEO, CEO pay, median worker pay, the ratio between two. Also has a company ID for each company, best used for merging. This list also includes data on company size and net profits as of Q4 2015, both collected by research assistants on Google Finance.
2. 02_glassdoor_ratings: Contains data from the Glassdoor API collected via 01_glassdoor_api_ratings.ipynb. Includes updated CEOs, company IDs, employee ratings of overall satisfaction, work/life balance, sr. leadership, compensation & benefits, career opportunities, culture and values, percent that approve of the CEO, percent that would recommend to a friend, number of Glassdoor ratings per company, and industry type.
3. 03_CEO_outliers.csv: A dataset saved for graphing a CEO-to-worker compensation ratio histogram that included outliers
4. 04_CEO_analyze: The final Analysis dataset derived from merging files 01 and 02 above. It includes all of the following variables: 
    - *id*: Company id used for merging data
    - *company*: Name of company
    - *industry*: Industry type
    - *ceo2015*: CEOs in 01_glassdoor_ceo_pay dataset
    - *ceo2016*: CEOs in 02_glassdoor_ratings dataset
    - *ceo_comp*: CEO compensation    
    - *median_comp*: Median worker compensation   
    - *ratio*: CEO-to-median-worker compensation ratio 
    - *numberOfRatings*: Number of Glassdoor Ratings  
    - *ceoratings*: Number of CEO ratings on Glassdoor     
    - *overall_2014*: Employee ratings of overall satisfaction ratings from 01_glassdoor_ceo_pay dataset on 1-5 Likert scale
    - *overall*: Employee ratings of overall satisfaction ratings from 02_glassdoor_ratings dataset on 1-5 Likert scale
    - *culturevalues*: Employee ratings of culture and values on 1-5 Likert scale 
    - *wlb*: Employee ratings of work/life balance on 1-5 Likert scale 
    - *careerops*: Employee ratings of career opportunities on 1-5 Likert scale  
    - *comp*: Employee ratings of compensation & benefits on 1-5 Likert scale  
    - *srleadership*: Employee ratings of Sr. leadership on 1-5 Likert scale  
    - *ceoPctApprove*: Percent of employees that approve of current CEO  
    - *rectofriend*: Percent of employees that would recommend the company to a friend   
    - *profits*: 2015 Year-end profits in thousands
    - *size*: 2015 Year-end company size
    - *ceo.match*: variable indicating whether ceo2015 and ceo2016 match (all match in the final dataset)  

### Code

1. 01_glassdoor_api_ratings.ipynb: Collects employee ratings data from Glassdoor API and exports data to the file 02_glassdoor_ratings.csv
2. 02_merge-clean_data.Rmd: Loads, cleans, and merges both Glassdoor datasets for the final analysis
3. 02_merge-clean_data.html: Knit HTML version of 02_merge-clean_data.Rmd
4. 03_analysis.Rmd: Conducts descriptive and quantitative analysis of the data, producing the tables and visualizations found in the Results directory
5. 03_analysis.html: Knit HTML version of 03_analysis.Rmd

### Results

1. 01_CEO_correlations.xlsx: Correlations between CEO-to-worker compensation ratios and all employee ratings variables. The first tab has the correlations and the second tab has the p-values.
2. 02_ratio-univariate-graphs.pdf: Two graphs showing histograms of the CEO-to-worker compensation ratio with and without outliers.
3. 03_wlb-comp-univariate-graphs.pdf: Two graphs showing histograms of work/life balance and compensation & benefits ratings.
4. 04_wlb-comp-scatterplot-graphs.pdf: Two scatterplots showing the relationships between CEO ratio and work/life balance and CEO ratio and compensation & benefits ratings.
5. 05_regressions.xlsx: Regression results for CEO ratio on work/life balance (tab 1) and compensation & benefits (tab 2) controlling for company size, profits, and number of Glassdoor ratings.


## More Information

Any questions? Please contact me at abenedetti@berkeley.edu.
