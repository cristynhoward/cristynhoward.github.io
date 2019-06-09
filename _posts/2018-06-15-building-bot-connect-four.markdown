---
title: "How I Built the Connect 4 Twitter Bot"
layout: post
date: 2018-06-27 01:44
headerImage: false
tag:
- Python
- Twitter
- MongoDB
category: blog
star: true
author: cristynhoward
description: "Here I recount the process of building a Twitter bot."
externalLink: false
---

I recently built [my first Twitter bot](https://cristynhoward.github.io/bot-connect-4)!

Having never built a bot before, the process of bringing one to completion took me on a winding journey, full of new tools and interfaces.

Once I started, it became a challenge to myself to complete the task and get the bot working. 

This essay is my retroactive attempt to chronicle my exploration, discovery, and construction process.

---

My bot journey began, as many journeys begin, with an idea. I’d seen a screenshot of two people playing connect four with emojis, and I thought it would make a cute Twitter bot. I was surprised to discover, upon searching, that no one had already made such a thing. 

Twitter is full of art bots that have fascinated and inspired me, and I had long wanted to get in on the action and make one myself. Now I had an idea for a great bot - one that adds features to the Twitter experience, and one that follows [good bot etiquette][1] by design. I went with my idea, and started to build.

When I first started working on the bot, I had no idea where to begin. I had only a vague idea of what VPS services were. I had never worked with the Twitter API before. I turned to [several][2] [Twitter][3] [bot][4] [tutorials][5] to help break the ice and give me some ideas about what I could do to get started. 

Being incredibly reluctant to share credit card details with VPS services I didn’t know how to use, just to work on a project I wasn’t even sure I could finish, I quickly decided that hosting my bot on Glitch was the best option available. Upon reading more about how Glitch works under the hood, I realized that it was unwise to trust Glitch to keep an app constantly active. I began planning to build a bot on Glitch that runs via a script triggered at regular intervals.

The thing is -- I'm a beginner at working with node.js. When I started building a node.js server on Glitch, I quickly realized that working with the node.js syntax would slow my progress. I was eager to get started, and wanted to work with something more familiar. Thankfully, [Glitch unofficially supports Python][6]. And I know Python, rather well. So, the very first thing I did to get my bot running was teach myself how to set up a [Flask][7] server [on Glitch][8].

Once I had the basic framework set up, and could trigger a Python script by hitting a URL, I could start work on the actual bot code. This is where I ran into my first bot-specific design problem. To work, my bot must respond, in a timely fashion, to users tweeting at it. This requires two separate Twitter API interactions: first the bot must check its mentions for new games and plays on open games, then it must write tweets in response to them. 

Many interactions with the Twitter API are rate limited. In high-volume circumstances, if I attempted to output a response to each mention before processing the next one, rate limit errors on the outgoing responses would affect the ability of my bot to continue processing incoming tweets. At the very least, I would need the ability to store outgoing tweets and send them out separately in case I encountered an outgoing tweet rate limit error. Given that this was already necessary, I quickly decided to completely split up mention-reading and tweet-writing into separate processes. That way, I could control the rate and error-handling of each process separately. 

So, as the first stage of my bot development, I produced code that would check the bot’s mentions, store a pre-written, outgoing tweet in a text file, and then separately send out the tweet. I set up [UptimeRobot][9] based on several recommendations I had seen in bot tutorials, and let my bot run, hands-free. I sent out a test tweet, and, after waiting several minutes - a response. The first sign of life! My first successful interaction with the Twitter API! This basic “mention responder”, the infant stage of my code development process, is immortalized in a Glitch project which can be found [here][10].

Once I had the basics working - a Flask server that, when pinged, successfully reads and stores responses to mentions, and that when pinged at a different URL, sends out those responses - I was able to start work on the game code. I wrote and tested most of the code currently found in [ConnectFourGame.py][11] as the second stage of bot development, keeping in mind the ways in which it would need to integrate with the I/O module. 

Because of design choices I had made when developing the game module, integrating it with the code from first development stage was simple and painless. However, when I got to the point where I was testing the integrated code, I was forced to reconcile with two more design problems. 

The first - when automating my bot with UptimeRobot, I realized the the service was limited, unreliable, and slow. I tried setting up ten (10!) simultaneous different read/write URLs to speed up the bot’s response time, but trying to get code to run in a timely manner this way felt a bit like trying to press a button every minute by telling 10 people to stand several meters away and throw rocks at it. Not ideal. It became clear that if I wanted a reliable bot with a quick response time, I would need a VPS. 

So, as the third phase of my bot development, I bit the bullet and did some research into various VPS services. I chose to sign up with Digital Ocean, mostly because they offered a sign-up credit that covered two months of the services I would need to host my bot. The choice to use a Ubuntu 16.04 server was admittedly arbitrary. Next, I taught myself how to set up the server, including firewall settings, SSH permissions, sudo non-root user configuration, and programming environment setup. The final step in the process of getting my code running on the VPS was to learn about cron files, and configure them to run my reading and writing scripts in 20 second intervals.

The second major design problem that I noticed when reviewing the integrated code - storing game data in text files works well when there are very few active games. However, if there are a million active games in storage, even deleting a single entry from the file requires iterating over the entire thing. Thus the worst case running time for storing, reading, and deleting entries from text files scales linearly with the total number of active games. And my bot needs to write, store, and delete two seperate line items for _every turn played_ in each game. Not ideal. It became clear that if I wanted a bot that could handle high volumes efficiently, I would need to use a database. Perhaps this consideration was over-engineering, as it’s wishful thinking that my bot will ever have more than a hundred active games open at any given time. However, the software engineer inside of me wanted to develop something efficient and robust, and using text files for storage felt clumsy.

So, as the final stage of my bot development, I researched and discovered mLab, a “Database-as-a-service” platform that offers a free 500-mb tier (enough storage for 62,500 active games). I identified the appropriate MongoDB driver, and spent some time teaching myself how to use PyMongo to access the cloud database instance. Once I did, I was able to code a few database helper functions now found in [databasehelpers.py][12] to facilitate storing, accessing, and deleting games and outgoing tweets. Then I altered the tweet processing code to store and load tweets and games from the database, and I was good to go. The last step was setting up a “database cleanup” cron job which scans the entire collection of active games once daily, and removes completed and expired games.

And with this, my bot framework was complete. 

<div class="side-by-side">
    <div class="toleft">
    	<p></p>
        <p>I had built my very first Twitter bot! And it was working exactly as I had imagined it. I felt like a magician!</p>
        <p>If you want to play a game, you’re welcome to do so.</p>
        <p>Instructions for how to play, and more information about the bot are available <a href="https://cristynhoward.github.io/connect-four-twitter-bot/">here</a>.</p>
    </div>

    <div class="toright">
        <img class="image" src="https://cristynhoward.github.io/assets/images/botmaker-badge.png" alt="My Botmaker Badge from Botwiki.org">
        <figcaption class="caption">My Botmaker Badge from Botwiki.org</figcaption>
    </div>
</div>

---

What’s next? 

Well, I've got it in my head that 1-player mode would be a fun addition... I've already done some work building AI connect four opponents!

Stay up to date on my projects by following me on [Twitter][14], [Github][15], or subscribing to the [RSS feed][16] of this blog!

[1]: http://tinysubversions.com/2013/03/basic-twitter-bot-etiquette/
[2]: http://blog.mollywhite.net/how-to-create-a-twitter-bot/
[3]: https://botwiki.org/resource/tutorial/how-to-make-a-twitter-bot-the-definitive-guide/
[4]: https://www.digitalocean.com/community/tutorials/how-to-create-a-twitterbot-with-python-3-and-the-tweepy-library
[5]: https://glitch.com/edit/#!/twitterbot
[6]: https://support.glitch.com/t/can-i-run-a-python-app-in-glitch/2140
[7]: https://en.wikipedia.org/wiki/Flask_(web_framework)
[8]: https://glitch.com/edit/#!/flask-hello-world
[9]: https://uptimerobot.com/
[10]: https://glitch.com/edit/#!/mention-responder
[11]: https://github.com/cristynhoward/connectfour/blob/master/ConnectFourGame.py
[12]: https://github.com/cristynhoward/connectfour/blob/master/databasehelpers.py
[13]: https://cristynhoward.github.io/connect-four-twitter-bot/
[14]: http://www.twitter.com/cristyn_howard
[15]: http://www.github.com/cristynhoward
[16]: https://cristynhoward.github.io/feed.xml
