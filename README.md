# Off-Platform Project: Reggie's Linear Regression

## Data Scientist: Analytics - Codecademy

### Overview

This project is slightly different than others you have encountered thus far on Codecademy. Instead of a step-by-step tutorial, this project contains a series of open-ended requirements which describe the project you’ll be building.

There are many possible ways to correctly fulfill all of these requirements, and you should expect to use the internet, Codecademy, and other resources when you encounter a problem that you cannot easily solve.

### Project Goals

Reggie is a mad scientist who has been hired by the local fast food joint to build their newest ball pit in the play area. As such, he is working on researching the bounciness of different balls so as to optimize the pit. He is running an experiment to bounce different sizes of bouncy balls, and then fitting lines to the data points he records. He has heard of linear regression, but needs your help to implement a version of linear regression in Python.

Linear Regression is when you have a group of points on a graph, and you find a line that approximately resembles that group of points. A good Linear Regression algorithm minimizes the error, or the distance from each point to the line. A line with the least error is the line that fits the data the best. We call this a line of best fit.

In this project, you’ll combine your knowledge of loops, lists, and arithmetic to create a function that will find a line of best fit when given a set of data.

### Tasks

#### Part 1: Calculating Error

1. The line we will end up with will have a formula that looks like:

```
y = m*x + b
```

where <code>m</code> is the slope of the line and <code>b</code> is the intercept, where the line crosses the y-axis.
Create a function called <code>get_y()</code> that takes in <code>m</code>, <code>b</code>, and <code>x</code>. It should return what the <code>y</code> value would be for that <code>x</code> on that line!
Once you have defined <code>get_y()</code>, test it out by uncommenting the <code>print()</code> statements and checking if the expected values display in the terminal.

2. Reggie wants to try a bunch of different <code>m</code> values and <code>b</code> values and see which line produces the least error. To calculate the error between a point and a line, he wants a function called <code>calculate_error()</code>, which will take in <code>m</code>, <code>b</code>, and an [x, y] point called <code>point</code> and return the distance between the line and the point.
First, define the function <code>calculate_error()</code>, passing <code>m</code>, <code>b</code>, and <code>point</code> as parameters.

3. To find the distance:

* Get the x-value from the point and store it in a variable called <code>x_point</code>
* Get the y-value from the point and store it in a variable called <code>y_point</code>
* Use <code>get_y()</code> to get the y-value that <code>x_point</code> would be on the line
* Find the difference between the y from <code>get_y()</code> and <code>y_point</code>
* Return the absolute value of the distance (you can use the built-in function <code>abs()</code> to do this)

The distance represents the error between the line <code>y = m * x + b</code> and the <code>point</code> given.

4. We have provided several test cases for <code>calculate_error()</code>. Uncomment each <code>print()</code> statement and check to see that it displays the expected value.

5. Great! Reggie’s datasets will be sets of points. For example, he ran an experiment comparing the width of bouncy balls to how high they bounce:

```
datapoints = [(1, 2), (2, 0), (3, 4), (4, 4), (5, 3)]
```

The first datapoint, <code>(1, 2)</code>, means that his 1cm bouncy ball bounced 2 meters. The 4cm bouncy ball bounced 4 meters.
As we try to fit a line to this data, we will need a function called <code>calculate_all_error()</code>, which takes <code>m</code> and <code>b</code> that describe a line, and <code>points</code>, a set of data like the example above.
<code>calculate_all_error()</code> should iterate through each point in points and calculate the error from that point to the line (using <code>calculate_error()</code>). It should keep a running total of the error, and then return that total after the loop.

6. We have provided several test cases for <code>calculate_all_error()</code>. Uncomment each <code>print()</code> statement and check to see that it displays the expected value.

7. Great! It looks like we now have a function that can take in a line and Reggie’s data and return how much error that line produces when we try to fit it to the data.

Our next step is to find the <code>m</code> and <code>b</code> that minimizes this error, and thus fits the data best!

#### Part 2: Try a bunch of slopes and intercepts!

8. The way Reggie wants to find a line of best fit is by trial and error. He wants to try a bunch of different slopes (<code>m</code> values) and a bunch of different intercepts (<code>b</code> values) and see which one produces the smallest error value for his dataset.

Using a list comprehension, let’s create a list of possible <code>m</code> values to try. Make the list <code>possible_ms</code> that goes from -10 to 10 inclusive, in increments of 0.1.

9. Now, let’s make a list of <code>possible_bs</code> to check that would be the values from -20 to 20 inclusive, in steps of 0.1.

10. We are going to find the smallest error. First, we will make every possible <code>y = m * x + b</code> line by pairing all of the possible <code>m</code>s with all of the possible <code>b</code>s. Then, we will see which <code>y = m * x + b</code> line produces the smallest total error with the set of data stored in <code>datapoints</code>.

First, create the variables that we will be optimizing:

* <code>smallest_error</code> — this should start at infinity (<code>float("inf")</code>) so that any error we get at first will be smaller than our value of <code>smallest_error</code>
* <code>best_m</code> — we can start this at <code>0</code>
* <code>best_b</code> — we can start this at <code>0</code>

11. We want to:

* Iterate through each element <code>m</code> in <code>possible_ms</code>
* For every <code>m</code> value, take every <code>b</code> value in <code>possible_bs</code>
* If the value returned from <code>calculate_all_error()</code> on this <code>m</code> value, this <code>b</code> value, and <code>datapoints</code> is less than our current <code>smallest_error</code>,
* Set <code>best_m</code> and <code>best_b</code> to be these values, and set <code>smallest_error</code> to this error.

12. By the end of these nested loops, the <code>smallest_error</code> should hold the smallest error we have found, and <code>best_m</code> and <code>best_b</code> should be the values that produced that smallest error value.

Print out <code>best_m</code>, <code>best_b</code> and <code>smallest_error</code> after the loops.

#### Part 3: What does our model predict?

13. Now we have seen that for this set of observations on the bouncy balls, the line that fits the data best has an <code>m</code> of 0.4 and a <code>b</code> of 1.6:

```
y = 0.4x + 1.6
```

This line produced a total error of 5.

Using this <code>m</code> and this <code>b</code>, what does your line predict the bounce height of a ball with a width of 6 to be? In other words, what is the output of <code>get_y()</code> when we call it with:

* <code>m</code> = 0.4
* <code>b</code> = 1.6
* <code>x</code> = 6

14. Our model predicts that the 6cm ball will bounce 4.0m.

Now, Reggie can use this model to predict the bounce of all kinds of sizes of balls he may choose to include in the ball pit!