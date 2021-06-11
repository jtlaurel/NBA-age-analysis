# NBA-age-analysis
A repository containing resources, processes and findings for my NBA age analysis.

## Motivation
NBA players sign multi-million dollar contracts every year. But how can we tell if the length and amount of these contracts are justified? This project will take a dive into how age affects performance in the National Basketball Association in an attempt to determine a 'peak' age and sort age groups by different performance metrics. 

## The Data
This is a public data set published at https://data.world/jgrosz99/nba-player-data-1978-2016 by Justin Grosz. It contains 17,709 rows and 109 columns and is saved as a .csv file. The data set contains every advanced statistic for every player each year from the years 1978-2016, as well as the number of games/minutes they played, their team, their age and their salaries.

## Exploratory Data Analysis
### Initial Findings
Upon examining the data after loading it into a pandas dataframe, we can see that there are a number of missing values(Picture?). Attempting to remove rows with missing values results in roughly 700 rows remaining, less than 5% of the original number of entries. To account for this, we will look at how age trends with a few metrics using the groupby method(picture.)

As we can see, age seems to possess some type of effect on these metrics. Another thing to consider is if these metrics are affected by time (picture). We can see that while some statistics such as 3PAr and BLK% have a visible trend as the years pass, the rest of the metrics we are looking at have no visible trend. Lastly, most of these metrics, like PER and TS%, take into account various others metrics when being calculated. 

### Cleaning the Data
When exploring the data, entries within 2016 were notable in that they had incomplete game data for that season. We decided to remove this data as the nature of advanced stats tend to be more variant with small game sample sizes, this can lead to abursdly high and low numbers that aren't representative of a player's season-long performance.  We also narrowed down our columns to the features we plotted above and removed entires with missing values in this columns. This left us with 11,539 rows from the original data set. In addition, when grouping by age, the ages of 18 and 39+ had to few entries too show a meaningful distribution, so we narrowed our scope to ages with a sample size of 50 or greater.

### Relevant Metrics
After cleaning the data we can narrow down our relevant features to three metrics to measure player performance, Player Efficiency Rating (PER), True Shooting Percentage (TS%), and Win Share per 48 Minutes (WS/48). These will measure overall player production, shooting ability, and win contributions respectively in an attempt to find a commonality on how age affects these various metrics. 

## Analysis
### Distributions
We begin by taking a look at the distribution of these metrics(picture). We can clearly see that the distribution for our population is approximately normal for all three of these metrics. Since normal distributions are pretty typical for sums and averages, it is imporant to note that these metrics are in fact weighted sums of other metrics. (picture)

The following function was utilized during this process to make histograms in a timely fashion:
>```
>def plot_distribution(data,stat,ax):
>    if len(data) > 2500:
>        ax.hist(data[stat],bins = 50)
>    else:
>        ax.hist(data[stat],bins = int(len(data)**0.5))
>```

### Hypothesis Tests
For this experiment, we will attempt to see if there is a significant difference in the average performance level of a player between certain age groups.
We can state the following:

Null Hypothesis: There is NO difference in performance level for the relevant metrics between ages and age groups.
Alternative Hypothesis: There IS a difference in performance level for the relevant metrics between ages and age groups.

### Relevant Functions


### Process
Since the population is approximately normal and we are testing if there is a significant difference in the means of these statistics, we will utilize the T-test to determine if our null hypothesis can be rejected. However, since we are testing how an age or age group's mean performance is significantly different from a large number of other ages/age groups, it would be more appropriate to plot a p-value matrix. Utilizing a function for creating heatmaps, we produced three p-value 'heatmaps' for our relevant statistics. 

### Findings

Our heatmap for PER demonstrates that there is a large difference in player productivity at age 30. Looking on our earlier Age vs. PER plot verifies that this is associated with a decline in performance. In addition, younger players seem to perform closer to the median age of 26. (picture)

Our heatmap for TS% look much different. There are clearly defined age groups (represented by the light squares) in which the p-value is not rejected. This suggests some commonality in shooting performance within these clusters of ages. Similary to PER, however, we can note that there is a steep decline at around age 30.(picture)

Our heatmap for WS/48 demonstrates a different trend from the previous metrics. There is a large change in performance at age 23, but this instead is associated with an increase in performance. In addition, we can see that there that older players tend to perform more similarly to the median age.(picture)

### Conclusions

We can conclude that while there is not significant difference in player performance across every age specified in our range, there are distinct age groups that differ in overall performance to others. 
