# Video preview conversion

## Component/part description

Convert input video into lower res video preview. For hypertranscript view.

Uses ffmpeg. Fluent ffmpeg.

## Related projects

NA

## Implementations Options considered

initially converted to `ogg` video. Quality was very poor, so moved to webm.

Then in previous implementation using NWJS this needs to be `webm` coz `mp4` not supported. Issue is making it cross browser compatible. `webm` not supported by safari and iOS.

## Current implementation

However with the recent move to Electron, was able to refactor and add support for `mp4`.

ffmpeg command 

```bash
ffmpeg -i inputfile -vf "scale=-1:360" -c:v libx264 -preset ultrafast -crf 40 output.mp4
```

see component 

{% embed data="{\"url\":\"https://github.com/OpenNewsLabs/autoEdit\_2/blob/master/lib/interactive\_transcription\_generator/video\_to\_html5/index.js\",\"type\":\"link\",\"title\":\"OpenNewsLabs/autoEdit\_2\",\"description\":\"autoEdit\_2 - Fast text based video editing, node Electron Os X desktop app, with Backbone front end.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://github.com/fluidicon.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://avatars1.githubusercontent.com/u/1502863?s=400&v=4\",\"width\":400,\"height\":400,\"aspectRatio\":1}}" %}

 

{% embed data="{\"url\":\"https://trello.com/c/IPZ8mKhL\",\"type\":\"rich\",\"title\":\"Trello\",\"description\":\"Organize anything, together. Trello is a collaboration tool that organizes your projects into boards. In one glance, know what\'s being worked on, who\'s working on what, and where something is in a process.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://a.trellocdn.com/prgb/dist/images/ios/apple-touch-icon-152x152-precomposed.0307bc39ec6c9ff499c8.png\",\"width\":152,\"height\":152,\"aspectRatio\":1},\"embed\":{\"type\":\"app\",\"html\":\"<blockquote class= trello-card><a href=\\\"https://trello.com/c/IPZ8mKhL\\\">Trello</a></blockquote><script src=\\\"https://p.trellocdn.com/embed.min.js\\\"></script>\",\"aspectRatio\":0},\"caption\":\"in textAV components\"}" %}

## What needs refactoring

Seems quiet fast now. 

