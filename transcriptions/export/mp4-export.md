# mp4 export

## Component/part description

Component to export paper-edit sequence as video mp4.

{% embed data="{\"url\":\"https://trello.com/c/h60eN5q4\",\"type\":\"rich\",\"title\":\"Trello\",\"description\":\"Organize anything, together. Trello is a collaboration tool that organizes your projects into boards. In one glance, know what\'s being worked on, who\'s working on what, and where something is in a process.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://a.trellocdn.com/prgb/dist/images/ios/apple-touch-icon-152x152-precomposed.0307bc39ec6c9ff499c8.png\",\"width\":152,\"height\":152,\"aspectRatio\":1},\"embed\":{\"type\":\"app\",\"html\":\"<blockquote class= trello-card><a href=\\\"https://trello.com/c/h60eN5q4\\\">Trello</a></blockquote><script src=\\\"https://p.trellocdn.com/embed.min.js\\\"></script>\",\"aspectRatio\":0}}" %}

## Related projects

## Implementations Options considered

There's also a client side implementation 

{% embed data="{\"url\":\"https://github.com/traceypooh/mp4cut.js\",\"type\":\"link\",\"title\":\"traceypooh/mp4cut.js\",\"description\":\"mp4cut.js - JS/clientside based clipping of an .mp4 file - rewrites header and only \(losslessly\) sends desired A/V packets for the start/end range\",\"icon\":{\"type\":\"icon\",\"url\":\"https://github.com/fluidicon.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://avatars1.githubusercontent.com/u/1376440?s=400&v=4\",\"width\":400,\"height\":400,\"aspectRatio\":1}}" %}

demo 

{% embed data="{\"url\":\"http://htmlpreview.github.io/?https://github.com/traceypooh/mp4cut.js/blob/master/index.html\",\"type\":\"link\",\"title\":\"GitHub & BitBucket HTML Preview\"}" %}

## Current implementation

uses `ffmpeg-remix module`

{% embed data="{\"url\":\"https://trello.com/c/h60eN5q4\",\"type\":\"rich\",\"title\":\"Trello\",\"description\":\"Organize anything, together. Trello is a collaboration tool that organizes your projects into boards. In one glance, know what\'s being worked on, who\'s working on what, and where something is in a process.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://a.trellocdn.com/prgb/dist/images/ios/apple-touch-icon-152x152-precomposed.0307bc39ec6c9ff499c8.png\",\"width\":152,\"height\":152,\"aspectRatio\":1},\"embed\":{\"type\":\"app\",\"html\":\"<blockquote class= trello-card><a href=\\\"https://trello.com/c/h60eN5q4\\\">Trello</a></blockquote><script src=\\\"https://p.trellocdn.com/embed.min.js\\\"></script>\",\"aspectRatio\":0}}" %}

{% embed data="{\"url\":\"https://github.com/Laurian/ffmpeg-remix\",\"type\":\"link\",\"title\":\"Laurian/ffmpeg-remix\",\"description\":\"Contribute to ffmpeg-remix development by creating an account on Github.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://github.com/fluidicon.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://avatars3.githubusercontent.com/u/21679?s=400&v=4\",\"width\":400,\"height\":400,\"aspectRatio\":1}}" %}

{% embed data="{\"url\":\"https://www.npmjs.com/package/ffmpeg-remix\",\"type\":\"link\",\"title\":\"ffmpeg-remix\",\"description\":\"ffmpeg slice/concat\",\"icon\":{\"type\":\"icon\",\"url\":\"https://static.npmjs.com/1996fcfdf7ca81ea795f67f093d7f449.png\",\"width\":230,\"height\":230,\"aspectRatio\":1},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://static.npmjs.com/338e4905a2684ca96e08c7780fc68412.png\",\"width\":1200,\"height\":630,\"aspectRatio\":0.525}}" %}

{% embed data="{\"url\":\"https://github.com/Laurian/ffmpeg-remix/pull/3\",\"type\":\"link\",\"title\":\"added optional \`ffmpeg\` bin path by pietrop · Pull Request \#3 · Laurian/ffmpeg-remix\",\"description\":\"added an optional path for the ffmpeg binary, for specific use case, eg working within electron where you might need to specify which ffmpeg binary to use. In the example ffmpeg-static is a module ...\",\"icon\":{\"type\":\"icon\",\"url\":\"https://github.com/fluidicon.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://avatars3.githubusercontent.com/u/4661975?s=400&v=4\",\"width\":372,\"height\":372,\"aspectRatio\":1},\"caption\":\"added option for ffmpeg binary so that it can be used in conjunction with \`ffmpeg-static-electron\`\"}" %}

## What needs refactoring

