# Hypertranscript

## Component/part description

Best described by functionality

* click on word, play video at corresponding part
* video plays, words change color to show you were it's at. 
* sync scroll \(optional\)
* search text \(optional\) 

It’s a view. It’s extensible. Eg need to be able to add other components, for text selections, annotations, tags, search, etc to the view.

## Related projects

### What is an `hypertranscript`?

[HyperTranscript representation as described in hyperaudio](http://hyperaud.io/blog/hypertranscripts) `==` Clickable transcript in sync with video.

--

## Implementations Options considered

in quickQuote, made hypertranscript using rails and erb.

{% embed data="{\"url\":\"https://trello.com/c/3f35GNS2\",\"type\":\"rich\",\"title\":\"Trello\",\"description\":\"Organize anything, together. Trello is a collaboration tool that organizes your projects into boards. In one glance, know what\'s being worked on, who\'s working on what, and where something is in a process.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://a.trellocdn.com/prgb/dist/images/ios/apple-touch-icon-152x152-precomposed.0307bc39ec6c9ff499c8.png\",\"width\":152,\"height\":152,\"aspectRatio\":1},\"embed\":{\"type\":\"app\",\"html\":\"<blockquote class= trello-card><a href=\\\"https://trello.com/c/3f35GNS2\\\">Trello</a></blockquote><script src=\\\"https://p.trellocdn.com/embed.min.js\\\"></script>\",\"aspectRatio\":0}}" %}

## Current implementation

Using backbone and browserify, with ejs templating.

--

## What needs refactoring

Reusable front end client side components.

At the moment the views are one block, it could be smaller views combined together, with defined interfaces, to make it more reusable.

Eg the hypertranscript "component" in transcript show and in paper edit is repeated. See view components for paper-edit

Eg in branch paper-edit \(which is an attempt to implement “v3”\) I have tried to put hypertranscript template as a separate view. [https://github.com/OpenNewsLabs/autoEdit\_2/blob/paperedit/lib/app/templates/hypertranscript.html.ejs](https://github.com/OpenNewsLabs/autoEdit_2/blob/paperedit/lib/app/templates/hypertranscript.html.ejs)

Which extracts it from transcription show template. [https://github.com/OpenNewsLabs/autoEdit\_2/blob/paperedit/lib/app/templates/transcription\_show.html.ejs](https://github.com/OpenNewsLabs/autoEdit_2/blob/paperedit/lib/app/templates/transcription_show.html.ejs)

Paper-edit show and transcription show could be made of components.

Entertaining the idea of using [vuejs](hypertranscript.md) to help with this. Or to do more research on how to best use backbone views in a more modular way.

