---
title: "Connect 4 Twitter Bot"
layout: post
date: 2018-06-26 01:44
image: /assets/images/markdown.jpg
headerImage: false
tag:
- Python
- Twitter
- bot
star: true
category: project
projects: true
author: cristynhoward
description: "Connect 4 Twitter bot written in Python"
externalLink: false
---

[@BotConnectFour][1] is a tool that emulates the board game Connect Four on Twitter.

I made it because I saw a screenshot of two people playing connect four with emojis, thought it would make a cute Twitter bot, and wanted to challenge myself to complete a project working with the Twitter API. Little did I know, I would learn to work with much more than the Twitter API in the process of completing this project, which I document [here][16].

---

## Overview

- [Bot Infrastructure](#bot-infrastructure)
- [About the Game](#about-the-game)
- [How to Play](#how-to-play)
- [Accessibility](#accessibility)
- [Code of Conduct](#code-of-conduct)
- [License](#license)

---

## Bot Infrastructure

[@BotConnectFour][1] is written in [Python][2], and makes use of the [Tweepy][3], [PyMongo][4], and [Emoji][5] libraries.

It is run from a [Digital Ocean][6] Ubuntu 16.04 droplet.

It stores game data in a Sandbox-tier MongoDB instance, hosted with [mLab][7].

Visit [@BotConnectFour's Github repository][8] to review the source code.

---

## About Connect 4

[Connect Four][9] (also known as Captain's Mistress, Four Up, Plot Four, Find Four, Four in a Row, Four in a Line and Gravitrips (in Soviet Union)) is a 20th century vertical strategy game. The earliest apparent version of the game, documented by Robbie Bell, is estimated to be Edwardian, produced c. 1901 - 1910, and is made out of Mahogany, with beech wooden game pieces.

The familiar, yellow plastic adaptation of the game was [invented by Howard Wexler][10], and first sold under the [copyrighted][11] name Connect Four in 1974. Currently the copyright is held by Hasbro, Inc.

The game consists of a a 6 by 7 board design, with 2 sets of color tokens. On each turn, the active player places one token of their colour in one of the 7 vertical shoots. The objective of the game is to connect four tokens of your colour in a vertical, horizontal, or diagonal line before your opponent does.

---

## How to Play

1. START: mention @BotConnectFour in a new tweet, type the word "new" followed by a space, & then mention the user you want to play a game with.

2. PLAY: on your turn (indicated by "UP!" beside your name), reply to the board with the number of the column you want to put your piece in.

3. WIN: when you get 4 in a row!

Inactive games are deleted after 14 days.

---

## Accessibility

@BotConnectFour accepts only Arabic numerals as player inputs.

Unfortunately, due to the highly visual game-play, @BotConnectFour is not accessible to Twitter users who rely on text-to-speech software.

---

## Code of Conduct

* Users of @BotConnectFour are subject to the Twitter [Terms of Service][12] and must follow the [Twitter Rules][13].

* Users are prohibited from using @BotConnectFour to harass or annoy other Twitter users with repeated, unwanted game requests.

* Users are prohibited from using @BotConnectFour to circumvent another Twitter user's block settings and deliver unwanted notifications.

* CoC violations may be reported via [Twitter Direct Message][14] to @BotConnectFour.

* Users who violate the CoC are subject to blocks from @BotConnectFour.

---

## License

@BotConnectFour's software is licensed under the [MIT License][15].

[1]: https://www.twitter.com/BotConnectFour
[2]: https://www.python.org/about/
[3]: http://www.tweepy.org
[4]: https://pypi.org/project/pymongo/
[5]: https://pypi.org/project/emoji/
[6]: https://www.digitalocean.com
[7]: https://mlab.com/welcome/
[8]: https://www.github.com/cristynhoward/connectfour
[9]: https://en.wikipedia.org/wiki/Connect_Four
[10]: http://www.howardwexlertoys.com/bio/inventing-connect-four/
[11]: https://tsdr.uspto.gov/#caseNumber=73019915&caseType=SERIAL_NO&searchType=statusSearch
[12]: https://twitter.com/en/tos
[13]: https://help.twitter.com/en/rules-and-policies/twitter-rules
[14]: https://help.twitter.com/en/using-twitter/direct-messages
[15]: https://github.com/cristynhoward/connectfour/blob/master/LICENSE.txt
[16]: https://cristynhoward.github.io/building-bot-connect-four/