# autoEdit 2 R&D Documentation for Developers -`1.0.6` - Working Draft

R&D Documentation for Developers for [autoEdit2](/www.autoEdit.io) `v1.0.6`  \(That does paper-editing\).

## Outline the problem
<!-- Outline the problem you are working on, why it is interesting andwhat the challenges are. -->  

For a video producer working on a factual/documentary production, editing video interviews is a time-consuming activity.

In the current work-flow, once the producer has the video file, they would have to find the quotes, which often entails manually scrubbing through the video in search of  usable sound bites, which can be something like finding a needle in a haystack, particularly if the video is lengthy. Additionally, transcriptions are not a viable option either, as often there is no time to wait for them or no budget, and without time- codes, transcriptions do not help to speed up the process.

In a fast paced newsroom often there is no time for such a time-consuming process.

The aim of this project is to produce an application that can maximise not only the depth of content but also the speed in which the content is produced.

The approach was to look at the traditional paper-editing workflow from documentary production, and see how that could translate into a digital world. [For more on paper-editing and how this is used to craft compelling stories out of video interviews, check out the notes from this workshop](http://pietropassarelli.com/wip_london_july2016.html).

## Areas of Interest

One reason why this project is interesting is because it utilises the new possibilities that have opened up with the node ecosystem, that allow for un unprecedented level of code reusability and the introduction of the HTML5 video tag. As well as the opportunities that have arisen in combining this with the increasing quality of speech to text technologies.

Projects such as [NWJS][nwjs] (formerly node-web-kit) allows to use web technology to build cross platform desktop applications that with minimal code change can be ported to a web app version. This also lower the barrier of entry for this type of development.

Traditionally video and audio have been like black boxes on the web, often having to recur to flash to provide video capabilities to pages. With the introduction of the HTML5 video tag, Javascript libraries like videos make it easier to manipulate the video, treating it as a Javascript object. However this turns the video into “a ‘black box’ we can do something with, such as triggering events at defined timecodes. It does not allow us to directly obtain the content of the video in a programmatic way and to manipulate the result. An example would be to take from the video the content of the quote and then analyse this to identify keywords and key topics. Another example would be to search what has been said in the video, find the quote and trim the video segment accordingly. For more of [a discussion of relevant projects that tackle this problem check out this article][beyonblackboxes]

As explored in a previous project, [quickQuote](http://pietropassarelli.com/quickQuote.html), I believe it is by combining video with its corresponding time-coded transcription that we can provide a direct programmatic solution.

## The Challenges

There were two main challenges for this project. The first was centered around investigating the problem of how working with video and transcriptions in the newsroom could lead to an increase of time-consuming multimedia production. The second main challenge was then identifying an appropriate solution.

###  Investigation of the Problem
Investigating and defining the problem was one of the first challenges. The initial problem-hypothesis was formulated around researching ways to make working with video in the newsroom easier and faster. Identifying the set-backs journalists have was difficult because they themselves did not fully know what they were. This is discussed further in the investigation chapter, which outlines how through a series of proof-of-concept prototypes and discussions with journalists and newsroom stake holders, it emerged that a the lack of a system to quickly extract video quotes was the problem and it was the solution to this problem that was the second stage of the challenge.

### A Comprehensive Solution

One of the challenges around this project is providing a comprehensive work-flow for the journalist and the user that is clear and easy to follow through from beginning to end, without requiring any training.

###  Video Transcriptions
The fastest way to be able to quickly select a caption from a video, is to search a transcription of that video. Therefore a challenge was to research and identify the most appropriate system to get the transcription of any given video. Human generated transcriptions were not an option because of time and resource constraints. Automated transcriptions needed to meet a certain threshold of acceptance from the user, as well as have accurate timecodes in order to be searchable and in sync with the video for quick feedback.

###  The Output

The output of the video quote selection system will be a text quote with the corresponding video clip associated with it. This needs to be something journalists can easily add to their news article with minimal or no configuration. The system also needs to be able to cut the original video source to trim it down to the video quote selection as a HTML5 H264 MP4 video.

## Aims and Goals

###  Aims

My aim for this project is to use an R&D approach to identify an appropriate solution to an every day problem; that of using video and transcriptions in the context of newsrooms to facilitate and increase their multimedia production for the web, as well as develop a working web application proof of concept.

Additionally, throughout the process, an aspect of the project became to learn the following technologies:
• Javascript/JQuery to manipulate the DOM to implement the front end logic of the application.
• JSON and AJAX• MVC design pattern of the Rails framework.
• Working with APIs, such as–user authentication with google auth–speech to text API
• Ruby Mine IDE• How to model the domain of the application into back end classes, rails models, efficiently.
• VideoJs and HTML5 Video
• T esting–Acceptance test - Selenium–Unit Test - RSpec• FFMPEG to trim and transcode video.
• Deployment on Deis / Heroku
- Refactoring components from open-source projects that were using hyper- transcript, with videojs and JQuery.

### Goals

The main goal is to build a web application that makes extracting video quotes and publishing them to news articles much easier.Goals for this project are to;• Investigate the problem in the newsroom around working with video and prototype a compelling solution.• build a web application that;• given a video returns a searchable transcription in sync with the video.• allows the user to select quotes–allows the journalist user to preview their quote selection before exporting –cut the video in the background once a quote selection is being exported. –export the video quote clip as HTML5 MP4 H264• produce a set of unit and acceptance tests to make the application as robust as possible.• deliver a system manual• deliver a user manual• provide code documentation• open-source the project.

## Overview of the Project

My personal preference for developing applications is to use a lean agile approach (Eric Ries 2011) to software development, with an initial emphasis on researching and identifying a problem solution, working closely with users and stake holders through proof of concept paper sketches prototypes and research on existing user practices and work-flows. As done during the course of the UCL Msc for GC02 industry project working with the Audava Start-up (Passarelli Pietro et al. 2015) and for the Entrepreneurship module developing an autoEdit application (Passarelli Pietro 2015b).However in the context of newsroom development at the Times and Sunday Times, this was not always possible, as it was required to produce an interactive prototype to demonstrate proof of concepts hypothesis to carry out what would be the equivalent of the “customer development” phase in the lean approach (Maurya 2012).Working within these constraints over the whole project took an iterative approach with three main overarching phases:

### Preliminary Research
Identifying, researching and learning the technology stack. This consisted of becoming familiarised with the Times & Sunday Times development team’s current technology stack.

### Hypothesis and prototype
Investigating the problem domain of the application. Making hypotheses, prototyping and investigating problems and solutions. Confront results with users and stake holders.In this phase, a bottom up approach was used to make a prototype and ensure the core aspects of each component fully worked and integrated as a whole.Once the appropriate problem and solution was identified, this was followed by a rapid prototype phase, to confirm such solution with the users and stake holders, in order to agree on user requirements, before moving on to implementation.

### Implementation

Followed by the final phase of re-factoring and implementation of the web application.In this phase a top down approach was used, with more care put on re-factoring code into components.A more detailed breakdown of the investigation carried out in this iterative process can be found in the investigation chapter.See appendix for outline of phases and internship timeline.


## Context

The context and background research to the project, as well as sources, and similar solutions can be found in [this blog article "Beyond Video as Black Boxes"](http://pietropassarelli.com/videoBox.html).



<!--## Overview of Report

Chapter 1, Introduction The first chapter outlines the problem investigated, the area of interest, aims and goals and gives an overview of the project and the rest of the report.

Chapter 2, Context The second chapter is concerned with providing context and background research to the project, as well as sources, and similar solutions. It also introduces the software.

Chapter 3, Investigation As mentioned, the project was built with an iterative approach, investigating the optimal solution for a system that would allow journalists to work more efficiently with video in their news article publications. This section expands on the different phases of the R&D investigation.12

Chapter 4, Requirements This chapter outlines the requirements for the final iteration of the video quote extractor application, the problem statement, list of requirements, use cases, and result of requirements analyses.

Chapter 5, Implementation The implementation of the application is discussed in this chapter. Design, architecture, components design, database and implementation details.

Chapter 6, Testing An overview of the testing strategy, the use of unit test and acceptance testing is presented in this chapter and a summary of test results.Chapter 7, Conclusion A summary of what the project has achieved, as well as critical evaluation and recommendation for future work.
 -->

---
**TL;DR **:This is meant to be a higher level overview of the structure, parts and components of the application. Focused more on how problem domain issue have been addressed, which options have been tried and considered and what is the current implementation strength and weaknesses. 

The first part is structured a round the 5 higher level parts that make up the app. Each one following this structure:

- Component/part description 
- Related projects. Eg parts that look good, or previous implementations. But have been used for current implementation options. 
- Implementations Options considered
- Current implementation 
- What needs refactoring 

Then it also contains a [roadmap section](/roadmap.md), and a [QA section](/qa/qa-intro.md) to serve as a checklist before every deployment, as well as a series of appendix with more technical info and implementation details relevant to the project , such as for example the [db setup](/current-db-setup.md) and [prerequisite](/prerequisites.md) to mention a few.

--- 

## **Overview of High level Parts**

<!-- TODO: add some kind of diagram -->

It's helpful to discuss the implementation of autoEdit by looking at the parts that make up the whole as stand alone overarching components, that are built of other smaller components and modules.

Tick \(✔\) for features implemented in `1.0.6`**        
**

1. **Transcriptions** ✔

   1. Transcriber ✔

      1. STT✔

      2. Video preview conversion ✔

      3. Metadata info for EDL✔

   2. Hyper-Transcript ✔

      1. Representation video + transcript in sync ✔

2. **Papercuts Selections** ✔

3. **Annotations Tags**

4. **Paper-edit** ✔

   1. Search and filter paper-cuts and transcriptions

   2. D&D papercut in paper-edit ✔

   3. Preview paper-edit ✔

5. **Export**✔

   1. Paper-edit export to EDL✔

## Data structures

Main data structures in the project

* Transcription json 
* paper-cuts json 
* paper-edit json 


## Stack 

If you are not familiar with [Node](https://nodejs.org/en/), [NWJS](http://docs.nwjs.io/en/latest/For Users/Getting Started/), [backbone](http://backbonejs.org/) or not sure were to start to get an overview to familiarise yourself with this project, check out the [prerequisite section](/prerequisites.md) to get an overview of the stack and see the minimum you need to know to get up to speed with this project.

---

## Trello board

Each release has it's own trello baord that gets duplicated/cloned to move on for subsequent releases. [For instance this the trello board for v1.0.6](https://trello.com/b/8LP7y3EI/autoedit-v2-1-0-6-release-paperedit) which will be kept for record, and soon there will be the one to keep track for the next release v`1.0.7`.

Trello board is used for planning and project management. 
Github issues are used for bug handling. 


[nwjs]: https://nwjs.io
[beyonblackboxes]: http://pietropassarelli.com/videoBox.html




