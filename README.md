# Mod_3_Project

Using the European Soccer Database from Kaggle.com, Kal and I began to sift through the data and think of different hypotheses that could be relevant. After going through it all, the 4 hypotheses we decided to test were:

1) Does being a home team increase your odds of winning according to bookmakers?

2) Does having a higher defensive aggression result in a higher winning percentage?

3) Does having a good offense result in a higher winning percentage?

4) Does being a home team increase your odds of winning a match overall?


## Question #1: Does being a home team increase your odds of winning according to bookmakers?

The most obvious way we thought to do this was to take the odds from bookmakers when a specific team player another specific team at home, and then that team's odds against the exact same team when they played away. We decided that we would take the odds from the greatest team ever in order to test our hypothesis: Manchester City!

First, we extracted the odds given by 4 different sports book makers: Bet 365, Bet & Win, Interwetten, and Ladbrokes. We took that data and put it in a dataframe.

Next, we isolated the games where Manchester City was the Home Team and the Away Team and then merged all of those games onto another dataframe. After, we isolated the 2008/2009 season as a test because 1) it makes sense to compare odds in the same season, considering most variables (players, coaches, injuries, etc.) are similar and 2) a personal bias of mine, knowing that Manchester City did not have the best year in 2008/2009 and the odds would fluctuate a bit more.

Our first big block of code was to extract all the odds for each book. We ran a for loop that took the odds for Manchester City when it played a specific opponent at Home and Away. The loop placed each odd in a different list, but they were located in the same spot on the list, making it easier to compare.

Next, we created a distribution, shown below:

![Screen Shot 2019-06-11 at 10 38 14 AM](https://user-images.githubusercontent.com/48563446/59281306-0d8cd700-8c35-11e9-8cd1-731ccfbd6ccb.png)

The Blue area is the density for Manchester City home odds, and the orange is the density for their away odds. For reference, the lower the odds (x-axis), the higher the percent chance of winning the bookmakers believe Man City has. As you can see, their is a high density lower on the x-axis for the home odds relative to the away odds.

Our null hypothesis was that there is no difference between the odds when Manchester City is Home or Away, and our alternative hypothesis was that there is a difference between the odds when Manchester City is Home or Away.

We calculated the t-statistic and ran a two-sample t-test. The t-stat came out to be -3.06, and created a normal distribution curve where the rejection zone was outside of -3.06 and 3.06 on the x-axis.

We finally calculated our p-value to be 0.00416, proving that we can reject our null hypothesis and that there is a difference between home odds and away odds.

## Question #2: Does a higher defensive aggression result in a higher winning percentage?

We wanted to see if defense wins championships. To start, we grabbed the team attributes data from our database, which measured several defensive categories on a scale from 0-100.

Then, I had to take all the matches in the database and write code to sort out who won the game, how many games they won in the season, and what their winning percentage was.

We ran into a small problem with the data set, as a few times there were teams that went undefeated, and other teams that were counted twice in the data, so we had to make sure to clean it all to get clean results.

Once we had collected the winning percentage and the team attributes onto one dataframe, we ran correlation tests.

Our null hypothesis was that there is no relationship between defensive aggression and a higher winning percentage, and our alternative was that there is a relationship.

![Screen Shot 2019-06-11 at 10 56 46 AM](https://user-images.githubusercontent.com/48563446/59282899-a7558380-8c37-11e9-8446-be9014c5c682.png)

As you can see from the table above, there is very low correlation between winning% and defensive aggression. Furthermore, the p-value for this correlation was at 0.4996, proving that we could not reject our null hypothesis given this data.

![Screen Shot 2019-06-11 at 10 58 36 AM](https://user-images.githubusercontent.com/48563446/59283034-e4ba1100-8c37-11e9-8014-2b245aba8155.png)

As shown by the scatterplot above, it almost appears that the defensive aggression values given by FIFA are discrete and not as continuous as we originally believed. This is definitely a reason why the results are not significant whatsoever.

## Question #3: If defense doesn't win championships, does offense?

We essentially used the table created above to see if offense wins championships based on the three offensive categories of Chance Creation Passing, Chance Creation Crossing, and Chance Creation Shooting. For each category, our null hypothesis was that there is no relationship between winning% and that offensive category, and our alternative hypothesis was that there is a relationship.

After the results of Question #2, I expected that we would not be able to reject our null hypothesis. However, for both Chance Creation Passing and Chance Creation shooting, even though they had relatively low correlations at 0.216 and 0.200, respectively, their p-values were below 0.01, meaning that we could reject the null hypothesis and accept them as facts. However, Chance Creation Crossing had a low correlation at 0.11 and a higher p-value at 0.114, meaning we could not reject that null hypothesis.

## Takeaways:

* Sometimes, it is better to truly explore all paths within a dataset and not limit where you want to go.
* Google / Stack Overflow are your best friends.
* If we were to do this again, I'd want to take my own data from websites, because trusting other data sets that you haven't throughly checked can result in some problems.
