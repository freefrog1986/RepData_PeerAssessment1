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
hist(step_per_day,
     breaks=20,
     density = 10,
     xlab = 'Steps',
     main = 'Total number of steps taken each day')
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
Make a time serise plot below to show the pattern of daily average steps of the 5-minutes interval. The max value of steps is between 500 and 1000 intervals.

```r
inter_mean_step<-with(ori_data,tapply(steps,interval,mean,na.rm=TRUE))
xaxis<-unique(ori_data$interval)
plot(xaxis,
     inter_mean_step,
     type = 'l',
     xlab = 'time serise of one day',
     ylab= 'average number of steps',
     main = 'Average daily active pattren')
```

![](PA1_template_files/figure-html/unnamed-chunk-5-1.png)<!-- -->
The code below is to calculate the maximum number of steps in the inter_mean_step dataset. 

```r
df<-data.frame(time = unique(ori_data$interval), step = inter_mean_step)
max_step_time<-subset(df,step==max(df[,2]))$time
```
Across all the days in the dataset 835 interval contains the maximum number of steps on average.  

## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
