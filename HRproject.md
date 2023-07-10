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

**Analysis**

Once finished with exploration, I was presented with a problem. A former employee is suing the company because they believe that layoffs were influenced by ageism. They are claiming that older employees were being let go at a higher rate than younger employees. I will use a statistical analysis of the data to shut this accusation down.

First, I used boxplots to visualize the age distribution of people who were let go. I have included the code sample used:
```R
boxplot(Age~Attrition,data=hrdata, main= "Who Got Fired", xlab="Attrition", ylab="Age")
```
<img src="images/HR Project/attrition by age.png?raw=true"/>

This boxplot shows that the opposite of this claim is true. Younger people were actually let go more often than older people. But just a visual isn't enough. I wanted to show that there is a stastical significance to the data shown. This is where R really shines. I did a two sample T-test on the data to test my hypothesis that younger people were let go more often than older people. To do this, I had to separate the values of the Age column into yes and no based on whether they were let go or remained employed. Then, a very simple line of code runs the test, as shown:
```R
yes_age <- hrdata[(hrdata$Attrition == "Yes"),'Age']
no_age <- hrdata[(hrdata$Attrition != "Yes"),'Age']
t.test(yes_age, no_age)
```
My results:

<img src="images/HR Project/ttest.png?raw=true"/>

These results don't look pretty, but they show that there is a high probability that my hypothesis is correct. The p-value is 0.0000000138, which is much lower than the standard 0.05 p-value that says that my hypothesis is 95% certain to be correct. So much for that lawsuit.


Next, I was told that another disgruntled employee is saying that layoffs were just based on employee number. I ran the same tests as above, but substituted employee number for age. Here is the code used, and my results:

```R
boxplot(EmployeeNumber~Attrition,data=hrdata,main="Who Got Fired", xlab="Attrition", ylab="Employee ID Number")
```
Which produced this box plot:

<img src="images/HR Project/attrition by number boxplot.png?raw=true"/>

The average employee ID numbers, as indicated by the line in the shaded section of the boxes, are very close visually. To determine if there is any statistical significance, I ran the same hypothesis test as before with my new data:

```R
yes_number <- hrdata[(hrdata$Attrition == "Yes"),'EmployeeNumber']
no_number <- hrdata[(hrdata$Attrition != "Yes"),'EmployeeNumber']
t.test(yes_number, no_number)
```

Which produced these results:
<img src="images/HR Project/attrition by number t test.png?raw=true"/>



### 2. You can add any images you'd like. 

<img src="images/dummy_thumbnail.jpg?raw=true"/>


