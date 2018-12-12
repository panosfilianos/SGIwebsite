---
menu: true
order: 4
layout: research
title: Text Analysis
---
# Text Analysis of Spotify's Top of the Top
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

But maybe they tell us even more than what can be derived from one song, with one glance or one brief moment of singing along the radio.

We analysed lyrics on the basis of being members in specific genres but also as a mere member of the whole set of lyrics. For each song we are going to retrieve:

- A sentiment metric
- A full grammar term analysis 
- A word count
- An analysis on its explicitness (swear words and expressions) 
- An analysis on the brands mentioned, divided by their sector

## Feelings of Love and Hate
### Inside Spotify's Top of the Top
Each word can have a certain sentiment value. This is assigned by asking a lot of people how they would rate that song sentimentally from 0 to 10 (0 being really sad and 10 being the happiest). All results for all words are kept into datasets.
We utilized three datasets/libraries to derive the sentimet results of the full corpus of lyrics:
    - Hedonometer sentiment (based on this [article](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0026752#s1))
    - TextBlob sentiment (based on the Python library)
    - SenticNet sentiment (based on the results discussed [here](https://sentic.net/))
Below, we can see how the sentiment is distributed in the full corpus of lyrics:
![Imgur](https://i.imgur.com/HH7gSJY.png){:class="img-responsive"}
Additionaly we can see how the sentiment is distributed across genres:
![Imgur](https://i.imgur.com/T4rU2WC.png){:class="img-responsive"}
Through this plot we can derive some interesting results:
- The __happiest__ genre in overall tones is __Country__: Its distribution is strongly above 5 with its main corpus of songs peaking near 6.
- The __saddest__ genre in overall tones is __Hip Hop__: Its distribution's peak is below 5.5
- The most __sentimentaly versatile__ genres are both __Blues__ and __Soul__: Both genres have a strong representation through their artists on the whole of the presented spectrum

## Listening to all songs at once
### Most Frequent Terms and TF-IDF
In this section we essentialy tried to validate an assumption:
> Songs, after all, are not that different. If you hear a song that belongs to a genre, it's like you've listened to the whole of it.

We did this by finding the most common songs of each genre (based on their frequency - Freq) and the ones that differentiate songs inside a genre (based on a metric called TF-IDF). If the second are not that special, then the songs of the genre can be very similar.

We, also, define the term _rythm collocations_: They are words that can be found together and that give rhythm to the song. Some example can be: 'hey hey hey', 'yeah yeah yeah', 'oh oh oh' etc.

These are the results:

![Imgur](https://i.imgur.com/SAhSNKY.png){:class="img-responsive"}

__Indie__: The frequency wordcloud is created off terms that are coming up in all genres. The TF-IDF wordcloud is comprised of names, rhythm collocations but also some words that are part of the hook of the song. These words are abstract (eg. Lionheart, Superlove, Aftershock etc.)

![Imgur](https://i.imgur.com/E6N9bF8.png){:class="img-responsive"}

__Country__: Its TF-IDF's wordcloud gives some very interesting results. One can recognize distinctive words that consist of a plularity of themes. Words like this are: redneck, tailgate, crank - hank, cowboy, country, truck, tractor. These results give us a good idea on what Country is talking about.

![Imgur](https://i.imgur.com/kOWiPFT.png){:class="img-responsive"}

__Soul__: Soul doesn't seem to have a lot of differences between Freq and TF-IDF. It is interesting to note the creativity, difference and uniqueness of the rhythm collocations. Some examples are: duda shaka, badu (which comes up in repetitions throughout songs), chikaching.

![Imgur](https://i.imgur.com/WSPHhFl.png){:class="img-responsive"}

__Pop__: Pop, also, doesn't seem to have any meaningful differences between Freq and TF-IDF. Most TF-IDF terms are names, leading us to the conclusion that songs can be the same (or very similar). Just changing the names, would change the song.

![Imgur](https://i.imgur.com/zZriTmp.png){:class="img-responsive"}

__Rock__: Songs seem to have significant differences. Words like: Thunder, Rosana and Propaganda come up in the TF-IDF wordcloud.

![Imgur](https://i.imgur.com/1tLC6Rh.png){:class="img-responsive"}

__Blues__: Although Blues songs won't have big differences, it's entertaining to see the TF-IDF include a lot of female names, implying similar love songs written for different women. Names like this are: Josephine, Layla, Rosalie, Madison
 
![Imgur](https://i.imgur.com/lNRzpmI.png){:class="img-responsive"}

__Hip-Hop__: The genre's results are similar to Pop. The TF-IDF wordcloud holds mostly names like: Snoop, Dogg, Krippy, Maybach etc.


## Parental advisory
### An Explicitness Analysis
Explicitness here is defined as: _the number of explicit material in the lyrics of a song_. More simply put, its how many swear words a song includes.

We used Google's definition of swear words, which includes the 'mainstream' version of them as well as common variations. The dataset that can be found [here](https://github.com/RobertJGabriel/Google-profanity-words).

These are our results:

![Imgur](https://i.imgur.com/oQrkTDV.png){:class="img-responsive"}

Analyzing the results above:
- __King of Swears__: __Hip-Hop__ is the undisputed winner. In a total of less than 1000 songs, almost 2500 swear words where used. The genre does not seem to have a large amount of swearing vocabulary, concentrating its impressive numbers into three swear words.
- The __most creative__ in the use of swear words, are both __Soul__ and __Pop__ concentrating their results in 4 swear words.
- The __least creative__ would be __Blues__ having only two swear words on its current catalogue.




## Are songs, advertisments?
Songs can include names on brands. We worked based on the following assumption:
> We assume that the mentioning of those brands, implies an advertisment and is done, in the overwhelming majority of cases, without the intent of smearing or criticizing the brand. Through that light, every mention of a brand is classified as an advertisment event.

We worked by indentifying brands that are included in:
- Top 500 Global Brands
- Top 100 Automotive Brands
- Top 50 Brands in Apparel
- Top 50 Brands in Spirits
- Top 10 Brands in Tobacco

The results are, once again, very interesting:

![Imgur](https://i.imgur.com/nJ81efF.png){:class="img-responsive"}

- __Choosing the medium__: Not all categories of brands come up in the plot. Tobacco and Spirit brands seem to have no representation. At the same time, brands from other categories come up more frequently. That is specifically true for Fashion, Auto (Car) and Global brands. 
- __Participation denial__: Also, not all genres include brand mentions. In particular, Indie and Soul seem to have far less mentions, where Rock and Blues, almost none.
- __The Advertiser__: __Hip-Hop__ is the genre that mentions brands the most. The most advertised through Hip-Hop songs, are Fashion brands, with Auto brands a close second.
- __A Trusted Pal__: It is interesting to observe that Country songs generaly abstain from mentioning brands with the sole exception of Auto brands. This doesn't come as a surprise, as words like tailgate, truck, tractor where part of the TF-IDF wordcloud.

## Wordy or laconic?
We also researched the wordiness of each genre. That is _how many words does a genre's song have approximatelly? Are there genres that are very wordy and rely strongly on lyrics or are they somewhat the same?_

![Imgur](https://i.imgur.com/ja80C5g.png){:class="img-responsive"}

A few interesting insights can be offered through the representation above: 
- Firstly we see that Hip-Hop is the undisputed winner of the wordiness contest. Having almost __3 times__ more words on average than Blues, the less wordy genre of them all and almost __2 times__ more than all other genres (with the exception of Pop).
- Secondly, we see that Country, Soul, Rock and Indie have similar words per song.  We indentify Indie's mean to be a little higher, since Indie is an umbrella term that refers more to the way the music is released than the actual content. Thus, inside Indie one can find music of multiple genres which includes Indie Hip-Hop. As we see Hip-Hop is inherently wordy and thus the small increase in Indie.

## New words for me
### Lexical wealth
We also attempted to find how lexically wealthy each genre is. To do this, we found the number of different words inside every genre:

![Imgur](https://i.imgur.com/ymjmTEE.png){:class="img-responsive"}

We see that the results largely correlates with the 'Average Number of words per song per genre' presented above. Hip-Hop is the most lexical diverse, where blues is the least diverse. 
## Count (on) my words
### How are words distributed in songs of a genre?
This time we focus on a __word count distribution__ per song, presented by genre:

![Imgur](https://i.imgur.com/dDtynpD.png){:class="img-responsive"}

We observe that:
- The __most diverse__ genre in terms of length is __Hip Hop__: Starting from around 200 words, Hip-Hop songs can go up to more than 1000 words, featuring the ties the genre can have to Spoken Word.
- The __least diverse__ genre is __Country__: It seems that songwriters of this genre seem to follow a tested and successful recipe as far as the length of the songs is concerned.


## JoyPlots: A small tribute

The retrieve a sentiment distributions graphs that made sense we resorted to Joy Plots. These plots, apparently took their name from the iconic album cover of __Joy Division's Unknown Pleasures__ album ([Source](https://blog.revolutionanalytics.com/2017/07/joyplots.html)). The album cover is presented below:

![Imgur](https://i.imgur.com/WIOXmOu.png){:class="img-responsive"}

As a tribute to the great band, great album and great people that came up with this vizualization, we will plot the distribution of song sentiment of each artist inside Rock (the closest we have to Joy Division's genre, Punk), to something that will hopefully look similar to you:

![Imgur](https://i.imgur.com/5Qq5Td7.png){:class="img-responsive"}

## Conclusions

### [Go back to the home page](https://scoupafi.github.io/SGIwebsite/index.html)


