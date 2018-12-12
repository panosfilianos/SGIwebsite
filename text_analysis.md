---
menu: true
order: 4
layout: research
title: Text Analysis
---

## Text Analysis of Spotify's Top of the Top
## Music is a beautiful thing.
It connects people of different backgrounds, from different parts of the world in a nearly automatic, subconcious level. It allows us to experience a mystical, unexplainable joy that is hard to come by in a world that is becoming increasingly logical and technocratic.

Albeit, music is not comprised just from a melody that can be comprehensible to all. A major part of the medium,   is the lyrical expression. This feature is grown and brewed in the contextual climate of the locality of each song and can provide unique insight on the feelings and form of expression of millions of people.

Thus, we have decided to have a closer look on what are the attriutes of lyrics of the Top Artists in Spotify's service. Specificaly:

- We have __retrieved__ the Top 100 Artists of 7 Top Genre's of Spotify. This totals to 700 Artists.
- We __fetch__ the current Top 10 songs of each Artist
- We __find__ the lyrics of each one of these songs
- We __analyse__ those lyrics with focus on sentiment, grammar, lexical similarity as well as a set of other features and __plot__ the results to reach meaningful conclusions

Finally, by utilizing our results we can effectively validate assumptions about characteristics of Genres, build useful tools and unearth improbable or unexpected connections between Artists who speak about the same things (or in the same way or about the same feelings) but belong in different Genres.

## It is not easy to find lyrics
Our research requires us to fetch lyrics. This is a challenging task because there is no open database of all song lyrics available. To successfuly manage to attain the lyrics for our songs we've had to resort in using a mix of services.

Concequently, we used:
1. __AZLyrics__: AZLyrics offers one of the most comprehensive, open libraries for lyrics.
2. __LyricWikia__: Unfortunatelly, LyricWikia's library is not completely comprehensive but retrieving data from them is not as daunting as in other places.
3. __Genius__: Genius's library of lyrics is focused in (and started from) Hip-Hop and Pop songs. Regardless, in the last years there has been a surge of new lyric pages of more genres. Genius is used extensively in the final solution, as LyricWikia can drop the ball in terms of finding lesser known songs.

## Words have amazing value
The backbone of this analysis is comprised from the lyrics' text and the things we do with it. We tried to go as deep as possible and extract a multitude of results and conclusions on them. After all, words _can_ tell a complete story.

But maybe they tell us even more than what can be derived from one song, with one glance or one brief moment of singing along the radio .

We analysed lyrics on the basis of being members in specific genres but also as a mere member of the whole set of lyrics. For each song we are going to retrieve:

- A sentiment metric
- A full grammar term analysis 
- A word count
- An analysis on its explicitness (swear words and expressions) 
- An analysis on the brands mentioned, divided by their sector




![Imgur](https://i.imgur.com/WSPHhFl.png){:class="img-responsive"}
![Imgur](https://i.imgur.com/E6N9bF8.png){:class="img-responsive"}
![Imgur](https://i.imgur.com/kOWiPFT.png){:class="img-responsive"}
![Imgur](https://i.imgur.com/5Qq5Td7.png){:class="img-responsive"}
![Imgur](https://i.imgur.com/zZriTmp.png){:class="img-responsive"}
![Imgur](https://i.imgur.com/SAhSNKY.png){:class="img-responsive"}
![Imgur](https://i.imgur.com/lNRzpmI.png){:class="img-responsive"}
![Imgur](https://i.imgur.com/WIOXmOu.png){:class="img-responsive"}
![Imgur](https://i.imgur.com/1tLC6Rh.png){:class="img-responsive"}
![Imgur](https://i.imgur.com/T4rU2WC.png){:class="img-responsive"}
![Imgur](https://i.imgur.com/dDtynpD.png){:class="img-responsive"}
![Imgur](https://i.imgur.com/nJ81efF.png){:class="img-responsive"}
![Imgur](https://i.imgur.com/HH7gSJY.png){:class="img-responsive"}
![Imgur](https://i.imgur.com/ymjmTEE.png){:class="img-responsive"}
![Imgur](https://i.imgur.com/oQrkTDV.png){:class="img-responsive"}
![Imgur](https://i.imgur.com/ja80C5g.png){:class="img-responsive"}
