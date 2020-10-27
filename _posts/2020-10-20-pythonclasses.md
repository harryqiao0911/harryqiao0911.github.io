---
layout: post
title: Python Classes

tags: [homework]
comments: true
---



# Code



```python
'''
A complete definition of the Point class.
A complete definition of the Triangle class.
Just translate from Java
A complete definition of a Polygon class, which can:
Hold any number of vertices
Calculate the area of the polygon
You can search for the formula online
Calculate the circumference of the polygon
Hint: You wrote a really useful method in Point!
'''


import numpy as np
import math

#define Point Class
class Point:
    #constructor
    def __init__(self, x, y):
        self.x = x
        self.y = y
    
    #function that find the slope of the line that connects the two points
    def slope(self, point_b):
        return (point_b.y - self.y)/(point_b.x - self.x)
    
    #function that find the distance between two point
    def distance(self, point_b):
        return math.sqrt((point_b.y - self.y)**2 + (point_b.x - self.x)**2)
    
    #function that find the determinant of the 2 by 2 matrix constructed using the coordinates of the two point
    def determinant(self, point_b):
        a = np.array([[self.x, self.y], [point_b.x, point_b.y]])
        return np.linalg.det(a)


#test class methods
horace = Point(10, 20)
mann = Point(0, 0)
print(horace)
print(mann.slope(horace))
print(mann.distance(horace))
print(mann.determinant(horace))


#define Triangle Class
class Triangle:
    #constructor
    def __init__(self, vertices):
        self.vertices = vertices


#define Polygon Class
class Polygon:
    #constructor
    def __init__(self, vertices): 
        #if point not in vertices:
            #vertices.append(Point(x,y))
        self.vertices = vertices
    
    #function that finds the area by adding all the determinants found using consecutive points
    #only works when the points are in clockwise or counterclockwise order
    def area(self):
        sum_determinant = 0
        for i in range(0,len(self.vertices)):
            sum_determinant = sum_determinant + self.vertices[i].determinant(self.vertices[(i+1)%len(self.vertices)])
        return abs(sum_determinant/2)
    
    #function that finds the circumference by adding the distance between consecutive points
    def circumference(self):
        sum = 0
        for i in range(0,len(self.vertices)):
            sum = sum + self.vertices[i].distance(self.vertices[(i+1)%len(self.vertices)])
        return sum


#test class method
a = Point(0, 0)
b = Point(10, 0)
c = Point(10, 10)
d = Point(0,10)
square = Polygon([a, b, c, d])
print(square.area())
print(square.circumference())
```