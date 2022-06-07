# How-Wage-Inequality-within-Clubs-Affects-Performace

Hello. Welcome to my investigation into the impact of a team's wage bill size on their domestic league performance, as well as how wage inequality between players within a club affects performance. 

## Inquiry

<img align="right" src="https://user-images.githubusercontent.com/105253832/171916636-3a92388b-ad6b-41df-beb7-abe30c5c1987.jpeg" width="400" height="400">
The size of a team's wage bill obviously has a great impact on how well a team performs. If a team can afford to pay the best players, they will, and will enjoy success in their domestic league. This project will look into to what extent wage bills affect domestic performance, and whether wage inequality within clubs positively or negatively affects team performance. 

## Data



The data for this visualization comes from [Capology](https://www.capology.com/) and [theFishy](https://thefishy.co.uk/leaguetable.php). Capology has free wage data for the top 5 leagues, based on a "network of insiders" and a complex algorithm. theFishy is a website with a robust database of final league tables from leagues across the world. 
- [Here is my scraper for capology.com](https://github.com/t-mckeon/Soccer-Analytics-Scrapers/tree/main/Capology)
- [Here is my scraper for thefishy.co.uk](https://github.com/t-mckeon/Soccer-Analytics-Scrapers/tree/main/Fishy)

The excel files scraped from the websites are available in the Data Tab. 

## Process

After combining the wage and point tally data, the first order of business is to normalize the data for each league and season. For the point tally data, we convert the nominal point tallies into percentage of potential points. We do this because some leagues (namely the Bundesliga) do not follow the relatively standard 38 game schedule. The percentage of pontential points value also allows us to discern teams that did particularly well in a certain season (say Man City's 100 point season), instead of just normalizing to the league winning side. 

The wage data was normalized to the highest and lowest spenders in that league and season. The data was normalized to a scale of 1 to 101.

The second order of business is getting a sense of the distribution of the wage data. If we are going to run a linear regression analysis, we're going to need linear data. Let's take a look at the normalized wage data.

<img align="center" src="https://user-images.githubusercontent.com/105253832/172431603-d78ff498-b76b-4cbb-8087-0d01bdab83f7.png" width="640" height="400">

We can see that the normalized data is following a logarithmic distribution, with most of the teams falling below the 10th percentile of total wages and the number of teams decreasing rapidly as we approach the 100th percentile (with the exception of a jump at the end as the highest spending team in each league is placed at the 100th percentile). 

We can transform this data into a normal distribution by taking the natural log of the normalized wage data. The histogram below shows the results of the transformation.

<img align="center" src="https://user-images.githubusercontent.com/105253832/172435525-2dc1ecc2-45f3-4627-82b0-bd3b742d23fc.png" width="640" height="400">

This greatly improves our ability to perform linear regression analysis on the dataset, though we lose a lot of interpretability of the coefficients. Shown below are the scatterplots of the two wage datasets (normalized and logarithmic normalized) and percent of potential points on the y-axis, as well as fitted lines. 

<p float="left">
<img src="https://user-images.githubusercontent.com/105253832/172436427-2baa7b5c-cd00-4c70-8781-ac9be2f7a0e2.png" width="480" height="300">
<img src="https://user-images.githubusercontent.com/105253832/172436442-624a5b52-43b9-49b2-bf56-3eccb25082ac.png" width="480" height="300">
</p>

We'll be running regressions on this data soon, but first we need to grab the other variable we want to test - inequality among teams. We're going to test out a couple different measures of inequality to do so. 

#### Gini Coefficient

The Gini Coefficient is usually used to measure the levels of inequality seen within countries, where a high value represents large concentrations of wealth among a small portion of the population. See [here](https://en.wikipedia.org/wiki/Gini_coefficient) for a full explainaition. 

If the individual wage values of players are placed in descending order, the gini coefficient can be calculated by this equation. 

<img align="center" src="https://user-images.githubusercontent.com/105253832/172438942-98b540e3-4147-46d9-880d-c670d989e88a.png" width="640" height="400">


#### Galt Score

The Galt Score is simply the ratio of the salary of a company's CEO to the salary of the median worker. In our case, it is the salary of the top-paid player to the wage of the median player. This differs from the Gini Coeffecient as we are measuring if a single player can influence a team's performance with their high salary. 



