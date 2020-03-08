---
title: "Season of KDE"
date: 2020-01-21 11:33:00 +0530
categories: [Blogging]
tags: [kde]
---
## Season of KDE 2020 - Contributing to an organisation for the first time!

I was introduced to a whole new world of Open Source and version control systems a few months back and I have come a long way from there. I made my first pull request in October, worked on my own project in November , took part in Season of KDE 2020 in December, worked on my SoK project in January and now, I am happy to say that SoK is finally over!

I learnt a lot during the coding period and would love to share my journey. 


### My Season of KDE Journey


#### Week 1: Building the Development Environment

The first thing that one has to do before beginning to contribute to an organisation is build the code of the application from the source. And if this is the first time a person is building any app then he/she  should be ready to do a lot of googling and praying for the cmake to compile successfully.

Kdenlive works with the help of a lot of dependencies and libraries. For the cmake to compile properly the system should have all these libraries installed in it. 

First things first, I got the kdenlive source code from the gitlab instance of KDE, invent.kde.org. It is always best to checkout from the master to a new branch in order to prevent committing incorrect changes and spoiling your whole branch. Then I created a build file and ran the cmake code. This returned a LOT of errors when the required libraries and dependencies were not found in my system. Most of the errors were solved when the following command was executed:


```
sudo apt-get build-dep kdenlive
```


This installed most of the required dependencies. However, during cmake since the errors were still there, I checked for the version required for the particular dependency, googled it, and installed it.  This is what took a lot of my time as I went through what is termed as “dependency hell”.

Either the application used an older version of a particular installed dependency or my system had an older version of the required library. This [blog](https://community.kde.org/Kdenlive/Development#Installing_dependencies) as well as [this one](https://community.kde.org/Kdenlive/Development/KF5) were very helpful.

Finally I changed my OS to kde neon dev edition and all the errors got corrected.

Next step was to  build and install the application using make and make install. After Kdenlive was successfully installed I could finally open the application.

After setting up the development environment, I started going through the source code to understand how different components of the timeline work.


#### Week 2: Working on Title Clips

During Week 2, I dived right into the source code to get an idea on how the application identifies whether a particular clip in the timeline is of a particular type. As suggested by my mentor Farid, I went through the code related to the timeline in src/timeline2/view  folder. Recently, a change was committed in master related to the target button colors. My mentor advised me to go through that commit to get an idea on how the colors are handled in the source code. 

After much searching and googling , I figured out how to differentiate between different clip types while assigning colors to them.

Since, there already was a difference between the audio and video clips, I tried to understand how the application realised whether a clip is audio or not.

On searching, I found that definition.h contains the Producer enumeration which lists all types of clips. Clips in the application are checked for their type by comparing them against this enumeration.

I added the function that would first check whether a clip in the timeline is of title type or not, then would assign the color that was decided by the community for the title clips.


![talk]({{ "assets/img/sok/oldtitle.png" | relative_url }})

#### Week 3: Hardcoding the colors is a big No-No

Nowadays every application has different themes according to the user’s convenience. Some like dark themes while some like light themes. When one is working on adding a particular color to a component, one should consider how the color would appear in the other themes. This is where I had gone the previous week. I had assigned a particular color to the title color that would remain the same irrespective of the current theme, i.e, I had hard-coded it. WIth the help of my mentor and the Kdenlive community I realised my mistake and searched for different uses of QColor and KColorscheme classes that would rectify this. 

However, the color chosen for title clips was not a default Role in the KColorScheme and could be composed by mixing different default ones. Meanwhile, I worked on adding a function to check whether the clip is of image type image clip and then added Neutral color of the ForegroundRole of KColorScheme class to the Image clip (see below).


![imageclip]({{ "assets/img/sok/imagecolor.png" | relative_url }})
<br>
Neutral color added to Image clip


#### Week 4: Marker Comments

Comment markers are used in the timeline to add comment to clip for a particular time. When the user first added a marker to a particular instant in the timeline, it wasn’t displayed making the user wonder if the feature actually works. He could make the comment markers display by going to the Kdenlive settings. However, this is time consuming. So, I worked on making the markers display by default.

Since the codebase was still new to me, a lot of time was spent trying to figure out how the comments were handled by the timeline. I tried many ways to make it default however none of them seemed to work for me.

With the help of Kdenlive developers, I found out that kdenlivesetting.kcfg deals with assigning default values to any component in the application. I then solved this issue by making the default value true for displaying comment markers.


#### Week 5: Adding color to the rest of the Clip types

During this week, I finally understood how I could combine different default colors of ForegroundRole to form a new color as it is done for the color of the target button.

Using this, I added color to the title clip by combining red (Negative foreground role) and blue (Link foreground role).

I also added a function to identify Slideshow clips and then assigned the color, which is a combination of blue (Link Foreground Role) and orange( Neutral Foreground Role), to it.





![new title]({{ "assets/img/sok/titlemixedcolor.png" | relative_url }})

Title clip after combining the default colors





![slideshow]({{ "assets/img/sok/slideshow.png" | relative_url }})

Slideshow clip after combining colors of image[ neutral] and video [link] clips


#### Week 6: Review

In this final week, I pushed all my changes and requested the developers to review it. After a few minor changes the changes were successfully merged! 


### Conf.Kde.in

During Week 2 , I got the wonderful opportunity to meet the KDE developers of my country, India in the conf.kde.in held in Delhi. I came to know about a lot of cool KDE and open source related stuff in this conference.

I also gave a lightning talk about my Season of KDE project for Kdenlive. Since this was the first time I was attending any conference, giving a talk in one was overwhelming, but went quite well all things considered :p



![talk]({{ "assets/img/sok/talk.jpg" | relative_url }})




![top_view]({{ "assets/img/kdeconf/topview.jpg" | relative_url }})




### The Road Ahead


#### Proxy and Clip Effect visual confirmation

I have started work on adding proxy clip visual confirmation. The user can’t know if a clip has the clip effect or is a proxy clip as there is no thumbnail to show otherwise.

I have gone through the codebase to understand where and how the proxy clip and clip effect is handled and how I could add the ‘proxy’ and ‘clip effect’  thumbnails.


#### Separate Audio channels

The user has to go to the Kdenlive settings each time he/she wants to separate the audio channels in the audio clips. I have started work on adding the option to separate the audio channels directly from the timeline track head.


#### Continue Contributing

I really enjoyed contributing to the KDE community during the coding period of Season of KDE and would love to continue to do so as much as I can.

