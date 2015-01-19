---
title: "Problem Set #2: MVIS 5301"
author: "C. Todd Lombardo"
date: "16 January 2015"
output: html_document
--- 

This work can also be found online at: <http://rpubs.com/ctodd/PS2> 

***
###1. Suppose the amount of money earned by all MICA graduates from speaking engagements is normally distributed with a mean of $4,040 and a standard deviation of $510. What percentage of MICA graduates earn between $4,000 and $4,500 on speaking engagements?  

> To find this, we will calculate the Z values at $4,000 and $4,500, then use the z-lookup tables to get the area under the curve between those Z values.  
> The formula to calculate ``Z = (Xi - Xbar) / s`` We have been given s, Xi and Xbar


```r
# Z = (Xi - Xbar) / s
s = 510
x4000 = 4000
x4500 = 4500
Xbar = 4040

Z4000 = (x4000-Xbar)/s
Z4500 = (x4500-Xbar)/s

Z4000
```

```
## [1] -0.07843137
```

```r
Z4500
```

```
## [1] 0.9019608
```

> The area of a normal distribution curve between z = 0.902 and z = -0.0784 is 0.8159 (@ Z= 0.90) minus 0.4681 (@Z = -0.08).  


```r
0.8159 - 0.4681
```

```
## [1] 0.3478
```

> Therefore, 34.8% of MICA graduates earn between $4,000 and $4,500 for speaking engagements.


***
###2. Find the confidence intervals for the following.

	A --> x̅ = 20, n = 36, σ = 3, confidence interval = 95%
	B --> x̅̅ = 25, n = 36, σ = 3, confidence interval = 95%
	C --> x̅̅ = 30, n = 25, σ = 4, confidence interval = 90%
	D --> x̅̅ = 50, n = 16, σ = 5, confidence interval = 99%

> Formula for Confidence Interval: CI = x̅ ± Z(σ/√n)  
90% CI Z value = 1.645  
95% CI Z value = 1.96  
99% CI Z value = 2.575  


```r
# A -- x̅ = 20, n = 36, σ = 3, confidence interval = 95%
20 + 1.96 * (3/sqrt(36))
```

```
## [1] 20.98
```

```r
20 - 1.96 * (3/sqrt(36))
```

```
## [1] 19.02
```

```r
#   B -- x̅̅ = 25, n = 36, σ = 3, confidence interval = 95%
25 + 1.96 * (3/sqrt(36))
```

```
## [1] 25.98
```

```r
25 - 1.96 * (3/sqrt(36))
```

```
## [1] 24.02
```

```r
# C -- x̅̅ = 30, n = 25, σ = 4, confidence interval = 90%
30 + 1.645 * (4/sqrt(25))
```

```
## [1] 31.316
```

```r
30 - 1.645 * (4/sqrt(25))
```

```
## [1] 28.684
```

```r
# D -- x̅̅ = 50, n = 16, σ = 5, confidence interval = 99%
50 + 2.575 * (5/sqrt(16))
```

```
## [1] 53.21875
```

```r
50 - 2.575 * (5/sqrt(16))
```

```
## [1] 46.78125
```



***
###3.  This question asks you to think about the directions of causality. Indicate the possible direction(s) of causality for the relationship between unemployment and the crime rate. Discuss your reasoning (a few sentences will suffice). Make sure to state clearly the assumptions you are making about the measurement of the construct (i.e., its operationalization) that may be important in justifying your choice.  

> Answer

***
###4.  There are 3 parts to this question:

x = c(1,1,5,5) 
y = c(1,3,2,4)

Line A: y = 1.5 + 0.5x  
Line B: y = 1.125 + 0.375x

a.  Graph the linear equations and data points

```r
x = c(1,1,5,5)        # Add the data to a vector
y = c(1,3,2,4)        
plot (x,y)                          # Plot the data
abline(1.5,0.5, col = 'blue')       # Line A in Blue
abline(1.125,0.385, col = 'green')  # Line B in Green
```

![](PS2_files/figure-html/unnamed-chunk-4-1.png) 

b.  Construct tables for x, y, ŷ, e, and e2;

> **Line A: y = 1.5 + 0.5x** 

x| y | yHat | e | e2 |
--------|--------|--------|--------|--------|
1 |1|2|-1|1|
1|3|2|1|1|
5|2|4|-2|4|
5|4|4|0|0|

 
> **Line B: y = 1.125 + 0.375x** 

x| y | yHat | e | e2 |
--------|--------|--------|--------|--------|
1|1.0|1.5|-0.5  |0.25
1|3.0|1.5|1.5	|2.25
5|2.0|3.0|-1.0	|1
5|4|3.0|1.0|1

c.	Determine which line fits the set of data points better, according to the least-squares criterion

> For Line A the sum of e2 = 6 and for Line B, the sum of e2 = 4.5, therefore Line B is considered the better fitting line for this dataset.

***

###5.  An instructor at Arizona State University asked a random sample of eight students to record their study times in a beginning calculus course. She then made a table for total hours studied (x) over 2 weeks and the test score (y) at the end of the 2 weeks. Here are the results.

x	10	15	12	20	8	  16	14	22  
y	92	81	84	74	85	80	84	80

The regression equation for these data is: ŷ = 94.86698 – 0.84561x.

a.	Graph the regression equation and the data points (if you use Excel, don’t simply use the “trendline” feature).

```r
x = c(10,15,12,20,8,16,14,22)         # Put data in to Vectors
y = c(92,81,84,74,85,80,84,80)
plot (x,y)                            # Plot the Data
regLine=lm(y~x)                       # R's Linear Model function: should be the same regression data given   
regLine                               # Call regLine to ensure slope and y-intercept are same
```

```
## 
## Call:
## lm(formula = y ~ x)
## 
## Coefficients:
## (Intercept)            x  
##     94.8670      -0.8456
```

```r
abline(regLine)                       # Plot the line on the graph
```

![](PS2_files/figure-html/unnamed-chunk-5-1.png) 

b.	Describe the apparent relationship between the two variables under consideration.  

> There appears to be a negative relationship between the variables: Longer hours of study is correlated with exam grade decrease.

c.	Interpret the slope of the regression line.

> Slope is in a negative direction; -0.84561.   

d.	What is the predicted exam score for a student who studies for 15 hours? 


```r
 # y = 94.86698 – 0.84561x
 # x = 15
94.86698 - 0.84561*(15)  # Thinking there should be a STD range callout here? since this is a predicted score?
```

```
## [1] 82.18283
```


###6. Read this article from Nate Silver at 538 <http://fivethirtyeight.com/datalab/killing-the-interview-could-cost-sony-100-million/> and write a paragraph about the potential sources of bias and error in the data and regression methodology. 
> Answer

