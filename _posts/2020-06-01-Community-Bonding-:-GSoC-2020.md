---
title: "Community Bonding : GSoC 2020"
author: Sashmita Raghav
date: 2020-06-01 10:40:00 +0530
categories: [Blogging]
tags: [gsoc]
---


Greetings to all!

A month ago I was selected to participate as a student in Google Summer of Code with Kdenlive. The Community Bonding period is coming to an end and the coding period will soon commence. 

In this post, I am going to talk about what the project is about, how I plan to implement it, and what all I have done in the community bonding period to ensure a smooth and bump-free coding period.
### About the Project

Kdenlive is largely limited in its ability to customize and edit subtitles. At present, subtitles are added as an effect, namely the Subtitle effect, this effect uses an FFmpeg filter to burn the subtitle file onto the respective video.

Basic subtitling support in Kdenlive can be achieved by extending the functionality of the existing “Subtitle” filter, thereby giving users more choices over subtitle customization.
### Planned Implementation
- A class will have to be created to store the subtitle lines with their duration and position in the timeline. All customizations made by the user to the subtitle file like altering the time, text, and color of the subtitles will be handled by this class. 
- Design a user-friendly user interface like a separate QML track for users to effortlessly customize subtitles in their projects.

### Community Bonding Period

First off, I completed a few prerequisites, like applying for a KDE Developer account, adding my blog to Planet KDE, to name a few.

Discussed with my mentors on how I plan to approach the implementation and finalized what I have to do over the course of the upcoming 3 months.

I went through the code base of Kdenlive to understand how the Subtitle effect is handled and how the parameter values of different FFmpeg filters can be manipulated. I also understood the standard method of writing a class used in the application. 

Now that I have better clarity on different aspects of the implementation, I am looking forward to a productive coding period 😀

**Project Overview:** [https://summerofcode.withgoogle.com/projects/#6465764850139136](summerofcode.withgoogle.com/projects/#6465764850139136)

**Project Status:** [https://community.kde.org/GSoC/2020/StatusReports/SashmitaRaghav](community.kde.org/GSoC/2020/StatusReports/SashmitaRaghav)

**GitLab:** [https://invent.kde.org/multimedia/kdenlive/-/issues/666](invent.kde.org/multimedia/kdenlive/-/issues/666)

Stay safe and stay tuned to my progress in upcoming posts.

~ Sashmita Raghav
