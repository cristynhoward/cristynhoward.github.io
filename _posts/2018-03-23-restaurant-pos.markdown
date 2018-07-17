---
title: "Restaurant Order Management Software"
layout: post
date: 2018-03-23 01:44
headerImage: false
tag: software design
category: project
projects: true
author: cristynhoward
description: "Alpha version of single-player mode for @BotConnectFour released."
externalLink: false
---

The capstone project for one of my software design courses was to build a restaurant order management and point-of-sale system. It was completed in two phases: first we completed the backend, then we refactored based on feedback we were given and built out the front end.

The entire project was a realistic experience in that it required working with a team of people with varying work ethic and varying levels of technical skill. In a sense, it was as much a project management course as it was a software design course.

Very early on in the first phase, I recognized that there was a leadership void in our group. I do not feel the need to fill that role, but I recognize what happens to disorganized software projects <span class="spoiler">(spoiler: they fail)</span>, so I made the decision to step up and organize group meetings with all group members, facilitate goal-setting, facilitate work-load distribution, and (try to) keep everything on schedule. 

For me, filling this role productively did not mean steam-rolling people or appointing myself Team Boss, nor did it mean doing everything myself. <span class="evidence">It was about asking the right questions to elicit positive contributions from all of the team members.</span> Questions such as: 
- When can we meet to reach consensus on our high-level design?
- What do we have left to do in order to implement our design before the deadline? 
- What are our priorities? What has to happen first?
- What will take the most time/be the most difficult? 
- What is a fair way to distribute this workload that takes advantage of all of our strengths? 

Having worked through group projects with frantic group members who barely meet deadlines in the past, I was impressed this time around. <span class="evidence">This approach allowed for all of our group members to complete their contributions to our project almost a full week ahead of schedule.</span> We were relieved to be able to let the first deadline come and go without any rushing or stress. It felt like something of a miracle - getting second year university students to surpass deadlines on an intensive group project, when no one is getting paid and no one is anyone else's boss, is like herding cats.

<div class="breaker"></div>

For the second half of the project, our team was shuffled around and re-paired with a different group. We agreed to use our backend moving forward, as the design was easier to understand. The work was split up such that we would collectively work on a high-level front-end design, the new group members (who were proficient with [Scene Builder][1]) would build out the screens based on that design, and the group members who had built the backend would make refactors to it based on the feedback we were given, would produce controller code (basically a formally documented API) for seamlessly hooking up with the front-end, and would help the front-end group members understand and integrate the backend and the API for it. 

It turned out that the group that we were re-paired with happened to be of the "frantic and barely meeting deadlines" variety. Rather than vent about it here, I will simply state that they were unresponsive and uncooperative (one didn't show up to class, our group meetings, or respond to emails for over a month), and by the time the final deadline arrived, their code was incomplete and full of bugs.

The good news is that my contributions to the code base, which met the specifications, passed all of our test cases, stuck to the [SOLID priciples of Object-Oriented design][2], and were refactored based on constructive feedback, earned me an 80 on the project. That's something I'm proud of. 

The bad news is that the code for the project is a little bit hard to showcase, specifically because the repo for the project has restrictive permissions on it, and because the frontend team never completed their work.

In the days before our project presentation, I wrote a command line interface as an alternative to the GUI to demonstrate full backend functionality. At some point I might get around to redoing the frontend code myself to show off the full glory of what the backend is capable of managing. For now though, the command line interface will suffice.

Here's a video of some of the features in action. I'll warn you though, the video moves at a slow pace.

<video controls="controls" width="580" height="435" 
       name="Restaurant Software Command Line Demo" 
       src="http://cristynhoward.github.io/assets/restaurant_demo.mov">
       </video>

<div class="breaker"></div>

Finally, although I received a lot of verbal feedback on my code and design at many stages of the design process, 
I received little personalized, written feedback on the final version. Of that, all I have to share is:

> Cristyn: Your version of the code has a view that is more separate from the
controller and model (MVC). You make good use of the Observer and
Dependency Injection design patterns. It is clear that you have identified
and fixed several bugs [in your groupmate's code]. Implementing an Employee class was a good idea.
Also, your code is clean at the method level.




[1]: https://gluonhq.com/products/scene-builder/
[2]: https://en.wikipedia.org/wiki/SOLID