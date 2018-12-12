---
menu: true
order: 1
layout: research
title: Our Dataset
---

We mainly decided to extract all music data we needed from ***Spotify***.

Spotify is probably one of the most well-known music streaming platforms all over the world. It contains more than 40 millions of tracks that users can listen to thanks to their multi-platform web and mobile applications. 

But in this case, we are mostly interested in the Spotify Web API endpoints. Using them, we have been able to obtain our desired information about music artists, albums, and tracks directly from the Spotify Data Catalogue. Furthermore, we have also been interested in obtaining calculated audio features of tracks.

The functions used to download our desired data are the following ones:

* Search by genre
* Get an Artist's Top Tracks
* Get an Artist's Albums
* Get an Album's Tracks
* Get a Track
* Get Song's audio features

To actually download all data needed, we have used the already existing Spotify library for Python. In order to use it, we first had to get credentials that Spotify asks. Anyone can ask for these credentials through the Spotify Website.

### We found where we get the data from! Now what?

We agreed in the following flow of actions:

- Retrive the ***Top 100 Artists*** of ***7 Top Genre's*** of Spotify. This totals to _700 Artists_.
- Fetch the current ***Top 10 songs of each Artist***.
- Find the ***collaborations*** of each Artist, by mining each Artist's albms.
- Get ***audio features*** of each one of these songs.
- **Mine** the lyrics of each one of these songs.

The genres we decided to retrieve songs from are the following:

* Pop
* Rock
* Hip-hop
* Blues
* Indie
* Country
* Soul

# Basic stats. Let's understand the dataset better

## Artist's Dataset

First, the artists' list of top 100 artists for each genre has been created. In this case, the *Search by genre* endpoint has been used by assigning that the type of the response information desired is artist. The maximum length of objects on each response that Spotify allows is just 50, so we needed to make the call twice by using the parameters *limit* and *offset* to obtain our information desired.

The downloaded list of artists has been saved on *artists.csv* file and for each artist, the following information has been kept.

* Artist
* Genre
* Artist uri
* Artist id

Afterwards, the collaborations for each artist wanted to be retrieved. To do it, we had to obtain the list of songs for each artist and then checked if the song has multiple artists or not.

As the Spotify platform does not allow to directly obtain the songs for each artist, first all the albums for each artist were obtained again with the *limit* and *offset* parameters. And then, for each album retrieved, all songs were downloaded and analyzed. A similar procedure was executed for the singles of each artist to obtain as much information as possible related to collaborations because we realized that some remix songs created were not included in an album. This time, we just retrieved, at maximum 50 singles for each artist.

Furthermore, we realized that we had to exclude the *compilation* albums and lists retrieved on the same service because, otherwise, information regarding the list of reproductions created by Spotify was also retrieved and processed on our creation of the graph.

In this step, we decided to do not filter the collaborations within our list of artists, as it would be nice to also abstract some information from the other collaborations at some point of our further analysis. That is why, each time that more than one artists were found on a song, a new entry was added to the *artists_colab.csv* or *artists_colab_singles.csv* files with the following format without any other filtering.

* Artist
* Artist id
* Artist colab.
* Artist colab. id
* Song
* Song id

## Songs Dataset

The dataset used for the Network of Song Similaruty is the topsters_all.csv. It contains information about the top 10 songs, of top 10 artists, of all genres. To create this we were based on the artists.csv

To obtain all the relevant data for this particular dataset, we also used the Spotify Library of Python (Spotipy).
After mining Spotify data, we got the elements needed , by mainly using the following functins:

>sp.artist_top_tracks<br>
sp.audio_features

The topsters_all.csv contains the following data in order.
* **Genre**: A list, which contains the genre(s) that the song belongs to. To do this we "borrowed" the genre(s) of the relevant artist from the artists.csv.
* **Artist**: The artist's name.
* **Artist_id**: Spotify API assigns a unique ID to each Artist.
* **Song**: The name of the song.
* **Song_id**: Similarly with Artists, Spotify API assigns a unique ID TO each song. This way you can distinguish to songs that might share the same name.
- **Audio_Metric**: A vector of 3 elements. Each of these elements is a particular audio feature. Namely, _Valence_, _Energy_ and _Dancebility_. We got those features by mining the Spotify API.

## Lyrics Mining

Lyric mining is a challenging task. This falls under the caveats of our venture. As with the challenges we faced with data preparation from Spotify, lyric mining would become the next big hurdle for us. To successfuly manage to attain the lyrics for our songs we've had to resort in using a mix of services. A simpler solution would be to use the Musicmatch API which offers direct access to the data we need.  

We have decided to refrain from using that API because:
- The free available version of their service is limited to 2000 requests per day and only 30% of the song. Even though the first part of the problem can be dealt with, by mining on consecutive days, the second part would be a roadblock for a meaningful lyrical analysis.
- The costs are very high for the amount of data we need.

Regardless, it is interesting to note that Musicmatch is offering solutions that can greatly resemble the possibilities that one has by enhancing the solutions described in our research. 

Concequently, we have utilized three methods of attaining lyrics:
1. __AZLyrics__: We directly mine their website for the song in question (using the available `azlyrics` library). AZLyrics offers one of the most comprehensive, open libraries for lyrics. Unfortunately, they impose a Rate Limit on the requests one can make on their website. The Rate Limit itself is unknown and once reached the client's IP is banned for an, also, unknown amount of time.
2. __LyricWikia__: Our method (through the corresponding library) also uses HTTP requests. Although there are no Rate Limits that seem to be restrictive with this solution, LyricWikia's library is not completely comprehensive.
3. __Genius__: Genius's library of lyrics is focused in (and started from) Hip-Hop and Pop songs. Regardless, in the last years there has been a surge of new lyric pages of more genres. This solution was designated to be a last resort. Genius does not offer an endpoint to retrieve lyrics (the closest would be `/songs/:id`, but it is essentialy the same as an HTTP request of the website) but rather one to search using their search engines and fetch the result. Thus when finding a possible match for a song, we would mine the song's page and parse it with Beautiful Soup. This leads us to conduct two API queries to receive a result from Genius and thus, due to its increased time requirements. Regardless, Genius is used extensively in the final solution, as LyricWikia can drop the ball in terms of finding lesser known songs.

Each lyric `.csv` file includes the following fields: 
* Artist
* Artist id
* Song
* Song id
* Lyrics

### [Go back to the home page](https://scoupafi.github.io/SGIwebsite/index.html)