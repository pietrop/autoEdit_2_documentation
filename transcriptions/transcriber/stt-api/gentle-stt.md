# Gentle STT

## Component/part description

{% embed data="{\"url\":\"https://trello.com/c/k9uJPfRQ\",\"type\":\"rich\",\"title\":\"Trello\",\"description\":\"Organize anything, together. Trello is a collaboration tool that organizes your projects into boards. In one glance, know what\'s being worked on, who\'s working on what, and where something is in a process.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://a.trellocdn.com/prgb/dist/images/ios/apple-touch-icon-152x152-precomposed.0307bc39ec6c9ff499c8.png\",\"width\":152,\"height\":152,\"aspectRatio\":1},\"embed\":{\"type\":\"app\",\"html\":\"<blockquote class= trello-card><a href=\\\"https://trello.com/c/k9uJPfRQ\\\">Trello</a></blockquote><script src=\\\"https://p.trellocdn.com/embed.min.js\\\"></script>\",\"aspectRatio\":0}}" %}

{% embed data="{\"url\":\"https://trello.com/c/4BBwUS4c\",\"type\":\"rich\",\"title\":\"Trello\",\"description\":\"Organize anything, together. Trello is a collaboration tool that organizes your projects into boards. In one glance, know what\'s being worked on, who\'s working on what, and where something is in a process.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://a.trellocdn.com/prgb/dist/images/ios/apple-touch-icon-152x152-precomposed.0307bc39ec6c9ff499c8.png\",\"width\":152,\"height\":152,\"aspectRatio\":1},\"embed\":{\"type\":\"app\",\"html\":\"<blockquote class= trello-card><a href=\\\"https://trello.com/c/4BBwUS4c\\\">Trello</a></blockquote><script src=\\\"https://p.trellocdn.com/embed.min.js\\\"></script>\",\"aspectRatio\":0}}" %}

## Related projects

## Implementations Options considered

Considered abstracting Gentle into it's own component that can more easily be packaged inside other apps.

## Current implementation

uses Gentle node SDK and requires Gentle OS X desktop app to run locally along side.

## What needs refactoring

Gentle needs to run as a desktop app  that can be connected to as REST API. This is a pretty big overhead when trying to packaging it inside another application. 

Biggest issue is that the port of the Gentle local server might change, and the [Gentle node SDK](https://github.com/OpenNewsLabs/gentle_stt_node) might not connect to it.

