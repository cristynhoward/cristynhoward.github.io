---
title: "This Week in Workshops"
layout: post
date: 2018-07-13 01:44
image: https://cristynhoward.github.io/assets/images/skyline.jpg
headerImage: false
tag:
- workshop
category: blog
author: cristynhoward
description: "Recount of my week attending engineering workshops."
externalLink: false
---
<meta name="twitter:image" content="https://cristynhoward.github.io/assets/images/skyline.jpg" />

I've started trying to take full advantage of (a) the booming tech community in Toronto and (b) the extracurricular services offered through the University of Toronto by making an effort to fill my schedule with free and low-cost engineering workshops and talks.

This week, I attended two workshops: the first was a two-hour Mobile App Development workshop run through University of Toronto libraries, and the second was a three-hour Google Assistant Voice Technology workshop run by VoiceTech.TO.

The length of these workshops sound significant, but I found that they moved too quickly and were too short to get deep into the subject matter at hand. Still, I found them beneficial -- if only to get gears turning in my head, and to introduce me to the tools and resources needed to dive in on my own.

---

The Mobile App Development workshop took place in [MadLab][1] in the Gernstein Science Information Center. Overall, I think the most valuable takeaway from this workshop was that mobile app development is much more accessible to me than I had realized. Going in, I was under the impression that I was in completely foreign territory. I learned that that is absolutely not the case! There are tools that lower the barrier of entry to mobile app dev: [XCode][2] is basically an IDE for developing iOS apps, and [Keynote][3], a program that ships standard with MacOS, has extensive [UX mockup features][4]. It's also not necessary to learn a new language, such as Swift, to begin building mobile apps -- there are ways to build [iOS apps in Java][5] and Objective C. We were also introduced to [Apache Cordova][6], a framework that allows for what are essentially web apps written in HTML/CSS/JavaScript to be compiled simultaneously into Android and iOS app bundles. Introduction to these tools, combined with the newfound confidence that mobile app architectures are within my realm of understanding, give me everything I need to get started with mobile app development. Now all I need to do is settle on an idea, and set aside the time. 

---

The second workshop, the Google Assistant Voice Technology engineering workshop, was run by [VoiceTech.TO][7], and was hosted in [the Atrium][8] at CBC headquarters in downtown Toronto. It was sponsored by CBC, so there was pizza and coffee and drinks, and the speaker, [Nick Felker][9], was a representative of Google. The event was part CBC trying to recruit tech talent, and part Google trying to inspire more devs to build Google Assistant integration into their products. Still, it was a valuable learning opportunity. The presentation went over the basics of how the Google Assistant NLP AI parses commands into various components, such as device type, device location, device trait, and desired state. We went over the types of [Smart Home 'intents'][10], including syncing devices, executing commands, and querying device states. We were briefly introduced to some places where we can find tools and resources, the most valueable of which (IMO) being the [extensive roster of Google code labs][11] -- short, hands-on tutorials for workng with a wide variety of Google's products and services.

Then, for the second half of the workshop, we went through the [Smart Home Washer][12] code lab. I think this part of the workshop was the most valuable, for a number of reasons. First, the lab requires working with [Firebase][13]. Firebase was briefly mentioned at the end of the Mobile App Development workshop, but in using it hands-on, it became apparent just how useful Firebase actually is. It basically integrates a bunch of services (such as a VPS, a cloud database, usage analytics, crash reporting, etc.) into one platform with a free tier! The code lab was also valuable in that it gave me an opportunity to reverse-engineer some node.js code, and to practise typing some myself. I'm still teaching myself node.js, so the opportunity to dive right into the backend of someone else's node app was illuminating. Finally, working through the Smart Home Washer tutorial gave me the opportunity to see what it looks like when Google Assistant NLP meets IoT technology in a cloud-to-cloud architecture. I got to watch in real time as my spoken commands were parsed and instantly transmitted into state changes in a cloud database. Pretty neat.

<img class="image" src="https://cristynhoward.github.io/assets/images/voicetechdemo.gif" alt="GIF of using Google Assistant to talk to a cloud database.">
<figcaption class="caption">Demostration of Google Assistant talking to Cloud Database.</figcaption>

---

All-in-all, these workshops were super worthwhile. I'm glad I went! If you live in a city with a tech community, I would encourage you to see if there are any local events or meetups that you can go to!

Believe it or not, I have several more workshops scheduled for the upcoming weeks. I'll likely want to reflect upon them in future blog posts, so keep an eye out for them!

[1]: http://mobile.utoronto.ca
[2]: https://developer.apple.com/xcode/
[3]: https://www.apple.com/ca/keynote/
[4]: https://www.lukew.com/ff/ff/entry.asp?1155
[5]: https://medium.com/@mateusz_bartos/write-ios-apps-in-java-along-with-android-900d6013f83f
[6]: https://en.wikipedia.org/wiki/Apache_Cordova
[7]: https://www.meetup.com/voice-tech-to/
[8]: http://www.cbc.ca/productionfacilities/toronto/atrium
[9]: http://nickfelker.me
[10]: https://developers.google.com/actions/smarthome/
[11]: https://codelabs.developers.google.com
[12]: https://codelabs.developers.google.com/codelabs/smarthome-washer
[13]: https://en.wikipedia.org/wiki/Firebase



