---
title: "Minimax AI: Alpha Release"
layout: post
date: 2018-07-17 01:44
headerImage: false
tag:
- Connect Four
- Twitter
- Bot
- AI
category: blog
author: cristynhoward
description: "Alpha version of single-player mode for @BotConnectFour released."
externalLink: false
---

The first type of @BotConnectFour AI opponent I've chosen to implement is based on a Minimax algorithm. Rather than trying to re-explain the wheel, [here][1] is a pretty comprehensive explanation of the Minimax algorithm, and what it looks like implemented in the context of Connect Four. 

Based on the above-linked tutorial, and the [Wikipedia article for general Minimax algorithms][2], I've begun developing a minimax algorithm.

The current code works. You can play a game of Connect Four with it. But it still occassionally does stupid things that it shouldn't do.

I have to sit down with it, debug it, and improve it. It's a working version. But it feels like a shame to have it sitting here, hidden and unloved, capable of playing decent games of Connect Four, waiting for me to find time to perfect it. So I wanted to hook a working version up to @BotConnectFour, and share my progress.

It took me a little while to hook it up because, before doing so, I wanted to develop a better testing framework to allow changes to my existing code to be verified before being pushed to the VPS. It's something I should've done from the get-go -- really, I should've designed my code from the bottom-up with testing frameworks in mind. But remember, when I started this project, I wasn't sure if it was going to ever turn into a real tool that people can see and use. Now that it is, I needed to feel confident pushing big changes to the tweet processor code into production.

Anyways, here's the current working implementation of the minimax algorithm. It's pretty barebones, and I built it to work directly on top of the existing ConnectFourGame module. And yes, it's still buggy.

{%highlight python%}
def minimax(game, depth):
    """ Chooses the next move in a ConnectFourGame.

    :param game: The ConnectFourGame to choose the next move for.
    :param depth: The number of layers to iterate the Minimax search.
    :return: The next column to play in. 1-indexed.
    """
    best_score = -1001
    best_moves = []
    moves = {}
    i = 1

    while i < 8:
        if game.get_val(i, 0) == 0:

            copy_game = ConnectFourGame.game_from_string(game.game_to_string())
            copy_game.play_turn(0, i)

            score = 0
            if copy_game.game_won == 1:
                score = 1000

            else:
                if depth > 0:
                    opponent_move = minimax(copy_game, depth - 1)
                    copy_game.play_turn(0, opponent_move)

                    if copy_game.game_won == 1:
                        score = -1000

            moves[i] = score

            if score > best_score:
                best_score = score
                best_moves.clear()

            if score == best_score:
                best_moves.append(i)

        i += 1

    return best_moves[random.randint(0, len(best_moves) - 1)]
{%endhighlight%}

I'm not going to change the bot's instruction page until I'm ready to actually release 1-player mode, so I'll share instructions for how to access this "Alpha" feature here.

To play 1-player game, tweet "@BotConnectFour new singleplayer".

If you've already tweeted that once, and try to do so again to start a second single player game, Twitter might return a duplicate status error saying something to the effect of "Status already sent." In that case, you can add a space after "singleplayer" and add any additional characters that you want. So, for example, "@BotConnectFour new singleplayer please and thnx" is a valid command to start a new single player game.

The bot should respond with a board that the AI has already played one turn in. From there, gameplay is the same as in two-player mode. 

[1]: https://roadtolarissa.com/connect-4-ai-how-it-works/
[2]: https://en.wikipedia.org/wiki/Minimax
