---
layout: post
title: What Makes a Track Hot or a FLop?
subtitle: A look into what makes a song a success.
cover-img: /assets/img/music_progarm.jpg
thumbnail-img: /assets/img/music_icon.jpg
share-img: /assets/img/music_progarm.jpg
tags: [pyton, music]
---
Ever wonder what makes a song become hit? What makes a song fail or flop? Is there a formula for making a hit track? To make predictions, we should start by looking at the past.  I began by looking at this dataset from Kallgle called The Spotify hit Predictor Dataset (1960-2019). It consists of features for tracks fetched using Spotify's Web API.  Every example has a column that informs us if the song was a hit or flop.  Being a hit means the song has been featured in the weekly list (Issued by Billboards) of hot-100 tracks in its decade, at least once. Each entry has 15 attributes: danceability, energy, duration of song, liveness, and so on. From this data, I was able to create a model that can predict whether a track will be a hit or flop based on its attributes.

<p align="center">
![xg_meme](https://raw.githubusercontent.com/joeyMckinney/joeymckinney.github.io/master/assets/img/classifier_meme.jpg)
</p>

Using XGBClassifier from Xgboost, I was able to achieve an 81% Validation accuracy score. But that still leaves the question of what makes a track a hit song? To answer that, I created this list that orders the most vital features and provides their weight.

 <p align="center">
![fig1](https://raw.githubusercontent.com/joeyMckinney/joeymckinney.github.io/master/assets/img/fig1.png)
</p>

As you can see, 'Instrumentalness' or how much of the song has no vocals, is the number one thing that influences a song's ability to be a hit or flop.  'Acousticness' or how much of a song's instruments were not electrically enhanced or modified, was in second place. With that information, I created this interaction plot below to see what the parameters are best for getting a hit between those two features.

<p align="center">
![fig2](https://raw.githubusercontent.com/joeyMckinney/joeymckinney.github.io/master/assets/img/fig2.png)
</p>

I should mention that Instrumentaliness and Acousticness were measured on a scale of 0 to 1. One being the song was mostly an instrumental or one being the song was a techno song. From this plot, I can infer that the ideal song has around for a hit has .03 and .19 of Acousticness and an Instrumentalness between 0 and .001. 

The next thing I wanted to look at was an example of how much these features pull on a song's ability to be a hit. Let's take a look at God's Plan by Drake. 

<p align="center">
![fig3](https://raw.githubusercontent.com/joeyMckinney/joeymckinney.github.io/master/assets/img/fig3.png)
</p>

In this plot the red is was is pulling the song to be a hit, blue doing the opposite. Although drakes song is a little speechy, the energy, danceability, and instrumentals work in his favor to make this so a hit. 

Ultimately the Instrumentalness, Acousticness,  who is the artist, danceability, and duration of the song is the top 5 contributors to a song's chance to being a hit. I should mention a few things that would make these that could throw these results off. I am only using data from 41,000 songs in the US, that is a small portion of music out there. These songs date back to the 60s, and as we know, the top genres of music have changed a lot over the years. So this may not be the best predictor for today's music.
