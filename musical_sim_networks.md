---
menu: true
order: 3
layout: research
title: Musical Similarity Networks
---

## Can Python, Spotify API and some Network tools track real Musical Similarity?

Music is in almost everyone's life. Some people are stuck in just one genre, while others who really enjoy discovering new Music.

But not all songs are fit for every moment of our lives. Sometimes we need an upbeat, happy song to complete our already cheerfull mood, and other moments what we need is a smooth downtempo, hip-hop song straight from the old-school. 

But music is endless and there are many times that we bored of the same playlist, or we just can't find a song matching our mood and taste.

As the title suggests, there is one question. Could we create a tool, able to track down new music with the desired mood, sound and this way cover our need. Part of the answer lies below.


## Get reliable data is the first part

As you have seen in our video we use the Spotify API to mine our data.

For the Song Similarity part of this assignment we create a 600KB file of 5.549 lines and 6 rows.<br>
Each line of our dataset should represent one unique song and various information about it.<br><br>
One could argue that we should have 7.000 songs, since we download the top 10 songs of top 100 artists of each one of 7 genres.<br>
The answer to this concern is that a lot of duplicate songs occured, which we have eliminated from our final file, in order to really have a **_unique_** song per line.

### This file, among others, contains an audio metric for each song.
>#### ***The audio metric is a vector that includes the 3 following musical attributes:***<br>
**_Valence_**:<br> 
A measure from 0.0 to 1.0 describing the musical positiveness conveyed by a track. Tracks with high valence sound more positive (e.g. happy, cheerful, euphoric), while tracks with low valence sound more negative (e.g. sad, depressed, angry).<br><br>
**_Energy_**:<br>
Energy is a measure from 0.0 to 1.0 and represents a perceptual measure of intensity and activity. Typically, energetic tracks feel fast, loud, and noisy. For example, death metal has high energy, while a Bach prelude scores low on the scale.<br><br>
**_Danceability_**:<br>
Danceability describes how suitable a track is for dancing based on a combination of musical elements including tempo, rhythm stability, beat strength, and overall regularity. A value of 0.0 is least danceable and 1.0 is most danceable.<br>
>#### ***The 3 aformentioned attributes will be used to assess the musical similarity between songs.***

### All the required data was obtained but, naturally, a serious concern rised:
How are we going to compare the songs using this audio metric?<br>

_At first we had one idea:_

#### Get the mean of the three elements, in order to obtain one number out of the vector.
> This is a handy and faster solution, as you need to compare just one number for each song, in order to decide if it will be connected with another one.<br><br>
>However, we must consider that what we are measuring here is song similarity and ***each element of this vector describes a unique quality of every song.***
***Diminishing this three-dimentional vector to just the mean of it's elements***, most probably ***comes with a cost***. That is, that there may be several different vectors (different song qualities), that produce the same mean, and this could lead to connecting two songs that are completely different.<br><br>
We said before that the three elements of the vector are valence, energy and danceability. It is reasonable to assume that a song with high danceability, most likely has high valence and energy. Or that a song with low valence, most likely has also low danceability and energy. If this is true, it means that these three elements follow a specific pattern and thus we can use the mean of every vector without getting a false idea for how a song sounds.<br><br><br>
**To find out if this is actually true, we have put it to the test:**<br><br>
>As you will see below, what we did was find the distribution of the absolute subtraction between two elements, for each pair of elements. If all songs have a very small difference between their elements' values, then we can safely use the mean.


3 photos of the respective distributions.

