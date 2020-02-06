# audio to video

## Component/part description

This module is used to convert audio or video file ingested in autoEdit to meet the specs needed by the speech to text api that it is being used.

Unfortunately each has it's preferred encoding/settings. Eg you can't send the same audio file spec to IBM and pocketsphinx coz it wouldn't work for one or ther other.



{% embed data="{\"url\":\"https://trello.com/c/1fLY5mLQ\",\"type\":\"rich\",\"title\":\"Trello\",\"description\":\"Organize anything, together. Trello is a collaboration tool that organizes your projects into boards. In one glance, know what\'s being worked on, who\'s working on what, and where something is in a process.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://a.trellocdn.com/prgb/dist/images/ios/apple-touch-icon-152x152-precomposed.0307bc39ec6c9ff499c8.png\",\"width\":152,\"height\":152,\"aspectRatio\":1},\"embed\":{\"type\":\"app\",\"html\":\"<blockquote class= trello-card><a href=\\\"https://trello.com/c/1fLY5mLQ\\\">Trello</a></blockquote><script src=\\\"https://p.trellocdn.com/embed.min.js\\\"></script>\",\"aspectRatio\":0}}" %}

## Related projects

First started looking into this when working on a refactor of [quickQuote](http://pietropassarelli.com/quickQuote.html), into a [quickQuote node version](https://github.com/pietrop/quickQuoteNode) making a [twitter export module](https://github.com/pietrop/quickQuoteNode/tree/master/lib/interactive_video_components/export/twitter_video).

## Implementations Options considered

You could also use `spawn` to fork a new ffmpeg process.

## Current implementation

Used fluent ffmpeg, passed ffmpeg as binary option to make it easier to package inside of autoEdit.

## What needs refactoring

At the moment there are two audio converter modules, one for IBM specs, and one for pocketsphinx specs. It be good to unify this code, perhaps pass in configuration variable with audio specs. Perhaps strategy pattern?

