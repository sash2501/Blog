---
title: "GSoC’ 20 Progress: Week 1 and 2"
author: Sashmita Raghav
date: 2020-06-15 17:40:00 +0530
categories: [Blogging]
tags: [gsoc]
---

Greetings!

It’s been two weeks since the coding period began and I would love to share with the community the progress I have made so far. 

In the past two weeks, I focused on implementing a basic class for handling subtitles.

First, I created a class called SubtitleModel. This class would contain the list of subtitle content included in the uploaded subtitle file. Since the SubtitleModel class would be utilized to implement a basic model based upon a list of strings, the QAbstractListModel provided an ideal base class on which to build. Subtitle files are usually of two basic formats: SubRipText file (.srt) and SubStation Alpha (.ass) type. Subtitles are maintained in these files in totally different formats based on their file type, so the function ought to parse through each file type in a distinctive way.

In the first week, I worked on composing a parser function for parsing the SRT format file and the SSA or ASS format file provided by the user. As of now, the parser parses through the .srt or.ass file and extricates the subtitle data like the subtitle text and its starting and ending timings. 

```
void parseSubtitle()
```

Next, I worked on composing the addSubtitle() function to add the accumulated data to the list model.

```
void addSubtitle (GenTime start,GenTime end, QString str)
```

I included many more fundamental functions like getModel() which returns a shared pointer to the Subtitle Model, and rolenames() and data() functions which help in returning values of the objects within the list based upon the custom roles. 

```
static std::shared_ptr<SubtitleModel> getModel()
```

In the forthcoming weeks, I will work on implementing a  Subtitle QML track in order to display the positions of the subtitles in the timeline.

The code can be viewed here(https://invent.kde.org/sassycode/kdenlive/-/commits/subparser).

That’s all for now, please stay tuned to my progress in upcoming posts.

~ Sashmita Raghav
