# Reproducible Research: Peer Assessment 1


# Set some global options:

tell chunks to be verbose and set the working directory:

```r
library("knitr")
opts_chunk$set(echo = TRUE )
opts_knit$set(base.dir = 'Assignement1/')
```

## Loading and preprocessing the data


use read.csv to read the data and use strptime to convert date coloumn into date format


```r
dat      <- read.csv(file = "activity.csv")
dat$date <- strptime(dat$date, format = "%Y-%m-%d")
```

## What is mean total number of steps taken per day?

###Calculate the total number of steps taken per day (ignoring NAs)
First get the number of days, then sum up the all steps and divide by number of days. NAs are ignored and considered zero steps.


```r
ndays <-  as.numeric(round (difftime( dat$date[length(dat[,2])] , dat$date[1], units = "days") + 1))
sum(dat$steps, na.rm = T)/ndays 
```

```
## [1] 9354.23
```

### show the number of steps per day in a histogram (i.e. the  graphical representation of the distribution of numerical data ([see wikipedia](https://en.wikipedia.org/wiki/Histogram))


```r
dat.aggr <-aggregate(steps ~ as.character(date), dat, sum)
hist(dat.aggr$steps, data = dat.aggr$date, breaks = 30, col = "red", xlab = "steps")
```

![](PA1_template_files/figure-html/plothist-1.png)<!-- -->


## What is the average daily activity pattern?



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
