# Homework 4
Armand Post  
May 30, 2016  



## Write Bootstrap Code to illustrate the central limit theorem in R Markdown (normally distributed)
## Sample code was found at http://wiener.math.csi.cuny.edu/Statistics/R/simpleR/stat008.html



```r
print("This below Code illustrates the Central Limit Theorem using a normal distribution, the first with sample size of 100 and the second 1000.  The number of simulations = 200.")
```

```
## [1] "This below Code illustrates the Central Limit Theorem using a normal distribution, the first with sample size of 100 and the second 1000.  The number of simulations = 200."
```


```r
results = c();
mu = 0; sigma = 1
for(i in 1:200) {
    X = rnorm(100,mu,sigma)       # generate random data
    results[i] = (mean(X) - mu)/(sigma/sqrt(100))
    }
hist(results,prob=T,main=paste("Normally Distributed"),xlab = paste("sample size = 100"))
```

![](Homework4_files/figure-html/unnamed-chunk-2-1.png)<!-- -->


```r
results = c();
mu = 0; sigma = 1
for(i in 1:200) {
    X = rnorm(1000,mu,sigma)       # generate random data
    results[i] = (mean(X) - mu)/(sigma/sqrt(1000))
    }
hist(results,prob=T,main=paste("Normally Distributed"),xlab = paste("sample size = 1000"))
```

![](Homework4_files/figure-html/unnamed-chunk-3-1.png)<!-- -->


```r
print("From the above, as sample size becomes larger, the distribution narrows and outliers become less prevalent.")
```

```
## [1] "From the above, as sample size becomes larger, the distribution narrows and outliers become less prevalent."
```


```r
print("The below Code illustrates the Central Limit Theorem using exponential data, the first with sample size of 100 and the second 1000")
```

```
## [1] "The below Code illustrates the Central Limit Theorem using exponential data, the first with sample size of 100 and the second 1000"
```


## Write Bootstrap Code to illustrate the central limit theorem in R Markdown (Exponential Data)
## https://rpubs.com/a_inparadise/86939


```r
print("This below Code illustrates the Central Limit Theorem using exponential data, the first with sample size of 100 and the second 1000")
```

```
## [1] "This below Code illustrates the Central Limit Theorem using exponential data, the first with sample size of 100 and the second 1000"
```


```r
# lambda is 0.2
lambda = 0.2

# we will be using 100 exponentials
n = 100

# we will be running 1000 simulations
nsims = 1:1000

# set a seed to reproduce the data
set.seed(876)

# gather the means
means <- data.frame(x = sapply(nsims, function(x) {mean(rexp(n, lambda))}))

# lets take a looks at the top means
head(means)
```

```
##          x
## 1 4.840508
## 2 4.835966
## 3 5.142004
## 4 5.288703
## 5 4.819646
## 6 4.885118
```

```r
library(ggplot2)
print("histogram below is the exponential distribution for sample size of 100")
```

```
## [1] "histogram below is the exponential distribution for sample size of 100"
```

```r
ggplot(data = means, aes(x = x)) + 
  geom_histogram(binwidth=0.1, aes(y=..density..)) +
  labs(x="Means") +
  labs(y="Density")
```

![](Homework4_files/figure-html/unnamed-chunk-7-1.png)<!-- -->



```r
# lambda is 0.2
lambda = 0.2

# we will be using 1000 exponentials
n = 1000

# we will be running 1000 simulations
nsims = 1:1000

# set a seed to reproduce the data
set.seed(876)

# gather the means
means <- data.frame(x = sapply(nsims, function(x) {mean(rexp(n, lambda))}))

# lets take a looks at the top means
head(means)
```

```
##          x
## 1 4.883376
## 2 4.835791
## 3 4.753542
## 4 4.997895
## 5 5.201948
## 6 4.973431
```

```r
library(ggplot2)
print("histogram below is the exponential distribution for sample size of 1000")
```

```
## [1] "histogram below is the exponential distribution for sample size of 1000"
```

```r
ggplot(data = means, aes(x = x)) + 
  geom_histogram(binwidth=0.1, aes(y=..density..)) +
  labs(x="Means") +
  labs(y="Density")
```

![](Homework4_files/figure-html/unnamed-chunk-8-1.png)<!-- -->


```r
print("As before with the normally distributed data, as sample size increases, the exponential data's distribution becomes narrower.")
```

```
## [1] "As before with the normally distributed data, as sample size increases, the exponential data's distribution becomes narrower."
```

