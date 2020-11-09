---
layout: post
title: Iris Lab
subtitle: My First Lab Assignment
tags: [labs]
comments: true
---

# My Process

In this lab, I found the average of all the final values of postfix expressions. In my code, I used the csv module, the Stack class I wrote in stack.py, variables, lists, and loops. In order to simplify the problem, I first wrote an evaluate method. The evaluate function takes a postfix expression and calculates the value the expression is equivalent to. Because I missed class on Monday, I searched up “postfix notation” and read the wikipedia entry on“Reverse Polish notation.” Because the operators associate with only the two operands before it, stack would be the perfect tool because it follows LIFO order. The idea that came to my mind was to create an empty stack. Everytime there is an operand, push that operand to the stack. Everytime there is an operator, pop the two operands on the top of the stack, perform the operation and push back the result. By using a for loop to repeat this process, the only number left in the stack would be the final answer. Using the csv module, I opened and read the calculate_me data set using the csv.reader() row by row. Since every row is read as a list, I could call on the evaluate function and evaluate row by row. In this lab, I also used the average_list function I wrote for the iris lab which finds the average of all the numbers in a list. To effectively use this method, I created an empty list, and appended the result row by row. Finally, after every row was read and evaluated, I called on the average_list function to get the final answer.

# Result

By using the function above, average of all the final values of postfix expressions: 529.91

# Generate Function
Because I finished the lab early, I had the chance to work on a generate function. My generate function has a parameter length, where users can generate a postfix expression of the length they want. In order to create a valid postfix expression, many constraints have to be considered. First, for a postfix expression that can yield one final result, it needs one more operand than operators. Second, starting from the left, at all times there need to be more operands than operators. Under these two constraints, I used loops, if statements, and the random module to make sure the postfix expression was valid and random.

# Code
```python
#import csv module and Stack Class from stack.py
import csv
from stack import Stack
import random


#evaluate a postfix expression, take a postfix expression and return a int
def evaluate(list):
    s = Stack([])
    for i in list:
        #if i is an operation symbol, pop the top two objects in stack to perform the operation and push the result
        #to the top of the stack
        #if i is a number, push the object to the top of the stack
        #because every row in this dataset has 7 numbers and 6 operations,
        #there is always one object left (final result) in stack when the loop complete
        if i == '+':
            popped_1 = int(s.pop())
            popped_2 = int(s.pop())
            s.push(popped_2 + popped_1)
        elif i == '-':
            popped_1 = int(s.pop())
            popped_2 = int(s.pop())
            s.push(popped_2 - popped_1)
        elif i == '*':
            popped_1 = int(s.pop())
            popped_2 = int(s.pop())
            s.push(popped_2 * popped_1) 
        else:
            s.push(i)
        #print(s)
    return s.peek()
#print(evaluate(['9', '6', '6', '+', '-', '4', '5', '10', '-', '1', '-', '+', '*']))


#find the average of numbers in a list
def average_list(list):
    sum = 0
    for i in list:
        sum = sum + i
    return(sum / len(list))


#read calculate_me.csv
#run evaluate for every row
result = []
with open("calculate_me.csv", "r") as f:
    data = csv.reader(f)
    for row in data:
        result.append(evaluate(row))
    #print(result)


#print final statement
print("The average of all the final values is " + str(average_list(result)) + ".")


#generate
def random_generate(length):
    if length % 2 == 0:
        return None
    else:
        postfix = []
        operand_count = 0
        operator_count = 0
        for i in range(0, length):
            #if the operand reach the max nummber can have, break the loop
            if operand_count == (length + 1) / 2:
                break
            #if the number of operand is not greater than the number of operator by 2
            #append a random number from 1 to 10 (operand)
            #because otherwise, a operator append would make this postfix expression invalid
            elif operand_count - 1 <= operator_count:
                postfix.append(random.randint(1, 10))
                operand_count = operand_count + 1
            #if the number of operand is greater than the number of operator by 2
            #the either random operator or random operand can be appended
            else: 
                value1 = random.randint(1,2)
                if value1 == 1:
                    postfix.append(random.randint(1, 10))
                    operand_count = operand_count + 1
                else: 
                    value2 = random.randint(1,3)
                    if value2 == 1:
                        postfix.append('+')
                        operator_count = operator_count + 1
                    elif value2 == 2:
                        postfix.append('-')
                        operator_count = operator_count + 1
                    elif value2 == 3:
                        postfix.append('*')
                        operator_count = operator_count + 1
        #after exiting the for loop, the list has all the operands it need
        #so the only thing left is to fill the rest wit
        while operator_count < (length - 1) / 2:
            value3 = random.randint(1,3)
            if value3 == 1:
                postfix.append('+')
                operator_count = operator_count + 1
            elif value3 == 2:
                postfix.append('-')
                operator_count = operator_count + 1
            elif value3 == 3:
                postfix.append('*')
                operator_count = operator_count + 1
                    
        return postfix 


#test method
print(random_generate(10))
for i in range(0,10):
    print(random_generate(9))
```
# Special Note

In terms of who I worked with, I worked individually on my code, but checked my final answer with Alexis. 

