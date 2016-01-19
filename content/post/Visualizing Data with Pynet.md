+++
date = "2015-12-31T17:43:56+01:00"
description = ""
title = "Visualizing Data with Pynet"

+++

# My first work visualizing Twitter data with Python and Gephi

#### Edit: here's the [link](https://github.com/blayhem/pynet) to my work.

About a week ago I read [this](https://www.reddit.com/r/dataisbeautiful/comments/3y5t1t/i_visualized_my_instagram_connections_oc/) reddit post, where user [Trevor Prater](https://github.com/trevorprater) did this curious job about data visualization with his Instagram network:

![Instagram connections](http://i.imgur.com/t6JShXt.png "Trevor Prater Instagram Connections")
([This](https://github.com/trevorprater/wholikes) is the repository with the code).

As Trevor said in the post comments:
> Using the Instagram API and the networx library (Python), I constructed a graph of the connections between my followers, their followers, the people they follow, the people I follow, the people that follow the people I follow, and the people that are followed by the people I follow. I then exported the networx graph as a GraphML file and loaded it into Gephi.

[Yo dawg](https://en.wikipedia.org/wiki/Semantic_satiation).

### My project

To plot a graph with my twitter connections, represented by my followers and their common followers with me. That is, all the people which is not also connected with me but also between them (mutually).

Python was a requirement if I wanted to follow Prater's steps, but I also wanted to learn Python anyway, and this was the perfect opportunity.

### Starting: I have no idea of what I'm doing

*Note: this was the first time I wrote anything in Python. As all the work I'm doing recently, the main objective with this was to get out of my comfort zone and learn something new. I love Python now, but I can't say the same for the Twitter REST API.*

I worked all the time with [Pycharm](http://jetbrains.com/pycharm), the Jetbrains IDE for Python. The first logical step was to document myself about [Networkx](https://networkx.github.io) and the [Twitter REST APIs](https://dev.twitter.com/rest/public).

There was a huge problem regarding the API: the **rate limiting**. My script needed to perform a query of all my followers' followers, and the API only allows 15 queries of *GET followers/ids* for every 15 minutes.

My ~~ñapa~~ solution: do a 1min delay before every query, so that after 15 queries (15min) the rate limit does not affect. **That is, a little more than 4h for my twitter account, with only 245 followers when I wrote this lines**. Yumm.

I also created a Twitter application (netpy) at [Twitter Apps](https://apps.twitter.com) to get the tokens for the queries, and a [second twitter account](https://twitter.com/pynet_) with less followers, for testing purposes.

After 4 hours running the script and creating the graph with Networkx, I exported all the data in a gexf file, to be opened with Gephi.
There, I colored the nodes by degree and rearranged them.

## Final result

![Round graph_final result](/static/pynet/curved.png "Round graph_final result")
(Round edges)

![Straight graph_final result](/static/pynet/wo labels.png "Straight graph_final result")
(Straight edges)

There are three main "clouds" of connected nodes, representing my friends in Zaragoza (left), my UC3M friends (upper right), and a few from Ciudad Real (lower right).

#### Edit2: I ran the script again with my GF's Twitter account (~720 followers). The results were even better:

![Straight graph_final result](/static/pynet/gold.png "Straight graph_final result")

#### Other links I found useful

[Set operations in Python](http://www.linuxtopia.org/online_books/programming_books/python_programming/python_ch16s03.html) (thanks, [Alex](https://github.com/alexrs95)!).

[John Keats Poems: graphing words w/ Networkx and Python](https://paulcrickard.wordpress.com/tag/gephi/).

[Gephi: introduction to Network Analysis and Visualization](http://www.martingrandjean.ch/gephi-introduction/).

Also thanks to my friend [Javier Honduco](https://github.com/javierhonduco) for the Python and Twitter API tips.
