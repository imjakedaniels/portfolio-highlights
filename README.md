# Jake's Porfolio

Below are some of my past visuals, reports, and projects. 

## Scraping & animating a basketball game using {rvest} & {gganimate} 

<p align="center">
  <img src="https://github.com/imjakedaniels/raptors_animation/blob/master/animations/Toronto Raptors_Utah Jazz-20200309.gif">
</p>

Using play-by-play data from [basketball reference](https://www.basketball-reference.com/boxscores/pbp/202003090UTA.html):
 
 <img src="https://github.com/imjakedaniels/raptors_animation/blob/master/play-by-play-data.PNG" width="800" height="400">
 
Data was scraped off the table using {rvest}, cleaned and summarized the data using {dplyr}, and styling with {ggtext}, {gganimate}.

I got 1500 upvotes on Reddit for an earlier version of this chart: https://www.reddit.com/r/torontoraptors/comments/eemlz4/what_a_comeback_vs_dallas/

More details in [raptors_animation repository](https://github.com/imjakedaniels/raptors_animation)

## Animating Chatter throughout the course of a Leafs Game

<p align="center">
  <img src="https://github.com/imjakedaniels/animated_leafs_graphs/blob/master/animations/twitter_reddit-leafs-tampa-bay-lightning-2020-03-10.gif">
</p>

More details in [animated_leafs repository](https://github.com/imjakedaniels/animated_leafs_graphs)

## Bloomberg Climate Change Animation

Recreating a Bloomberg visualization on Climate Change using their data.

Article here: https://www.bloomberg.com/graphics/2015-whats-warming-the-world/

<p align="center">
  <img src="https://github.com/imjakedaniels/bloomberg_climate_animation/blob/master/animations/bloomberg_orginal.gif">
</p>

Notebook in [bloomberg_climate_animation](https://github.com/imjakedaniels/portfolio-highlights/)

## Visualizing political discourse off Medium.com every week

Scraping articles tagged "politics" off Medium with a scraper I made. Tokenizing articles and using pairwise correlations to create node networks that present latent groupings of topics from that week. Below are from Jan 26th 2020 to Feb 1st 2020.

### Trending Network

Based on geometric claps generated.

<p align="center">
  <img src="https://github.com/imjakedaniels/visualizing_politics/blob/master/visuals/trending_politics_network%202020-01-26%202020-02-01%20.png">
</p>

### Volume Network

Basesd on mention volume.

<p align="center">
  <img src="https://github.com/imjakedaniels/visualizing_politics/blob/master/visuals/volume_politics_network%202020-01-26%202020-02-01%20.png">
</p>
