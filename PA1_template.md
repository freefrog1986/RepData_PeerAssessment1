# Reproducible Research: Peer Assessment 1

## Loading and preprocessing the data

```r
unzip('activity.zip')
ori_data<- read.csv(file = 'activity.csv')
head(ori_data)
```

```
##   steps       date interval
## 1    NA 2012-10-01        0
## 2    NA 2012-10-01        5
## 3    NA 2012-10-01       10
## 4    NA 2012-10-01       15
## 5    NA 2012-10-01       20
## 6    NA 2012-10-01       25
```

## What is mean total number of steps taken per day?
Calculate the total number of steps taken per day and visualize the data by generating a histogram. 

```r
step_per_day<-with(ori_data,tapply(steps,date,sum,na.rm=TRUE))
par(mar=c(4,4,4,4))
hist(step_per_day, breaks=20,density = 10)
```

![](PA1_template_files/figure-html/unnamed-chunk-2-1.png)<!-- -->
Get the median of total number of steps taken per day.

```r
median(step_per_day)
```

```
## [1] 10395
```
Get the mean of total number of steps taken per day.

```r
mean(step_per_day)
```

```
## [1] 9354.23
```

## What is the average daily activity pattern?



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
