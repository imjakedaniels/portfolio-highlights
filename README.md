# Jake's Porfolio

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

## Animating Chatter throughout the course of a Leafs Game

I post these on r/Leafs subreddit. It uses TF-IDF to determine the most popular word on Twitter and Reddit every 2 minutes. 

I use {rtweet} to get tweets mentioning various keywords for the leafs (#TMLTalk, leafs, @MapleLeafs, #LeafsForever).
I use {PRAW} (a Python scraper for Reddit threads) to get the data off their official game-thread.

It leverages the @MapleLeafs twitter account for posting "game start" "goals" and "game end" timestamps so I can mix real time data with in-game events. This chart can work for any trending topic to show the change in conversation over time (Think over the course of Trump's speech, Conference, Hashtag). I also have an emoji only version :)

<p align="center">
  <img src="https://github.com/imjakedaniels/animated_leafs_graphs/blob/master/animations/twitter_reddit-leafs-tampa-bay-lightning-2020-03-10.gif">
</p>

Notebook in [animated_leafs repository](https://github.com/imjakedaniels/animated_leafs_graphs)

## Bloomberg Climate Change Animation

Recreating a Bloomberg visualization on Climate Change with gganimate. Using a 5-year moving average to remove volatility on the label. Along with an annotation at the end of the gif. 

Article here: https://www.bloomberg.com/graphics/2015-whats-warming-the-world/

<p align="center">
  <img src="https://github.com/imjakedaniels/bloomberg_climate_animation/blob/master/animations/bloomberg_orginal.gif">
</p>

Notebook (and moving version if yours doesn't replay) in [bloomberg_climate_animation](https://github.com/imjakedaniels/portfolio-highlights/) repo.

## Visualizing political discourse off Medium.com every week

Scraping articles tagged "politics" off Medium with a scraper I made. Tokenizing full-text off articles and using pairwise correlations to create node networks that present latent groupings of topics from that week. Below are from Jan 26th 2020 to Feb 1st 2020.

I believe Buttigieg had just won Iowa Caucus. Joe Rogan endorsed Bernie. The UK officially Brexited.

### Trending Network

Based on geometric claps the articles containing each word generated on average.

<p align="center">
  <img src="https://github.com/imjakedaniels/visualizing_politics/blob/master/visuals/trending_politics_network%202020-01-26%202020-02-01%20.png">
</p>

### Volume Network

Based on mention volume.

<p align="center">
  <img src="https://github.com/imjakedaniels/visualizing_politics/blob/master/visuals/volume_politics_network%202020-01-26%202020-02-01%20.png">
</p>

## Animated Boomerang Charts

Inspired by Instagram's boomerang posts. I can create bar charts that behave similarly (just as cool maybe). They can show stark contrasts based on different attributes. Below compares survey responses from three locations.

<p align="center">
  <img src="https://github.com/imjakedaniels/boomerang_charts/blob/master/animations/residency_animation.gif">
</p>
