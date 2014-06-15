# Reproducible Research: Peer Assessment 1


## Loading and preprocessing the data


```r
data <- read.csv("activity.csv", colClasses=c("numeric", "Date", "numeric"))
splitData <- split(data$steps, data$date)
sums <- sapply(splitData, sum, rm.na=TRUE)
```
## What is mean total number of steps taken per day?
The mean and median is calculated next

```r
mean(sums, na.rm=TRUE)
```

```
## [1] 10767
```

```r
median(sums, na.rm=TRUE)
```

```
## [1] 10766
```

The following is a histogram of the total steps each day.

```r
require(ggplot2)
```

```
## Loading required package: ggplot2
```

```r
qplot(sums, binwidth=500, xlab="steps")
```

![plot of chunk unnamed-chunk-3](figure/unnamed-chunk-3.png) 


## What is the average daily activity pattern?

```r
plot.ts(data$interval, data$steps, xlab="Interval", ylab="Steps", xy.lines=TRUE)
```

![plot of chunk unnamed-chunk-4](figure/unnamed-chunk-4.png) 

## Imputing missing values
The number of rows with missing values.

```r
sum(is.na(data$steps))
```

```
## [1] 2304
```



## Are there differences in activity patterns between weekdays and weekends?
