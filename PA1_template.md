---
title: "Reproducible Research: Peer Assessment 1"
output: 
  html_document:
    keep_md: true
---



## Loading and preprocessing the data

Let's start by loading the data from `data/activity.csv`.


```r
# Load data from CSV
data <- read.csv("data/activity.csv")
```

## What is mean total number of steps taken per day?

Load libraries, then calculate the sum of all steps taken in a day, before plotting the results in a histogram along with a summary (mean, median).


```r
# Load libraries
library(dplyr)
library(ggplot2)
```


```r
# Add all steps taken in a day together
total_day <- group_by(data,date)
total_day <- summarize(total_day, total_steps = sum(steps))

# Plot the resulting data
g <- ggplot(data = total_day,aes(x=total_steps)) + theme_bw()
g <- g + geom_histogram(binwidth=1000) 
g <- g + xlab("Number of steps taken per day") + ylab("Days count")
print(g)
```

![plot of chunk unnamed-chunk-3](figure/unnamed-chunk-3-1.png) 

```r
# Calculate mean and median and write to report
mean_steps <- mean(total_day$total_steps, na.rm = TRUE)
median_steps <- median(total_day$total_steps, na.rm = TRUE)
```

The mean number of steps per day is 10766.19 and the median is 10765.

## What is the average daily activity pattern?



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
