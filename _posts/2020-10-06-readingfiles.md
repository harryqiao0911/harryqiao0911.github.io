---
layout: post
title: Reading Files

tags: [homework]
comments: true
---



# Code



```python
'''
## Objective
This homework will give you an idea of how to start the lab this week, as well as give you practice reading files with Python. We will do a lot of this together in class.

## Task
Write code that reads the attached `iris.csv`, and creates a dictionary where
  - each key is a species of iris
  - each associated value is a list of all petal-widths of that species
{
  'Iris-setosa': [2.1, 3.2, 4.5, etc... ],
  'Iris-versicolor': [1.1, 2.2, 3.3, 4.4, etc... ],
  'Iris-virginica': [3.1, 2.2, 1.3, etc... ]
}

## Hints
  * Create an empty dictionary before reading the file
  * Populate the dictionary while reading the file
  * Everything is read in as a String -- make sure to convert using float()!

## Submit
Turn in your Python file.
'''


import csv

petal_widths = {}
petal_widths["Iris-setosa"] = []
petal_widths["Iris-versicolor"] = []
petal_widths["Iris-virginica"] = []
print(petal_widths)


with open("iris.csv", "r") as f:
    data = csv.reader(f)
    for row in data:
        if row[4] == "Iris-setosa":
            petal_widths["Iris-setosa"].append(float(row[3]))
        elif row[4] == "Iris-versicolor":
            petal_widths["Iris-versicolor"].append(float(row[3]))
        elif row[4] == "Iris-virginica":
            petal_widths["Iris-virginica"].append(float(row[3]))
            
print(petal_widths)
```