---
title: ":robot::knife: Stabbing Robot"
layout: post
date: 2017-12-17 01:44
headerImage: false
tag:
- Arduino
- hardware
category: project
projects: true
author: cristynhoward
description: "Stabbing Robot made from an Arduino reactive circuit."
externalLink: false
# jemoji: '<img class="emoji" title=":robot:" alt=":robot:" src="https://assets.github.com/images/icons/emoji/unicode/1F916.png" height="20" width="20" align="absmiddle">'
---

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">I made a killer robot. <a href="https://t.co/GvVIQBn7PR">pic.twitter.com/GvVIQBn7PR</a></p>&mdash; ⃝〇˳°. (@cristyn_howard) <a href="https://twitter.com/cristyn_howard/status/942502860939579398?ref_src=twsrc%5Etfw">December 17, 2017</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 

---

After explaining some work I had been doing with the Arduino Starter Kit, a friend joked that I should put my skills to use making an evil killer robot.

And after building several reactive circuits following tutorials in the Arduino Projects book, I wanted to challenge myself to build one without guidance or instruction.

It seemed straightforward to direct a servo to move in response to a shadow overhead, so quickly I came up with the idea to make the Stab Bot 5000!

The first step was writing the code to control the circuit, which you can check out [here][1].

The second step was wiring the circuit to connect the photoresistor and servo to the Arduino Uno via the breadboard. 

After verifying that the code and circuit worked properly, the last step was building a little housing for the servo out of cardboard, tape, and hot glue. After adding an arm, some legs, a grumpy expression, and a deadly weapon, the Stab Bot 5000 was complete!

Now, this circuit design is very simple and has obvious flaws. The most obvious being that the photoresistor and light source need to be set up in just the right positions for shadows to trigger the arm at the right time. 

One fix for this would have been to mount the photoresistor onto the servo housing itself, but that was beyond the scope of this project.

I set out to build a reactive circuit from scratch, and I did! 

Yay!

[1]: https://github.com/cristynhoward/stab-bot-5000/blob/master/stab-bot-5000.ino