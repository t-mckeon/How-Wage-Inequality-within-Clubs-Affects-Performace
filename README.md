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

The wage data was normalized to the highest and lowest spenders in that league and season. The data was normalized to a scale of 1.0 to 101.0.

The second order of business is getting a sense of the distribution of the wage data. If we are going to run a linear regression analysis, we're going to need linear data. Let's take a look at the normalized wage data.

<img align="center" src="https://user-images.githubusercontent.com/105253832/172431603-d78ff498-b76b-4cbb-8087-0d01bdab83f7.png" width="640" height="400">


