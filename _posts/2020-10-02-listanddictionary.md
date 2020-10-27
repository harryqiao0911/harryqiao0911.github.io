---
layout: post
title: Python Lists and Dictionaries

tags: [homework]
comments: true
---



# Code



```python
'''
This homework is a guided walk through lists and dictionaries.
Write your code underneath each instruction.

Scenario:
I'm coding an old arcade game, and I want a high-score screen at the end.
This requires me to keep track of all the scores!
'''

### Lists ###

#1) Create an empty list named high_scores

high_scores = []
print(high_scores)


#2) Add the score 100 to high_scores 3 times.
# high_scores should now contain 3 scores, each 100.

for i in range (0,3):
    high_scores.append(100)

print(high_scores)


#3) Change the 0th score to 73

high_scores[0] = 73
print(high_scores)


#4) Add 5 different scores between 0-100 to high_scores

for i in range (0,5):
    high_scores.append(95 + i)
    
print(high_scores)


#5) Print the length of high_scores

print(len(high_scores))


#6) Print the items from index 2 to index 5 of high_scores

print(high_scores[2:5])


#7) Delete the 0th element of high_scores

del high_scores[0]
print(high_scores)


#8) Print out all of the high_scores

print(high_scores)


#9) Complete this function, which returns the average of all the numbers
# in the list parameter
def average(list):
    sum = 0
    length = len(list)
    for i in range(0,length):
        sum = sum + list[i]
    return sum/length

print(average(high_scores))


# In[21]:


# CHALLENGE:
# Print out a sorted version of high_scores, with the highest scores first
high_scores.sort(reverse = True)
print(high_scores)


### Dictionaries ###
'''
A list is great for keeping track of the scores, but what if I want to also keep track of _who_ achieved each score? 
In other words, I want to associate a name with a score. A dictionary would be perfect for this!
'''
#1) Create an empty dictionary named named_scores

named_scores = {}
print(named_scores)


#2) Add the score 100 with the name "MrLee"

named_scores["MrLee"] = 100
print(named_scores)


#3) Change MrLee's score to 0

named_scores["MrLee"] = 0
print(named_scores)


#4) Add a score between 0-100 with your name

named_scores["HarryQiao"] = 98
print(named_scores)


#5) Print MrLee's score

print(named_scores["MrLee"])


#6) Delete MrLee's score

del named_scores["MrLee"]
print(named_scores)


#7) Add a few more scores! Whatever names you want

named_scores["Harry"] = 96
named_scores["Qiao"] = 94
print(named_scores)


#8) Print out all of the names and their scores

print(named_scores)


# CHALLENGE:
# Print out a sorted version of the high scores, so that
# the names with the highest scores come first
```