## Why 'R' Our Employees Leaving? - A Data Analysis with 'R'

<img src="images/HR Project/cover.png?raw=true"/>


**Project description:** 

For this project, I was analyzing data from a human resources dataset. There had been a recent increase in the number of people leaving the company, and I was tasked to find out why. 

### The Data

The original dataset came from IBM's human resources division, and can be found at [this link](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset). 

I used R as my tool for analysis because this project was focused on statistical analysis, and that is what R is best at. I could have also used Python or Excel, but the dataset is too large for Excel to do well, and Python, while a great language, is not as good as R for statistics.

**Exploration:**

My first step was to use a correlation matrix to explore the data to see if there was any sort of correlation. This could usually be done with scatter plots, but the correlation matrix in R makes it even easier by combining multiple scatterplots together. R makes the correlation matrix fairly easy with just this short bit of code:

```R
pairs(~MonthlyIncome+Age+TotalWorkingYears+Education,data=hrdata,main="Scatterplot Matrix")
```

The result is shown here:
<img src="images/HR Project/scatterplot.png?raw=true"/>


```python
print('this is the python code I used to solve this problem')
```

### 2. You can add any images you'd like. 

<img src="images/dummy_thumbnail.jpg?raw=true"/>


