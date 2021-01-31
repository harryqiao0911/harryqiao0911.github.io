---
layout: post
title: Descriptive Lab
tags: [labs]
comments: true
---

# Conclusion
In this lab, I worked with the COVID-19 vaccination dataset. The variables that I looked into are the ones that seemed the most interesting. In this lab, I analyzed variables such as daily vaccination and daily vaccination per million individually, and tried to find if there was a correlation between the number of people vaccinated and the number of people fully vaccinated. Although I am not a medical expert and not sure how the two are different, I hypothesized that there is a correlation, positive linear in particular, between the two variables. 

Let’s first look at daily vaccination and daily vaccination per million. Using the .describe() method we learned on the seaborn google docs, I was able to print the summary statistics easily, instead of using methods written by myself. These are the summary statistics of the two variables. 

![Summary Stats](/assets/img/dlab1)

After doing some research on seaborn API reference, I was able to find the plots I wanted to graph. Some graphs required seaborn 0.11.1, and I was able to install that version specifically on the terminal (actually did some research on how to do so). For these two variables, I graphed with violin plot and histogram. When I first started this project, I only did daily vaccination and found that the variable was very right skewed. The standard deviation and range were also very large. It makes sense, because there are not that many countries that have large populations as well as advanced technology or money to vaccinate a large number of people. Then I was thinking about how to eliminate the role of population. When I repeated the same process with the variable daily vaccination per million, I once again came to the conclusion that the dataset was also very right skewed with a very large standard deviation and range.

![Violin1](/assets/img/dlab2)

![Violin2](/assets/img/dlab3)

![Hist1](/assets/img/dlab4)

![Hist2](/assets/img/dlab5)

Then I looked at the relationship between the number of people vaccinated and the number of people fully vaccinated. I hypothesized that there was a positive linear relationship between the two variables. I decided to graph the two variables on a scatter plot with people fully vaccinated on the x axis and people vaccinated on the y axis. This way the slope of the best fit line would be a good estimate of how many people vaccinated were actually fully vaccinated. On seaborn API reference, there is a method that plot all the data points and draw a linear regression model fit. With the best fit line, the slope can be estimated to be 5.83. This means that for every 6 people vaccinated, 1 is fully vaccinated. Using methods written in the previous assignments, I found the correlation between the two variables to be 0.796, which means there is a somewhat positive linear relationship. 

![Scatter](/assets/img/dlab6)

![Best Fit](/assets/img/dlab7)

# Code
```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

covid_path = "country_vaccinations.csv"
covid_df = pd.read_csv(covid_path)
#print summary statistics
print(covid_df[['daily_vaccinations', 'daily_vaccinations_per_million']].describe())

#violin plot of daily vaccinations
_data = covid_df
sns.violinplot(data=_data, x='daily_vaccinations')

#violin plot of daily vaccinations per million
sns.violinplot(data=_data, x='daily_vaccinations_per_million')

#histogram of daily vaccinations
sns.histplot(data=_data, x='daily_vaccinations', bins=10)

#histogram of daily vaccinations per million
sns.histplot(data=_data, x='daily_vaccinations_per_million', bins=10)

#scatter plot people vaccinated vs people fully vaccinated
sns.scatterplot(data=_data, x="people_fully_vaccinated", y="people_vaccinated")

#scatter plot people vaccinated vs people fully vaccinated with best fit line
sns.regplot(data=_data, x="people_fully_vaccinated", y="people_vaccinated")

import csv

species_list = {}
with open("country_vaccinations.csv", "r") as f:
    data = csv.reader(f)
    next(data)
    covid_list = {'people_vaccinated':[], 'people_fully_vaccinated':[]}
    for row in data:
        #fill dictionaries with correspondings
        if(row[4] == ''):
            covid_list['people_vaccinated'].append(0)
        else:
            covid_list['people_vaccinated'].append(float(row[4]))
        if(row[5] == ''):
            covid_list['people_fully_vaccinated'].append(0)
        else:
            covid_list['people_fully_vaccinated'].append(float(row[5]))

#calculate the average of numbers in a list
def average_list(list):
    sum = 0
    for i in list:
        sum = sum + i
    sum = round(sum, 1)
    return round(sum / len(list), 3)

#return standard deviation in a list
def standard_deviation(list):
    avg = sum(list)/len(list)
    sq = 0
    for i in list:
        sq = sq + (i - avg)**2
    sd = (sq/(len(list)-1))**(1/2)
    return sd

# return correlation
def correlation(list1, list2):
    n = len(list1)
    sx = standard_deviation(list1)
    sy = standard_deviation(list2)
    mx = average_list(list1)
    my = average_list(list2)
    corr = 0
    for i in range(0,n):
        corr = corr + (list1[i] - mx)*(list2[i] - my)
    return (1/(n-1))*(1/(sx*sy))*corr

#print correlation
print("The correlation is "  + str(correlation(covid_list['people_vaccinated'],covid_list['people_fully_vaccinated'])))
```