---
title: Investigating the exponential distribution and comparing it with the Central
  Limit Theorem
author: '@tribetect'
date: "August 18, 2015"
output: pdf_document
---

#Overview
In a few (2-3) sentences explain what is going to be reported on

We investigated the distribution of averages of 40 exponentials doing 1000 simulations.

#Simulations
 
 Include English explanations of the simulations you ran, with the accompanying R code. Your explanations should make clear what the R code accomplishes.
 
 
 
1. The exponential distribution was simulated in R with rexp(n, lambda) where lambda is the rate parameter. The mean of exponential distribution is 1/lambda and the standard deviation is also 1/lambda. 
2. Lambda was set = 0.2 for all of the simulations. 
3. Set number of simulations to 1000: variable, 'nosim'.



```r
my_seed = 512 #for random number generators based simulations
set.seed(my_seed) 

# Setup the supplied quantities as variables
lambda <- 0.2
samplesize <- 40 #size of random exponential samples 
nosim = 1000 #number of simulations
mns = NULL #variable to store means of samples
```
# Comparing Sample Mean and Theoretical Mean
We plot the distribution of a 1000 simulated means of sampletaken from an exponential distribution. Size of each sample was 40.

The theoratical mean of the distribution, shown using a vertical red line, is close to the center of the distribution of means of the samples.


```r
for (i in 1 : nosim) mns = c(mns, mean(rexp(samplesize, lambda)))
hist(mns, main = "Distribution of sample means")
theo_mean <- mean(mns)
abline(v = theo_mean, col = "red", lty = 2)
text(theo_mean - .5, y = 230, labels = paste("Theoretical Mean:", round(theo_mean,2)))
```

![](Part_1_files/figure-latex/unnamed-chunk-2-1.pdf) 



#Sample Variance versus Theoretical Variance
Include figures (output from R) with titles. Highlight the variances you are comparing. Include text that explains your understanding of the differences of the variances.

#Distribution
Via figures and text, explain how one can tell the distribution is approximately normal.

