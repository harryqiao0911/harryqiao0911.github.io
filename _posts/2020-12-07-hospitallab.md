---
layout: post
title: Hospital Lab
tags: [labs]
comments: true
---

# My Process

In this lab, I found which county in NY state has the most hospital beds per person using knowledge learned in class before and after we went remote. In my code, I obtained data using a web API, cleaned and prepared data for analysis. Specifically, I used the requests module and csv module, functions, dictionaries, lists, loops, and variables. First, I have to obtain the data from the given web API. Second, I have to write a csv file with the obtained raw data. Then, I have to clean and standardize the raw data. Last but not least, I have to analyze the data and find the NY county with the most beds per person. 

To make my code more generic, I wrote 4 functions. The first function is named pull, it takes “id” and pulls the “id”th row from the web API (very similar to what we did in class). The second function is named convert. Because the data obtained from the web API is plaintext instead of .json, I have to convert plaintext to a list. I achieve this by messing with the index where the commas appear. The third function is named standardize. It standardizes the number of beds to 1HAB by a simple division. This way, analysis is easier to perform. The last function is a summation function. Now that I am writing the blog post, I realize how stupid I was because of course there is a summation function written just like the max function. 

With these functions, it is much easier overall. To get the standardized csv file, I can use a loop to pull each line of data from the web API, convert to list, standardize, and write as a row in the csv file. To analyze this standardized csv file, I used a method that is very similar to my method for the iris lab. Because we want to find the county with the most beds per person regardless of bed type, I can create a dictionary with the name of the county as a label. For each dictionary label, I create a list and append all the beds per person. Then find the sum and append to the end of the list. I also created a list for the sums of hospital beds per person for each county, and used the max function to find the maximum. Then I found the dictionary label with the last element equal to this maximum and printed the label. 

### Stepbacks

There are way more setbacks in this lab than the previous ones. When I first started the lab, I couldn’t figure out the pull function because I didn’t know the data was not .json. When I tried to write the csv file, I first threw in full rows and just thought that it would work. It looked pretty good, except that it is really 1 column. That is why I wrote a convert function. I spent a lot of time on the convert function. I kept getting a list of only commas until I realized that I forgot to put one line inside a loop. In my analysis, when I tried to find the max in a list, I wrote a find_max function at first that uses recursion. Because there are quite a few terms in the list, the code compiles, but never finish running. I didn’t know what was causing the problem, so I had to run my code part by part. When I figured out what the problem is, I googled and found that there is a prewritten max function. 


# Result

By using the method above, my code shows that New York county has the most beds per person.

# Generate Function
My code shows that New York county has the most beds per person. I would not be surprised if this is the correct answer. In this lab, I deepened my understanding of how to obtain data from web API, how to clean and standardize data sets, and how to analyze. 

# Code
```python
import requests
import csv

url = "https://hm-cs.herokuapp.com/hospital"
key = "ArtOfDataKEY123"


#Pull a given row number from the API
def pull(id):
    payload = {'key': key,
        'id': str(id)
    }   
    response = requests.get(url, params=payload)
    if response.status_code == 200:
        data = response.text
        return data
    else:
        print("Error!!!")

#convert plain text to list
def convert(string):
    list = []
    index = 0
    for i in range(0,len(string)):
        if string[i:i+1] == ",":
            list.append(string[index:i])
            index = i+1
    list.append(string[index:])
    return list

#standardize measure by changing measure to 1HAB and adjust beds accordingly
def standardize(list):
    measure = int(list[4][:len(list[4])-3])
    list[5] = float(list[5])/measure
    list[4] = "1HAB"
    return list

#find sum of a list
def find_sum(list):
    s = 0
    for i in list:
        s = s + float(i)
    return s


#Pull all the data and write into hospital_lab_raw.csv
with open('hospital_lab_raw.csv', 'w', newline = '') as f:
    thewriter = csv.writer(f)
    for i in range(0,135):
        string = pull(i)
        row = convert(string)
        thewriter.writerow(row)
        
#Pull all the standardized data and write into hospital_lab.csv       
with open('hospital_lab.csv', 'w', newline = '') as f:
    thewriter = csv.writer(f)
    thewriter.writerow(convert(pull(0)))
    for i in range(1,135):
        string = pull(i)
        row = convert(string)
        standardized_row = standardize(row)
        thewriter.writerow(standardized_row)


#open hospital_lab.csv
county_list = {}
with open("hospital_lab.csv", "r") as f:
    data = csv.reader(f)
    next(data)
    for row in data:
        #organize data by county, regardless of bed type
        county = row[2]
        #create dictionary for new county
        if county not in county_list:
            county_list[county] = []
        county_list[county].append(row[5])


#create a list with the sum of beds/person for each county
bed_sum = []
for i in county_list:
    s = find_sum(county_list[i])
    county_list[i].append(s)
    bed_sum.append(s)


#find max and print result
maximum = max(bed_sum)
county = ""
for i in county_list:
    if county_list[i][len(county_list[i])-1] == maximum:
        county = i
print(county + " county has the most hospital beds per person")  
```

# Special Note

In terms of who I worked with, I worked individually on my code, but checked my final answer with Alexis. 