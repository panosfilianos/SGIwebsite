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
>**The audio metric is a vector that includes the 3 following musical attributes:**<br>
**_Valence_**:<br> 
A measure from 0.0 to 1.0 describing the musical positiveness conveyed by a track. Tracks with high valence sound more positive (e.g. happy, cheerful, euphoric), while tracks with low valence sound more negative (e.g. sad, depressed, angry).<br><br>
**_Energy_**:<br>
Energy is a measure from 0.0 to 1.0 and represents a perceptual measure of intensity and activity. Typically, energetic tracks feel fast, loud, and noisy. For example, death metal has high energy, while a Bach prelude scores low on the scale.<br><br>
**_Danceability_**:<br>
Danceability describes how suitable a track is for dancing based on a combination of musical elements including tempo, rhythm stability, beat strength, and overall regularity. A value of 0.0 is least danceable and 1.0 is most danceable.<br>
>***The 3 aformentioned attributes will be used to assess the musical similarity between songs*** and determine the _mood_ of a song

### Ok. All the required data was obtained but, naturally, a serious concern rised:
How are we going to compare the songs using this audio metric?<br>

_At first we had one idea:_

**Get the mean of the three elements, in order to obtain one number out of the vector.**
> This is a handy and faster solution, as you need to compare just one number for each song, in order to decide if it will be connected with another one.<br>
>However, we must consider that what we are measuring here is song similarity and ***each element of this vector describes a unique quality of every song.***
***Diminishing this three-dimentional vector to just the mean of it's elements***, most probably ***comes with a cost***. That is, that there may be several different vectors (different song qualities), that produce the same mean, and this could lead to connecting two songs that are completely different.<br>
We said before that the three elements of the vector are valence, energy and danceability. It is reasonable to assume that a song with high danceability, most likely has high valence and energy. Or that a song with low valence, most likely has also low danceability and energy. If this is true, it means that these three elements follow a specific pattern and thus we can use the mean of every vector without getting a false idea for how a song sounds.<br><br>
**To find out if this is actually true, we have put it to the test:**<br><br>
>As you will see below, what we did was find the distribution of the absolute subtraction between two elements, for each pair of elements. If all songs have a very small difference between their elements' values, then we can safely use the mean.


[Imgur](https://i.imgur.com/WgoeiEk.png){:class="img-responsive"}<br>

[Imgur](https://i.imgur.com/lffU2Z9.png){:class="img-responsive"}<br>

[Imgur](https://i.imgur.com/hRj1VWp.png){:class="img-responsive"}<br>


As we see from the distributions above, the pattern we have talked about earlier really exists in a very high amount of songs, for every pair of elements. However, there are also quite a few songs with high "distance" between their elements and this cannot go unnoticed.<br><br>
Since it is always better to use examples, below you can hear how a song with very **low valence**, but **high danceability** sounds like.
> This song has valence = 0.12 and danceabilty = 0.73. We remind you that the max value for these elements is 1.<br><br>

Keep reading and enjoy!

<a href="http://www.youtube.com/watch?feature=player_embedded&v=q7lKpkW_jG8" target="_blank"><img src="http://img.youtube.com/vi/q7lKpkW_jG8/0.jpg" 
alt="IMAGE ALT TEXT HERE" width="240" height="180" border="10" /></a>


***So, after actually listening to songs with high distance between their elements, we came up with a second idea, regarding how we are goint to use our vector. And that is the idea we kept :***

- #### We calculate the Euclidean distance between the vectors.
>This way we use the whole vector and essentially create a sphere in space, which contains all the vectors with distance equal, or lower to the one that we choose to use as a treshold.<br><br>
***if:***<br><br>
$ \sqrt{(valence_2 - valence_1)^2 + (energy_2 - energy_1)^2 + (danceability_2 - danceability_1)^2} <= treshold $, <br><br>
***then add_edge between 1 and 2***

In the next chapter you will see the graph created, following the idea described above.


## Create and analyze the Networks

>Firstly, let's explain what exactly the **Network of Similarity** is about:
- Nodes: Unique Songs
- Edges: An edge connects two songs, only if their vector distance is equal, or lower to the chosen treshold. Or, in other words two songs are connected, only if they are similar enough for our chosen standards.

>The main idea of what we want to do is described below:
- Find the songs that represent the "sound" of each genre. ***(Top 5 songs based on connectivity)***
- Find how consistent each genre is soundwise. Do most songs sound similar, or you can find many different sounds/styles? ***(See how many different connected components there are per genre. Degree distribution for each genre)***
- Find the main different sounds of each genre ***(by creating communities)***


### Network of Pop

#### Visualization


[Imgur](https://i.imgur.com/DstBnUJ.png){:class="img-responsive"}


#### Degree Distribution of Pop Songs Network

[Imgur](https://i.imgur.com/5wj8p6s.png){:class="img-responsive"}


What we cam see from the distribution above is that most nodes are low-connected, while only a few nodes are the most connected ones.

By this kind of degree distribution we could infer that only a few amount of the total of pop songs, represent the "mood" of the genre.


#### Top 5 most connected songs of Pop

1. Love on the Weekend by John Mayer	 

2. thank u, next by Ariana Grande	 

3. Sober by G-Eazy	

4. TAlk tO Me (with Rich The Kid feat. Lil Wayne) 

5. bellyache by Billie Eilish	 

By examining the audio metric, we also see that all top-5songs are very similar to each other in terms of mood. This inidicates a sense of consistency regarding the mood of these songs and, most likely - regarding the previous findings (degree distribution) - of the whole genre. (which makes sense, if we sit back and think a bit about how non-diverse pop music is.)

- **Valence** audio metric ranges from 0.41 - 0.43
- **Energy** audio metric ranges from 0.57 - 0.66
- **Danceability** metric ranges from 0.69 - 0.72

By the above we can see that Pop's main mood and sound has average "happyness", average energy, and relatively high danceability.


#### Community Detection

There are 11 main communities in the Pop network.

[Imgur](https://i.imgur.com/DstBnUJ.png){:class="img-responsive"}


### Network of Rock

#### Visualization


[Imgur](https://i.imgur.com/FTn2N0A.png){:class="img-responsive"}


#### Degree Distribution of Rock Songs Network

[Imgur](https://i.imgur.com/FHbaI6S.png){:class="img-responsive"}

Below you can see the degree distribution of the Rock Network of Musical Similarity.

Compared to the Pop network, this degree-distribution is closer to the gaussian one, but still there is a tendency of most nodes being more low-connected. So, we have almost the same pattern, of few songs representing rock's main "mood" or style, but in a lesser extent, compared with Pop.


#### Top 5 most connected songs of Rock

1. Master of Puppets (Remastered) by Metallica

2. The Last Of The Real Ones by Fall Out Boy

3. Shut Up and Dance by WALK THE MOON

4. Into the Night (feat. Chad Kroeger) by Santana	 

5. Hash Pipe by Weezer


Again, what we see is that all top-5 songs are really close, in terms of musical attributes. What we see, though, is that regardless of their same attributes, their sound is not very close. (e.g. Master of Puppets by Metallica, and Into the Night by Santana).

#### Why this happens?
> The musical attributes we have chosen can detect the general "mood" of the song, how upbeat it is, or how slow and sad. What they cannot detect well is the actual sound, which may stem from the actual instruments that are used.
Further we discuss reasons for why this happens and how the reliability of our metric could by improved, without ay change of the metric itself.

- **Valence** audio metric ranges from 0.56 - 0.62
- **Energy** audio metric ranges from 0.83 - 0.87
- **Danceability** metric ranges from 0.54 - 0.59

By the above metric values, we can see that Rock's main mood and sound has average "happyness", very high energy, and relatively high danceability.


#### Community Detection

There are 13 main communities in the network.

[Imgur](https://i.imgur.com/rRgTQsf.png){:class="img-responsive"}


### Network of Hip-Hop

#### Visualization

[Imgur](https://i.imgur.com/U1Vvcqn.png){:class="img-responsive"}

#### Degree Distribution of Hip-Hop Songs Network

[Imgur](https://i.imgur.com/km5dFxl.png){:class="img-responsive"}

The same pattern continues with most songs being more low-connected and less songs having the higher degree.

#### Top 5 most connected songs of Hip-Hop

1. Yoppa (with BlocBoy JB) by BlocBoy JB

2. Moves by Big Sean

3. Love Galore (feat. Travis Scott) by SZA	

4. Sold Out Dates (feat. Lil Baby) by Gunna

5. FlatBed Freestyle by Playboi Carti


The top-5 of Hip-Hop are really close regarding the musical attributes we have extracted from Spotify. Also, contrary to Rock, Hip-Hop seems to be a more consistent sounding genre, as all top-5 most representing songs have the same "new-school" sound of hip-hop music. This is a quality we can detect only by listening to the songs and cannot be inferred from the audio metric. As we said the audio metric can give us the general "mood" of a song and if this is combined with a fairly consistent sounding genre, then we have much better results.

- **Valence** audio metric ranges from 0.34 - 0.41
- **Energy** audio metric ranges from 0.5 - 0.59
- **Danceability** metric ranges from 0.76 - 0.82

By the above we can see that Hip-Hop's main mood and sound has relatively low "happyness", moderate, but high danceability.


#### Community Detection

There are 8 main communities in the Hip- Hop network.

[Imgur](https://i.imgur.com/sTtMn4T.png){:class="img-responsive"}


### Network of Blues

#### Visualization

[Imgur](https://i.imgur.com/c5KhkLR.png){:class="img-responsive"}

#### Degree Distribution of Blues Songs Network

[Imgur](https://i.imgur.com/d4OTzAY.png){:class="img-responsive"}

In this genre it is clear that we moved from the previous pattern, closer to the normal gaussian distribution. This means that most of the songs have the same amount of degree  and thus the song "mood" that we calculate is more consistent compared to previous genres.


#### Top 5 most connected songs of Blues

1. American Woman - 7" Version by The Guess Who

2. Take It From Me by KONGOS

3. Reelin' In The Years by Steely Dan

4. Whiskey In The Jar by Metallica

5. Outta My Mind by The Arcs

Through the degree distribution we have seen that the songs' "mood" obtained by our audio metric, is more consistent in this genre. However, again we come across to the phenomenon, which occured in Rock music. By listening to the top-5 representing songs, there are differences between them regarding their actual sound. Some of them seem more like classic rock, which is highly influenced by blues, and others have a more contemporary sound, reminding bands like The Black Keys.

- **Valence** audio metric ranges from 0.75 - 0.77
- **Energy** audio metric ranges from 0.69 - 0.76
- **Danceability** metric ranges from 0.52 - 0.56

By the above we can see that Blue's main mood and sound has high "happyness", high energy, but an average danceability.

#### Community Detection

There are 12 main communities in the Blue's network.

[Imgur](https://i.imgur.com/CR0OMCB.png){:class="img-responsive"}





### Network of Indie

#### Visualization

[Imgur](https://i.imgur.com/StazZid.png){:class="img-responsive"}

#### Degree Distribution of Indie Songs Network

[Imgur](https://i.imgur.com/9NitkNm.png){:class="img-responsive"}

The degree distribution again moves back to the previous pattern, having most of the songs concentrated on degrees, lower than the mean one, in the same respect as Pop and Rock.

#### Top 5 most connected songs of Indie

1. Flight 22 by Kali Uchis

2. Maybe We're Meant To Be Alone by Bad Suns

3. The Reason by Chelsea Cutler

4. Navajo by Masego

5. Crew (feat. Brent Faiyaz & Shy Glizzy) by GoldLink

Indie also seems like a more consistent genre in terms of sound of the songs. We, ve seen by the degree distribution that few songs have high degree, thus these songs show the main moodof the genre, and we have also listened to the top 5, which seem very close sounding.

- **Valence** audio metric ranges from 0.34 - 0.45
- **Energy** audio metric ranges from 0.61 - 0.65
- **Danceability** metric ranges from 0.64 - 0.73

By the above we can see that Indie's main mood and sound has relativiley low "happyness", moderate energy, and makes you move a bit more than just standing still while listening.

#### Community Detection

There are 13 main communities in Indie's network.

[Imgur](https://i.imgur.com/vTU2SqA.png){:class="img-responsive"}



### Network of Country

#### Visualization

[Imgur](https://i.imgur.com/XqKYju0.png){:class="img-responsive"}

#### Degree Distribution of Country Songs Network

[Imgur](https://i.imgur.com/9FrpLAQ.png){:class="img-responsive"}

The degree distribution follows the pattern of most genres. Few songs give the general "mood" og the genre's songs.

#### Top 5 most connected songs of Country

1. 20 in a Chevy by Cole Swindell

2. Little Bit of Both by Chris Janson

3. That's When I Love You by Phil Vassar

4. Me on You by Morgan Evans

5. Me and My Kind by Cody Johnson

Country music is a genre that follows more strongly the pattern we are talking about. Only a few songs gibe the general "mood", although by listening to the songs we can see that they are the more traditional straight country songs onw would expect and then we have the more modern, which are like pop-country music.

- **Valence** audio metric ranges from 0.52 - 0.67
- **Energy** audio metric ranges from 0.8 - 0.85
- **Danceability** metric ranges from 0.55 - 0.59

By the above we can see that Country's main mood and sound has relativiley high "happyness", very high energy, but they average danceability, and trully country songs are not the ones that someone would expect to dance listening to them.

#### Community Detection

There are 8 main communities in Country's network.

[Imgur](https://i.imgur.com/h7VgomE.png){:class="img-responsive"}



### Network of Soul

#### Visualization

[Imgur](https://i.imgur.com/vi5JK5j.png){:class="img-responsive"}

#### Degree Distribution of Soul Songs Network

[Imgur](https://i.imgur.com/WThv9Wx.png){:class="img-responsive"}

The degree distribution follows the pattern of most genres. Fewer songs give the general "mood" of the genre's songs.

#### Top 5 most connected songs of Soul

1. Fantasy by Alina Baraz

2. I Can't Get Next To You by The Temptations

3. Charlie Brown by Anna Of The North

4. Safe - Shallou Remix by Shallou

5. Come Over by Kenny Chesney

Soul  also follows the pattern we keep talking about. Only a few songs represent the genres general "mood". By listening to the songs, we see that only one has a more traditional soul mood, while the others are modern and sometimes do not remind you of soul, althouth the respective artist is classified as soul by Spotify.

- **Valence** audio metric ranges from 0.69 - 0.72
- **Energy** audio metric ranges from 0.66 - 0.75
- **Danceability** metric ranges from 0.65 - 0.68

By the above we can see that Soul's main mood and sound has mild to high "happyness", mild energy and mild danceability.

#### Community Detection

There are 13 main communities in the network.

[Imgur](https://i.imgur.com/vi5JK5j.png){:class="img-responsive"}



### Full Graph

#### Visualization

[Imgur](https://i.imgur.com/gZHaEKq.png){:class="img-responsive"}

#### Degree Distribution of Soul Songs Network

[Imgur](https://i.imgur.com/Yezyaoh.png){:class="img-responsive"}


#### Barplot of mixes-genre songs per Genre

In many cases we came across songs which did not belong to just one genre. Below we show how many these songs are per genre.

[Imgur](https://i.imgur.com/GKx8Dky.png){:class="img-responsive"}

From the above plot we get a well expected result. The more popular genres (pop, hip-hop, rock) have more mixed songs. This makes sense, if we consider that the genres stem from artists and not from the songs, and thus artists from more popular genres have a more diverse and broad range.

Soul, blues and country on the other side hav much more mixed songs, which shows that the respective artists have a more focused attitude to their genre's music style.


## Discusions and Conclusions

We have seen that our metric works well in detecting a general "mood" of a song, but it cannot quite catch the real sound of a song. We can give an example, which was drawn by  analyzing the Rock Network. While commenting on the top 5 connected songs of the Network, we' ve seen that although the songs were very close values of the audio_metric, some of them were very different on how they sound.

The first one was ***Metallica's - Master of Puppets*** and the second one was ***WALK THE MOON's - Shut Up and Dance***

The difference is obvious.

The problem lies in the fact that Spotify is not very "strict" in regards to genre separation. This means that genres like Rock can contain many songs that also belong to another genre, consequently making a more diverse genre.

The way we could overcome this problem is threefold. Firstly, be more strict when downloading the artists, in the sense of writing more specific queries and thus obtaining only the really relevant artists and consequently songs of each genre.
Secondly, as we cannot avoid the fact that artists with mixed genres will occur, when obtaining the top-5 songs of each genre, we could filter the songs and keep only the ones that belong **only** to that particular genre. Lastly, the most ambitious goal of ours, would be to connect our audio metric, with the lyrics sentiment metric and build a much more reliable metric that takes into account both "mood" and context.

Regarding communities Also,we have seen that, in general we had 12-14 per genre. If we assume that every community can represent a subgenre, 12-14 might be a big number. This can be lowered by increasing the treshold for connecting two songs. This way less and more broad communities will be produced, with more distinct audio metrics between them.
In addition, future work that should be done is to find and categorize each subgenre(community) by further analyzing the community neteworks. 

### [Go back to the home page](https://scoupafi.github.io/SGIwebsite/index.html)