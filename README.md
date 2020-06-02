# Jake's Visual Portfolio

Below are some of my past visuals, reports, and projects.

## Scraping & animating a basketball game using {rvest} & {gganimate} 

I visualized play-by-play data I scraped off [basketball reference](https://www.basketball-reference.com/boxscores/pbp/202003090UTA.html):

<p align="center">
  <img src="https://github.com/imjakedaniels/raptors_animation/blob/master/animations/Toronto Raptors_Utah Jazz-20200309.gif">
</p>

Data was scraped off this table using {rvest}. I cleaned and summarized the data using {dplyr} then custom styling with {ggtext} and {gganimate}.

<img src="https://github.com/imjakedaniels/raptors_animation/blob/master/play-by-play-data.PNG" width="800" height="400">

I got 1500 upvotes on Reddit for an earlier version of this chart: https://www.reddit.com/r/torontoraptors/comments/eemlz4/what_a_comeback_vs_dallas/

Notebook in [raptors_animation repository](https://github.com/imjakedaniels/raptors_animation)

## Bloomberg Climate Change Animation

Recreating a Bloomberg visualization on Climate Change with gganimate. Using a 5-year moving average to remove volatility on the label. Along with an annotation at the end of the gif. 

Article here: https://www.bloomberg.com/graphics/2015-whats-warming-the-world/

<p align="center">
  <img src="https://github.com/imjakedaniels/bloomberg_climate_animation/blob/master/animations/bloomberg_orginal.gif">
</p>

<p align="center">
  <img src="https://github.com/imjakedaniels/bloomberg_climate_animation/blob/master/animations/bloomberg_orbital.gif">
</p>

<p align="center">
  <img src="https://github.com/imjakedaniels/bloomberg_climate_animation/blob/master/animations/bloomberg_solar.gif">
</p>

<p align="center">
  <img src="https://github.com/imjakedaniels/bloomberg_climate_animation/blob/master/animations/bloomberg_volcano.gif">
</p>

<p align="center">
  <img src="https://github.com/imjakedaniels/bloomberg_climate_animation/blob/master/animations/bloomberg_greenhouse.gif">
</p>

Notebook (and moving version if yours doesn't replay) in [bloomberg_climate_animation](https://github.com/imjakedaniels/bloomberg_climate_animation) repo.

## COVID-19 Unemployment Spike

"Siri, show me what an outlier looks like." <br>
_"Sure, here is this week's chart of the US Unemployment Insurance Weekly Claims Report"_

<p align="center">
  <img src="https://github.com/imjakedaniels/covid_unemployment_spike/blob/master/visuals/ICSA_pandemic_spike.gif">
</p>

https://github.com/imjakedaniels/covid_unemployment_spike

## #BlackLivesMatter Interactive Web Page

Built an interactive Shiny App: https://imjakedaniels.shinyapps.io/blm_app/

I sampled tweets from the top 50 Twitter Trends every hour using {rtweet} since May 7th. I subset trends that included mentions of #BlackLives Matter, Police, and Racist.

I created an interactive Treemap using D3 through {d3treeR}, and a searchable datatable to highlight dates with lots of topics around these conversations, and the underlying context for each trend.

<p align="center">
  <img src="https://github.com/imjakedaniels/blm-trends/blob/master/BLM_app_view.gif">
</p>

https://github.com/imjakedaniels/blm-trends

## Animating 2020 daily average gas price in Toronto

Gas prices drop in response to COVID-19 consequences.

<p align="center">
  <img src="https://github.com/imjakedaniels/gasoline_toronto/blob/master/visuals/toronto_gas.gif">
</p>

https://github.com/imjakedaniels/gasoline_toronto/

## Animating Chatter throughout the course of a Leafs Game

I post these on r/Leafs subreddit. It uses TF-IDF to determine the most popular word on Twitter and Reddit every 2 minutes. 

I use {rtweet} to get tweets mentioning various keywords for the leafs (#TMLTalk, leafs, @MapleLeafs, #LeafsForever).
I use {PRAW} (a Python scraper for Reddit threads) to get the data off their official game-thread.

It leverages the @MapleLeafs twitter account for posting "game start" "goals" and "game end" timestamps so I can mix real time data with in-game events. This chart can work for any trending topic to show the change in conversation over time (Think over the course of Trump's speech, Conference, Hashtag). I also have an emoji only version :)

<p align="center">
  <img src="https://github.com/imjakedaniels/animated_leafs_graphs/blob/master/animations/twitter_reddit-leafs-tampa-bay-lightning-2020-03-10.gif">
</p>

Notebook in [animated_leafs repository](https://github.com/imjakedaniels/animated_leafs_graphs)

## Churn Management Program - Ryerson Capstone Project

This project aims to develop a statistically stronger classification model to predict customer churn compared to a standard, non-dimensionality-reduced, logistic-regression model.

**Part 1)** 
I will be splitting the data into subsets relating to Billing, Customer, CustService, Product, Operations and Service using R and exporting them by writing a script from MySQLWorkbench to a MySQL cloud-server hosted on AWS. 

```
DROP TABLE IF EXISTS Customer;
CREATE TABLE Customer (
churn int,
months int,       
uniqsubs int,      
actvsubs int,        
crdlscod VARCHAR(2),
asl_flag VARCHAR(1),         
prizm_social_one VARCHAR(1),
area VARCHAR(50),             
phones int,         
models int,   
truck int,
rv int,
own_rent VARCHAR(1),        
lor int,             
dwlltype VARCHAR(1),         
marital VARCHAR(1),         
adults int,
infobase VARCHAR(1),           
income int,          
numbcars int,   
HHStatin VARCHAR(1), 
dwllsize VARCHAR(1),     
forgntvl int,
ethnic VARCHAR(1),        
kid0_2 VARCHAR(1),            
kid3_5 VARCHAR(1),         
kid6_10 VARCHAR(1),         
kid11_15 VARCHAR(1),       
kid16_17 VARCHAR(1),         
Customer_ID VARCHAR(10),
PRIMARY KEY(Customer_ID)
);
LOAD DATA LOCAL INFILE  
'C:/Users/Jake/Documents/ryersoncapstone1/Customer_info.csv'
INTO TABLE Customer 
FIELDS TERMINATED BY ','
LINES TERMINATED BY '\n'
IGNORE 1 ROWS;
```

**Part 2)** 
I will connect to the server with R and pull the data for cleaning - handling NA, restructuring variables - to prepare it for Exploratory Analysis. With Weka I can leverage java-powered machine learning to return cluster analysis, decision trees and infogain from variables to better look at predictors of churn.


```
cn <- dbConnect(drv      = RMySQL::MySQL(), 
                username = "root", 
                password = Sys.getenv("MY_PASS"), 
                host     = Sys.getenv("MY_HOST"), 
                port     = 3306, 
                dbname   = "capstoneryersonMYSQL")

Billing <- dbGetQuery(cn, "SELECT * FROM Billing;")
Customer <- dbGetQuery(cn, "SELECT * FROM Customer;")
CustService <- dbGetQuery(cn, "SELECT * FROM CustServ;")
Operations <- dbGetQuery(cn, "SELECT * FROM Operations;")
Product <- dbGetQuery(cn, "SELECT * FROM Product;")
Service <- dbGetQuery(cn, "SELECT * FROM Service;")

tele_clean <- inner_join(Billing, Customer) %>%
  inner_join(CustService) %>%
  inner_join(Operations) %>%
  inner_join(Product) %>%
  inner_join(Service)

write_csv(tele, "tele.csv")
```

**Part 3)** 
I will reduce the dimensions of the data using techniques that look at reducing rows by normalizing the data into z-scores and removing those which test in the 99% confidence of being an outlier. I will reduce the number of variables in half with techniques which examine high multicolinearity, near-zero variance, low information-gain and low Boruta importance. This increases the accuracies while reducing the computation time required.

![Weka info-gain](https://github.com/imjakedaniels/ryersoncapstone/blob/master/3%20Dimensionality%20Reduction/Reduction%20Visuals/weka%20-%20infogain_importance.png?raw=true)

**Part 3)** 
I will reduce the dimensions of the data using techniques that look at reducing rows by normalizing the data into z-scores and removing those which test in the 99% confidence of being an outlier. I will reduce the number of variables in half with techniques which examine high multicolinearity, near-zero variance, low information-gain and low Boruta importance. This increases the accuracies while reducing the computation time required.

**Part 4)**
I will then train, validate and compare classification methods with R, using the following models: base R's Logistic Regression, Caret's 10-Fold Logistic Regression, Caret's Gradient Boost Machine, Weka's LogitBoost, Weka's Naive Bayes, and Weka's Random Forest models and evaluate the best model based on AUC, Lift and False-Positive Rate. I can then evaluate the projected revenue earned by my Churn Management Program which targets the top 5% of predicted-to-chun customers with a $50 rebate aimed to retain 30%. This is why a strong lift and low false-positive rate benefit the goal of the Churn Management Program. 
![Predictive Model Performances](https://github.com/imjakedaniels/ryersoncapstone/blob/master/4%20Modelling/model_metrics_comparison.PNG?raw=true "Predictive Model Performances")

Random Forest visual
![Final Model](https://github.com/imjakedaniels/ryersoncapstone/blob/master/4%20Modelling/final_model_visual.PNG?raw=true "Final Model")

Using this information, I will simulate ad-hoc reporting using Tableau. Ex. Studying behaviours of new home owners with a newborn child. As well, generate monthly earnings and demographics. More here: [Jake's Public Tableau](https://public.tableau.com/profile/jake.daniels#!/vizhome/SimpleChurnDashboard/ChurnSimpleDash)

![Churn DashBoard](https://github.com/imjakedaniels/ryersoncapstone/blob/master/Tableau%20Reports/Notable%20Examples/Simple%20Churn%20Dash.png?raw=true "Churn DashBoard")
![Equipment Age](https://github.com/imjakedaniels/ryersoncapstone/blob/master/Tableau%20Reports/Notable%20Examples/Equipment_Age.PNG?raw=true "Equipment Age")

This all will showcase my ability to optimize and compare classification models from different packages, utilize pre-built reporting tool (Tableau) to generate reports, design & interact with a cloud-based dataset by writing scripts and connections and cleaning & mutating a dataset in R.

### Results

The Churn Management Program is projected to retain $7,831,250 from a sample of 500,000 customers when offering a $50 rebate at 50c cost to communicate to the 5% likeliest-to-churn customer as predicted by our Random Forest Model at a 30% success rate. The success rate effectiveness will depend on the campaign (e-mail or telemarketing) incorporating friendlier trends into the offer to lower the customer's likelihood to churn. Ex. Increase their phone usage, tie the discount to monthly terms, or offer new product at reduced rate.

## [@laidoffbot](https://twitter.com/layoffbot) Unemployment Visual for Nick Swartz

Discovering dates of significance when people tweeted "I just got laid off" "I was just laid off".

<p align="center">
  <img src="https://github.com/imjakedaniels/layoffbot_timeseries/blob/master/covid_tracking_log10.png">
</p>

https://github.com/imjakedaniels/layoffbot_timeseries

## Physical Distancing Tickets in Toronto

Looking at how many and when people are penalized for not respecting social distancing.

<p align="center">
  <img src="https://github.com/imjakedaniels/physical_distance_tickets_toronto/blob/master/visuals/tickets_issued_plot.png">
</p>

https://github.com/imjakedaniels/physical_distance_tickets_toronto/

## Visualizing political discourse off Medium.com every week

Scraping articles tagged "politics" off Medium with a scraper I made. Tokenizing full-text off articles and using pairwise correlations to create node networks that present latent groupings of topics from that week. Below are from Jan 26th 2020 to Feb 1st 2020.

I believe Buttigieg had just won Iowa Caucus. Trump was dealing with impeachment. Joe Rogan endorsed Bernie. The UK officially Brexited.

### Trending Network

Size of text based on geometric mean clap generated on average by any articles containing the word.

<p align="center">
  <img src="https://github.com/imjakedaniels/visualizing_politics/blob/master/visuals/trending_politics_network%202020-01-26%202020-02-01%20.png">
</p>

### Volume Network

Size of text based on absolute mention volume.

<p align="center">
  <img src="https://github.com/imjakedaniels/visualizing_politics/blob/master/visuals/volume_politics_network%202020-01-26%202020-02-01%20.png">
</p>

## Animated Boomerang Charts

Inspired by Instagram's boomerang posts. I can create bar charts that behave similarly (just as cool maybe). They can show stark contrasts based on different attributes. Below compares survey responses from three locations.

<p align="center">
  <img src="https://github.com/imjakedaniels/boomerang_charts/blob/master/animations/residency_animation.gif">
</p>

# Summary

I like to get data from the wild and create unique visuals to tell the story. I love animations.

I mainly use R for scraping, cleaning and visualizing—but use SQL/Python if needed!
