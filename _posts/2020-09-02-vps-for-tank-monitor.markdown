---
title: "Using a VPS to Host a Web App"
layout: post
date: 2020-09-02 01:44
headerImage: false
category: blog
author: cristynhoward
description: ""
externalLink: false
tag:
- Fish Tank Monitor
- Backend
- Node
---

So, I’m planning to measure the temperature (and potentially the pH and dissolved oxygen) in my fish tank using a micro controller and sensors, send the readings to a cloud database, and render them in a GUI accessible over the internet. 

The project includes a diverse array of tasks, including:
* setting up the microcontroller to take readings, then setting it up to securely take commands and transmit data via an API over the internet 
* storing readings in a database
* designing and implementing a dynamic GUI to display readings
* user authentication (important if I want to be able to change settings on the tank’s hardware over the internet in the future, though I’ll be the only user)
* setting my VPS up to handle incoming web traffic, and run the web app and various services

I’m aware that this outlined project is not the easiest or most straightforward way to build a digital thermometer that stores and displays past readings. I’ve chosen to approach the project this way because it’s truly “full stack” in that I’ll be doing everything from front-end web development, to database management, to server-side architecture, to micro controller programming. Essentially, I’m doing the project this way because it will exercise my skills as a software engineer. The complexity is the point.

This blog post is about the last two bullet points on the list of tasks for this project: configuring my VPS to handle web traffic and serve the web application. 

Now, I understand that whenever you expose anything to the internet, you are essentially opening a portal to hell in terms of security, so one of my main concerns when approaching this task was providing a layer of abstraction between the actual web application I was going to have running and the web traffic requesting its content.

I learned pretty quickly that a reverse proxy server would serve this purpose quite well. It would act as an intermediary between the application and the traffic in search of it, allow me to log the traffic hitting my server, handle things like SSL certification, and afford me the opportunity to set up some basic DDOS protection.

So, I installed nginx on my droplet, and then I followed their documentation to set up a reverse proxy server.

Ok, well, I admit, it was a little more complicated than that. 

In truth, the very first thing I did was buy a sweet domain. Did you know .fish domains are a thing now? If there’s ever an appropriate use for a .fish domain, it’s a web GUI displaying data from an actual fish tank.

After buying a domain I had to create A and CNAME records on the DNS servers, and then wait for those changes to propagate.

In the mean time, I installed nginx on my droplet, and set up a server block for my domain. By the time I had finished this, my DNS records had propagated, and nginx was serving a static default webpage over HTTP when I entered the domain in my browser. The next step was configuring SSL certification for the nginx server. After this, my reverse proxy server was ready to start serving up some actual content.

I’ve worked with node and express several times now, and I knew it’d be appropriate for this project to begin with an express helloworld. So, on my local device, I made an express application with some simple default pages: the landing page and the user login page. Once I had something barebones up and running on my local machine, I pushed it to a private repo and cloned that repo to my VPS. Finally, I installed node on the VPS and verified that the application ran on the machine.

The next problem to solve was keeping the node application running reliably on the server while I wasn’t there to babysit it. For this, I chose PM2. Installing PM2 and configuring my node application to run as a process on startup was straightforward. 

At this point I had a basic hello world running, one that would stay running even if I restarted my VPS, and one that was being served to requests for content at my domain over SSL via a reverse proxy. Pretty neat, eh? I’ll admit, it was kind of disappointing that the only visual payoff for my work up until this point is a simple landing page that loads without errors, and a tiny little padlock icon in the browser’s URL bar. That’s what I get for starting with server-side stuff.

Now, I’ll be the first to point out the solutions I’ve chosen to implement aren’t the only ones I could have used, nor are they the best ones for all circumstances. One issue is the lack of development/deployment workflow. Right now, if I want to test changes in the production environment, I may have to stop the application, restart it with the updates, verify that it works, and if not, manually restore it. That means there’s the potential for downtime, and I can’t guarantee continuous delivery. Another limitation of this setup is that it isn’t scalable. Development of the application hasn’t been isolated from the server’s operating system, so it can’t be deployed in different environments without manual set up. And my VPS isn’t that powerful, so I’m not even making use of PM2’s built-in cluster mode and load balancing.

The important point is that this is a hobby project with exactly one user: me. If the application is down, that’s because I, the only user, am actively working on it. And while there may be the occasional traffic to the planned demo page with dummy data, there will only ever be one active user session at a time — mine. So none of these problems are serious enough in my situation to warrant spending the time to engineer solutions for them. However, I feel it is important to note that if I was building this to be production-ready in an enterprise context, I would have made vastly different choices. 

So, what’s next for this project? Well, I’m currently comparing specs for different micro controllers, and when I start fiddling with the hardware, I’ll make another blog post about it. 

Because I want to wait to develop the GUI until after I have the hardware, data storage, and user authentication worked out, the node application running on the VPS is going to serve as a placeholder for the time being.

But if you want to check out what I have so far — verify that the placeholder application is served without errors and with a tiny little padlock icon in the browser’s URL bar?

Go to [checkonmy.fish][1]!

[1]: https://checkonmy.fish