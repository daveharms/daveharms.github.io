## Why 'R' Our Employees Leaving? - A Data Analysis with 'R'

<img src="images/HR Project/cover.png?raw=true"/>


**Project description:** 

For this project, I was analyzing data from a human resources dataset. There had been a recent increase in the number of people leaving the company, and I was tasked to find out why. 

### The Data

The original dataset came from IBM's human resources division, and can be found at [this link](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset). 

I used R as my tool for analysis because this project was focused on statistical analysis, and that is what R is best at. I could have also used Python or Excel, but the dataset is too large for Excel to do well, and Python, while a great language, is not as good as R for statistics.

**Exploration:**

My first step was to use a correlation matrix to explore the data to see if there was any sort of correlation. I didn't want all of the data though, just those things that might be relevant to job satisfaction and retention. I chose to use the following columns: age, daily rate, distance from home, education, hourly rate, monthly income, monthly rate, number of companies worked, total working years, and training time last year.

To create the correlation matrix, I used this code:
```R
hrdata[ , c("Age", "DailyRate", "DistanceFromHome", "Education", "HourlyRate", "MonthlyIncome", "MonthlyRate", "NumCompaniesWorked", "TotalWorkingYears", "TrainingTimesLastYear")]
```
This created a new, narrowed-down version of the dataset using just the columns that I wanted to look at. Next, I created the actual matrix using the cor function:

```R
cor(
hrdata[ , c("Age", "DailyRate", "DistanceFromHome", "Education", "HourlyRate", "MonthlyIncome", "MonthlyRate", "NumCompaniesWorked", "TotalWorkingYears", "TrainingTimesLastYear")]
)
```
Which returned this result:

<img src="images/HR Project/correlation.png?raw=true"/>

My next step was to visualize the items with a strong correlation. This could usually be done by creating multiple scatter plots, but R makes it even easier by combining multiple scatterplots together. R makes this fairly easy with just this short bit of code:

```R
pairs(~MonthlyIncome+Age+TotalWorkingYears+Education,data=hrdata,main="Scatterplot Matrix")
```

The result is shown here:
<img src="images/HR Project/scatterplot.png?raw=true"/>

As is expected, the correlation between the employee's age, number of years they have been employed, and salary have a positive correlation. It stands to reason that the older you are and the longer you've been in the workforce, the more you'll get paid. 

```python
print('this is the python code I used to solve this problem')
```

### 2. You can add any images you'd like. 

<img src="images/dummy_thumbnail.jpg?raw=true"/>


