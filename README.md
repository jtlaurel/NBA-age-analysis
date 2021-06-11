# NBA-age-analysis
A repository containing resources, processes and findings for my NBA age analysis.

## Motivation
NBA players sign multi-million dollar contracts every year. But how can we tell if the length and amount of these contracts are justified? This project will take a dive into how age affects performance in the National Basketball Association in an attempt to determine a 'peak' age and sort age groups by different performance metrics. 

## The Data
This is a public data set published at https://data.world/jgrosz99/nba-player-data-1978-2016 by Justin Grosz. It contains 17,709 rows and 109 columns and is saved as a .csv file. The data set contains every advanced statistic for every player each year from the years 1978-2016, as well as the number of games/minutes they played, their team, their age and their salaries.

## Exploratory Data Analysis
Upon examining the data after loading it into a pandas dataframe, we can see that there are a number of missing values(Picture?). Attempting to remove rows with missing values results in roughly 700 rows remaining, less than 5% of the original number of rows. To supplement this, we will look at how age trends with a few metrics using the groupby method(picture.)

As we can see, age does seem to possess some type of effect on these metrics. Another thing to consider is if these metrics are affected by time (write here). Most of these metrics take into account various others, such as PER. After this analysis we can narrow down our relevant features to three metrics to measure player performance, Player Efficiency Rating (PER), True Shooting Percentage (TS%), and Win Share per 48 Minutes (WS/48). These will measure overall player production, shooting ability, and win contributions respectively in an attempt to find a commonality on how age affects these various metrics.

## Cleaning the Data


