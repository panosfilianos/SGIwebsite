---
menu: true
order: 1
layout: research
title: Collaboration Networks
---

Our main purpose of this section has been developing a network analysis of the collaborations between the top 100 artists for every 7 genres defined. With it, we have been able to abstract useful information from the collaborations between the different top artists per genre, see which genres tend to have more collaborations between artists, see if the different artists tend to do collaborations with artists within the same genre or a different one, and much more. In the end, we also created a small recommendation system from the tools learnt during the course.

The data that we have used during this section has been the list of 100 artists of the 7 genres defined and the artists' songs colaborations between these artists.

Thanks to the information retrieved from the artists' songs colaborations, the following network has been created.

[Add picture]

### Main characteristics of the structure of the network

* *Undirected* graph
* Node: Artist inside the top 100 of each 7 genres
    * Name attribute for each node
    * Node color based on genre
    * Node size based on the degree of the node
* Edge: Collaboration between artists
    * Edge weight: Number of times that they have collaborated in different songs

**Main information abstracted from the network created:**

* Number of nodes: 609
* Number of edges: 2163
* Number of isolated nodes: 160

**Main outcome abstracted from the network:**

* The 26,2% of the artists of our network do not have collaborations
* The mean of the number of artists with which an artist has collaborated is 3,5
* Hip-hop, pop and indie artists tend to be connected between them
* Country artists tend to collaborate just with artists within his genre
* It exists considerable collaborations with artists of different genres
* *Mixed* artists seem to have collaborated with more different artists than the other artists
So, it could explain why they are assigned to more than one genre. 
* The second group with higher degree is hip-hop.
* *Blues* artists tend to be connected by pairs. 
* No much rock artists are displayed because most of the 50% of the rock artists nodes are isolated.

To obtain a more accurate information related to the degree values of each node of our network created, the three artists per genre that have a higher degree value are displayed.

| The top 3 nodes with highest degrees |                  |                  |                    |
|--------------------------------------|------------------|------------------|--------------------|
| Pop                                  |     Future 66    |   Gucci Mane 66  |    Lil Wayne 65    |
| Hip-hop                              |     Future 66    |   Gucci Mane 66  |    Lil Wayne 65    |
| Indie                                |      Wale 43     |     G-Eazy 31    |      Khalid 29     |
| Country                              | Willie Nelson 30 |   Colt Ford 27   |   Brad Paisley 16  |
| Soul                                 |  John Legend 26  | Mary J. Blige 20 |   Alicia Keys 14   |
| Blues                                |  Eric Clapton 18 |   B.B. King 18   |   Ray Charles 11   |
| Rock                                 |   Elton John 16  | Fall Out Boy  11 | Imagine Dragons 10 |


*Main Conlusions*

With the results retrieved, we can see that the top 3 artists, regarding the number of other artists that they have collaborated with, of the hip-hop and pop artists are the same ones. So we can identify them as three of the mixed artists displayed on the network above, as they are classified within more than one genre.

Both three artists - Future, Gucci Mane and Lil Wayne - almost double the number of artists that the other top artists of the other genres have collaborated with. So we can reaffirm that artists within hip-hop and pop genres seem to be the ones that have collaborated with more different artists.

After looking for more information related with the three top artists stated, they all three seem to be defined as rapers. It hinds that there is a representation of hip-hop artists that are also classified as pop artists. It remains to be researched if Hip-hop is majorly or solely providing artists to pop. A possible correlation with this currency will be also found and exposed during the text analysis of the lyrics.

We can also see with the results retrieved for rock and blues artists are the ones with less collaborations between the top artists of our created network. It has been interesting to realize that both three top retrieved artists from blues genre were all born before the 40's, which can mean, either that currently, this genre is not really popular or that there are no new popular artists within this genre.


*Analysis of the isolated nodes*


[Add graph]

With the information retrieved, we can say that the genre with more artists without collaborations is *rock*. In fact, more than fifty artists of the rock genre have no collaborations, which means that 50% of the artists of genre rock do not collaborate with other artists. This measure is quite significant to determine that rock artists tend to just perform their own music.

Rock genre is followed by blues and indie, which have around 40 isolated artists. While, on the other side, pop and hip-hop are the genres with less non-connected nodes. It means that around 95% of the artists of both, pop and hip-hop genre have collaborated with at least one of the other top artists.


## Number of times that each artist has collaborated with other artists

We want to also analyze the number of times that each artist has collaborated with other artists. To do it, a second visualization of the graph is displayed below. On it, each node is also colored by genre and the size assigned to the node is the weighted degree of each one.

[Add picture]

### Main characteristics of the structure of the network

* *Undirected* graph
* Node: Artist inside the top 100 of each 7 genres
    * Name attribute for each node
    * Node color based on genre
    * Node size based on the weighted degree of the node
* Edge: Collaboration between artists
    * Edge weight: Number of times that they have collaborated in different songs

**Main information abstracted from the network created:**

* Number of nodes: 609
* Number of edges: 2163
* Number of isolated nodes: 160

**Main outcome abstracted from the network:**

* Same relations between nodes as before
* Within each genre there are one or a group of few nodes that are considerably bigger respect to the other ones.
* There is a big node, which represents an artist within the mixed genre.
* Even blues artists seemed to do not have collaborated with many other artists, they have collaborated many times with the same ones.Their calculated weighted average is much higher than many other nodes that have more connections.

To obtain a more accurate information related to the significant weighted degree values of each node of our network created, the three artists per genre that have a higher weighted degree value are displayed.

| The top 3 nodes with highest weighted degrees |                   |                                    |                                      |
|-----------------------------------------------|-------------------|------------------------------------|--------------------------------------|
| Pop                                           |   Gucci Mane 494  |            Lil Wayne 276           |              Future 242              |
| Hip-hop                                       |   Gucci Mane 494  |            Lil Wayne 276           |             Rick Ross 247            |
| Country                                       | Willie Nelson 145 |         Waylon Jennings 79         |           George Strait 47           |
| Blues                                         |  Eric Clapton 118 |           Janis Joplin 78          | Big Brother & The Holding Company 78 |
| Indie                                         |      Wale 114     |             Jeremih 66             |           Anderson .Paak 54          |
| Rock                                          |   Tom Petty  88   | Tom Petty and the Heartbreakers 80 |         The Rolling Stones 33        |
| Soul                                          |   John Legend 51  |            Jamie Foxx 43           |             NxWorries 35             |

*Main Conlusions*

At first glance, the values calculated for the weighted degree are much higher in comparison to the previous ones calculated for the degree.

We can easily recognize the previous bigger node within the mixed genre as the Gucci Mane. After having a look at his Wikipedia webpage, we can say that Gucci Mane has released more than 12 studio albums, over 70 mixtapes and it was also stated that he has collaborated with many well-known artists, such as Drake, Lil Wayne or Ariana Grande. The three of them are also included in our study and classified within hip-hop or pop genres

Furthermore, we can also realize that hip-hop and pop artists are still the artists that have collaborated more times with other artists. But, this time, the order of the values retrieved is not the same as the one obtained before. And, on the other side, soul is still the genre where the artists have collaborated fewer times. Finally, we can also realize with numbers that within almost all genres there is one node that has a much higher number of collaborations than the other ones.

## Number of unique songs in which each artist has collaborated with other artists

Before continuing with the centrality analysis of our network, we calculated the exact number of songs in which the artist has collaborated with other artists. Until now, we had the number of collaborators for each unique songs, but we could not differentiate if one song was created for more than two artists or not. That is why we are showing how the top artists per genre that have collaborated in more number of songs with other artists.

| The top 3 nodes with highest unique songs |                   |                                    |                                      |
|-----------------------------------------------|-------------------|------------------------------------|--------------------------------------|
| Pop                                           |   Gucci Mane 461  |            Lil Wayne 257           |              Future 218              |
| Hip-hop                                       |   Gucci Mane 461  |            Lil Wayne 257           |             Rick Ross 219            |
| Country                                       | Willie Nelson 141 |         Waylon Jennings 78         |           George Strait 47           |
| Blues                                         |  Eric Clapton 118 |           Janis Joplin 78          | Big Brother & The Holding Company 78 |
| Indie                                         |      Wale 102     |             Jeremih 63             |           Anderson .Paak 52          |
| Rock                                          |   Tom Petty  88   | Tom Petty and the Heartbreakers 80 |         The Rolling Stones 33        |
| Soul                                          |   John Legend 51  |            Jamie Foxx 39           |             NxWorries 35             |


*Main conclusions*

It can be recognized that the artists retrieved per genre are the mainly the same ones than before. This means that most of the artists tend to collaborate in pairs for the different songs created. In fact, for the top rock artists the values have not changed, which means that all the songs were in pairs. While the genres that have changed the most are again pop and hip-hop.

## Centralities

To obtain deeper information of the artists, a further analysis on the centrality of the nodes has been developed.For each centrality calculated, a visualization network and the top results calculated have been shown.

### Betweenness centrality

[Add graph]

[Add table]

**Main outcome abstracted:**

* There are around seven nodes that seem to be more influential.
* There is a rock artist that seems to be the most influential one on the whole network, followed by a hip-hop artists, three country artists and two mixed genre artists. 
* The isolated or low connected nodes have a very small value of betweenness centrality.
* The most influential node of the network is Elton John. It is followed by Snoop Dogg, country artist.
* There are artists that even they do not have a lot of numbers of collaborations and connections on the node, they are considered the most influential artists of the network. So, if we would be artists, maybe it could be a good idea to think on them to do our next collaboration if we want to arrive to more public.


### Eigenvector centrality

[Add graph]

[Add table]

**Main outcome abstracted:**

* The artists considered as more influential are the ones with higher eigenvector centrality.
* The most influential artists are artists from mixed, hip-hop and pop genres. 
* In fact, the artists of the mixed genre seem to have a slightly higher value calculated. So we can say that artists of these genres tend to do more collaborations than the other ones.
* We can identify Gucci Mane as the most collaborative artist of our network.
* Blues artists are the less collaborative ones.

## Degree distribution per genre

The distribution of collaborations between the artists of our network is calculated to 
check which is the genre that tends to have more artists that collaborated with other ones. A table with the total number of collaborations per genre is also shown.

[Add plot]

|         | Number of collaborations |
|---------|--------------------------|
| Hip-hop |           6676           |
| Pop     |           5896           |
| Blues   |           1049           |
| Country |            964           |
| Indie   |            913           |
| Soul    |            658           |
| Rock    |            589           |

With the plot and information displayed, we can confirm that *hip-hop* and *pop* artists are the ones that have collaborated more times with other artists. And, on the other side, there are *soul* and *rock*.


## Communities detection

At this point, we would like to see if artists of one same genre, tend to collaborate with artists of the same genre or to different ones. To do it, we have found the different communities in our network and we will see if exists a correlation with the genres assigned to each node. A graph visualization with the nodes showed by community and a confusion matrix are showed below.

[Add graph]

[Confusion matrix

**Main information abstracted from the communities created:**

* 181 different communities have been created to define our network
* Unfortunately, 167 of this communities only hold a unique artist, which means that all isolated nodes and a few more have been related to any other similar node.
* Just the first 18 communities have been displayed on the confusion matrix.
* Almost all *country* artists are contained within the same community. This is because, as we previously visualized, almost all country artists are connected between them because they tend to have collaborations between them. 
* *Rock* artists are distributed in many different communities, as most of their artists do not have collaborations with other artists.
* There are three partitions - 2, 3 and 7 - that relationate quite a huge amount of nodes. These main partitions contain artists from almost all genres, which can mean that there are quite a lot of artists that tend to collaborate with artists that are classified in other genres. 
* There are two partitions - 0 and 7 - that are mainly formed from artists of pop and hip-hop genres. This reaffirms again that there is a significant link between the pop and hip-hop genres.


## Additional information

* **Friendship paradox** has been true 61.08 % of the times on our created network
* **The coefficient of assortativity** calculated for our network is 0.28. As the calculated value is more close to 0 than 1, we have to say that our network tends to be non-assortative. This means that the artists of our network do not tend to collaborate with other artists that have collaborated with a similar number of artists.

## Cliques analysis

Finally, we have evaluated the information provided by the cliques to try to find similar artists from their collaboration information. The hypothesis that we were trying to implement here was:

 > *"There is a huge probability that I like artists that have collaborated with my favorite artist"*

Or even more,

 > *"There is a huge probability that I like artists that are completely connected with artists that are completely connected with my favorite artist"*

Due to the fact that a clique is defined as a subset of vertices of an undirected graph such that they form a completed subgraph, we would like to use this information to create a small recommendation system with the information retrieved from the calculated cliques of the network.

Before doing that we have retrieved some useful information regarding the cliques of our network. More concretely, the number of different cliques of our network has been calculated in addition to the number of artists that form the largest clique.

* The number of different cliques calculated for the whole network is 2090
* The number of artists that form the largest clique of the network is 12

An example of clique calculated is shown below.

[Add picture]

## Recommendation system

The bases for a recommendation system of artists based on the information retrieved by the cliques of the network has been created. More concretely, two approaches have been developed.

The recommended artists for the artist *Ed Sheran* using our first approach are showed below.

[Add picture]


The recommended artists for the artist *Ed Sheran* using our second approach are showed below.


[Add picture]

