---
layout: post
title: For Loop Review

tags: [homework]
comments: true
---



# Code



```python
for i in range(2):
    print (i, end="  ")


for i in range(1,5):
    print (i, end="  ")


for i in range(3,20,2):
    print (i, end="  ")


numIterations = 6
for i in range(numIterations):
    print (i, end="  ")


numIterations = 6
for i in range(1,numIterations+1):
    print (i, end="  ")


for i in range(100,201,2):
    print (i, end="  ")


for i in range(5,-1,-1):
    print (i, end="  ")


numbers = [1, 3, 5, 7, 9, 11]

for i in range(len(numbers)):
    print (numbers[i], end="  ")


for i in numbers:
    print (i, end="  ")
```