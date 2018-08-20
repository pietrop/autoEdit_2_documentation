# Intro

Working Draft R&D Documentation for Developers for [autoEdit2](https://github.com/pietrop/autoEdit_2_documentation/tree/6a02a8d72f177e127c3fe0b3c3959dbc6f737f13/www.autoEdit.io) `v1.0.12` 

## Outline the problem

For a video producer working on a factual/documentary production, editing video interviews is a time-consuming activity.

In the current work-flow, once the producer has the video file, they would have to find the quotes, which often entails manually scrubbing through the video in search of usable sound bites, which can be something like finding a needle in a haystack, particularly if the video is lengthy. Additionally, transcriptions are not a viable option either, as often there is no time to wait for them or no budget, and without time- codes, transcriptions do not help to speed up the process.

In a fast paced newsroom often there is no time for such a time-consuming process.

The aim of the autoEdit project is to produce an application that can maximise not only the depth of content but also the speed in which the content is produced.

The approach was to look at the traditional paper-editing workflow from documentary production, and see how that could translate into a digital world. [For more on paper-editing and how this is used to craft compelling stories out of video interviews, check out the notes from this workshop](http://pietropassarelli.com/wip_london_july2016.html).

{% embed data="{\"url\":\"http://pietropassarelli.com/wip\_london\_july2016.html\",\"type\":\"link\",\"title\":\"Workshop: How to craft compelling stories out of video interviews? · Pietro\",\"icon\":{\"type\":\"icon\",\"url\":\"http://pietropassarelli.com/public/favicon.ico/favicon-192.png\",\"width\":192,\"height\":192,\"aspectRatio\":1}}" %}

For [an overview of how this has been implemented in autoEdit, from a user's point of view, check out the user manual](https://autoedit.gitbook.io/how-to-tell-compelling-stories-out-of-interviews).

{% embed data="{\"url\":\"https://autoedit.gitbook.io/how-to-tell-compelling-stories-out-of-interviews\",\"type\":\"link\",\"title\":\"Introduction - How to tell compelling stories out of video interviews\",\"icon\":{\"type\":\"icon\",\"url\":\"https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/spaces%2F-LKEX2pgEboHMhySJ5EJ%2Favatar.png?generation=1534637655291617&alt=media\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://www.gitbook.com/share/space/thumbnail/-LKEX2pgEboHMhySJ5EJ.png\",\"width\":1200,\"height\":630,\"aspectRatio\":0.525}}" %}

For some [high fidelity sketches in HTML, Bootstrap and JS check this out](http://pietropassarelli.com/autoEdit_sketches/) as well as [this repo](https://github.com/pietrop/autoEdit_sketches)

## Areas of Interest

One reason why this project is interesting is because it utilises the new possibilities that have opened up with the node ecosystem, that allow for great level of code reusability and the introduction of the HTML5 video tag. As well as the opportunities that have arisen in combining this with the increasing quality of speech to text technologies.

### Reusable architecture and components

Not only node coupled with npm and yarn package management system allows for a modular component based approach but also projects such as [NWJS](https://nwjs.io) \(formerly node-web-kit\) and [Electron](https://electronjs.org/), allow to use web technology to build cross platform desktop applications that with minimal code change can be ported to an equivalent web app version.

Most recently, [Adobe Common Extensibility Platform \(CEP\)](https://www.adobe.io/apis/creativecloud/cep.html) running on chromium enabled close integration of web technologies with video editing software such as Premiere. This makes is possible to create "panels" that have access to the functionality of the video editing software, opening up the possibility to more closely integrate with the video editor and producer's workflow. 

Combined with a mobile first approach, this allows to develop desktop, web, mobile version of the same app without the traditional overhead that this would involve.

This also lower the barrier of entry for this type of development.

### Video on the web

Traditionally video and audio have been like black boxes on the web, often having to recur to flash to provide video capabilities to pages. With the introduction of the HTML5 video tag, Javascript libraries like videos make it easier to manipulate the video, treating it as a Javascript object. However this turns the video into "a ‘black box’ we can do something with", such as triggering events at defined timecodes. It does not allow us to directly obtain the content of the video in a programmatic way and to manipulate the result. An example would be to take from the video the content of the quote and then analyse this to identify keywords and key topics. Another example would be to search what has been said in the video, find the quote and trim the video segment accordingly. For more of [a discussion of relevant projects that tackle this problem check out this article](http://pietropassarelli.com/videoBox.html)

As explored in a previous project, [quickQuote](http://pietropassarelli.com/quickQuote.html), I believe it is by combining video with its corresponding time-coded transcription that we can provide a direct programmatic solution.

### HCI: A Comprehensive Solution

One of the challenges around this project is providing a comprehensive work-flow for the journalist and the user that is clear and easy to follow through from beginning to end, without requiring any training.

### Video Transcriptions

The fastest way to be able to quickly select a caption from a video, is to search a transcription of that video. Therefore a challenge was to research and identify the most appropriate system to get the transcription of any given video. Human generated transcriptions are subject to time and resource constraints. While automated transcriptions need to meet a certain threshold of acceptance from the user, as well as have accurate timecodes in order to be searchable and in sync with the video for quick feedback.

### The Output

Paper-editing it's only one stage in the documentary production when editing video interview, it generally corresponds to a rough cut stage, where a video sequence is assembled in a video editing software. This is then followed by a fine cut, where the video sequence is polished, cut-aways/B-roll shots are added to it etc..

It was therefore important for the output to integrate with video editing software.

After some research, it turned out that the best output for the "digital paper-editing"\(a selection of text from different transcriptions\) in autoEdit export part, as a "data interchange format" that was able to connect to a video editing software is an [EDL](../../appendix/edl-format.md). Which stands for Edit decision list, a plain text file format, that describes a video sequences and is widely compatible with non linear video editing software.

This proved easier and more widely compatible to work with then an XML.

In subsequent version it turned out that packaging the app as a Adobe Panel \([Adobe Common Extensibility Platform \(CEP\)](https://www.adobe.io/apis/creativecloud/cep.html)\) can make the creation of a sequence in Adobe Premiere even more frictionless.   
As opposed to when importing an EDL the clips are offline and need to be reconnected.  

## Structure of the documentation

This documentation is meant to be a higher level overview of the structure, parts and components of the application. Focused more on how problem domain issue have been addressed, which options have been tried and considered and what is the current implementation strength and weaknesses.

The first part is structured a round the 5 higher level parts that make up the app. Each one following this structure:

* Component/part description 
* Related projects. Eg parts that look good, or previous implementations. But have been used for current implementation options. 
* Implementations Options considered
* Current implementation 
* What needs refactoring 

Check out the [High level overview of the parts](high-level-overview-of-the-parts.md) for more on this.

Then it also contains a [roadmap section](../../appendix/roadmap/), and a [QA section](../../qa-list/qa-intro.md) to serve as a checklist before every deployment, as well as a series of appendix with more technical info and implementation details relevant to the project , such as for example the [db setup](../../appendix/current-db-setup.md) and [prerequisite](../../appendix/prerequisites.md) to mention a few.

## The Stack

If you are not familiar with [Node](https://nodejs.org/en/), [Electron](https://electronjs.org), [backbone](http://backbonejs.org/) or not sure were to start to get an overview to familiarise yourself with this project, check out the [prerequisite section](../../appendix/prerequisites.md) to get an overview of the stack and see the minimum you need to know to get up to speed with this project.

## Trello board

Each release has it's own trello baord that gets duplicated/cloned to move on for subsequent releases. [For instance this the trello board for v1.0.6](https://trello.com/b/8LP7y3EI/autoedit-v2-1-0-6-release-paperedit) which will be kept for record, and there is [one to keep track for the next release v`1.0.13`](https://trello.com/b/Md913hIA).

{% embed data="{\"url\":\"https://trello.com/b/Md913hIA\",\"type\":\"rich\",\"title\":\"Trello\",\"description\":\"Organize anything, together. Trello is a collaboration tool that organizes your projects into boards. In one glance, know what\'s being worked on, who\'s working on what, and where something is in a process.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://a.trellocdn.com/prgb/dist/images/ios/apple-touch-icon-152x152-precomposed.0307bc39ec6c9ff499c8.png\",\"width\":152,\"height\":152,\"aspectRatio\":1},\"embed\":{\"type\":\"app\",\"html\":\"<blockquote class= trello-board-compact><a href=\\\"https://trello.com/b/Md913hIA\\\">Trello</a></blockquote><script src=\\\"https://p.trellocdn.com/embed.min.js\\\"></script>\",\"aspectRatio\":0}}" %}

Trello board is used for planning and project management. \(Altho at the moment needs cleaning up and it's mostly gathering notes for feature ideas\) [Github issues](https://github.com/OpenNewsLabs/autoEdit_2/issues) are used for bug handling. There is also a [waffle dashboard](https://waffle.io/OpenNewsLabs/autoEdit_2) that provides a trello like view of the github issues to help with organisation.



## Gitbooks

This documentation is written using gitbooks, and synced with a [github repo](https://github.com/pietrop/autoEdit_2_documentation) for convenience and backup.
