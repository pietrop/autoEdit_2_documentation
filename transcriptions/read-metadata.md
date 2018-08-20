# Read metadata

## Component/part description

Read metadata info from input video or audio file, minimum required.

* Card name \(known as reel name\)
* Timecode offset
* File name

Altho card name seems to be optional in Adobe Premiere.

This info is then added to the transcription json in autoEdit.

This info is used when making an EDL, as timecode offset, clip and card name are used to reconnect the video sequence in the video editing software of choice.

See [EDL format in appendix](../appendix/edl-format.md), as well as [EDL composer module](https://github.com/OpenNewsLabs/autoEdit_2/tree/master/lib/edl_composer)

{% embed data="{\"url\":\"https://trello.com/c/Ev4LqgAY\",\"type\":\"rich\",\"title\":\"Trello\",\"description\":\"Organize anything, together. Trello is a collaboration tool that organizes your projects into boards. In one glance, know what\'s being worked on, who\'s working on what, and where something is in a process.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://a.trellocdn.com/prgb/dist/images/ios/apple-touch-icon-152x152-precomposed.0307bc39ec6c9ff499c8.png\",\"width\":152,\"height\":152,\"aspectRatio\":1},\"embed\":{\"type\":\"app\",\"html\":\"<blockquote class= trello-card><a href=\\\"https://trello.com/c/Ev4LqgAY\\\">Trello</a></blockquote><script src=\\\"https://p.trellocdn.com/embed.min.js\\\"></script>\",\"aspectRatio\":0}}" %}

## Related projects

NA

## Implementations Options considered

NA

## Current implementation

Uses `ffprobe`, through fluent-ffmpeg.

Example of [output in autoEdit transcription json](../appendix-data-structures/autoedit-transcription-json.md) of metadata info.

```javascript
"metadata": {
        "filePathName": "/Users/pietropassarelli/Downloads/Jesselyn Radack-Mobile.mp4",
        "fileName": "Jesselyn Radack-Mobile.mp4",
        "date": "2016-02-29 12:52:17",
        "reelName": "NA",
        "timecode": "NA",
        "fps": "1/50",
        "duration": 1618.16
    },
```

[see metadata reader component for more info](https://github.com/OpenNewsLabs/autoEdit_2/tree/master/lib/interactive_transcription_generator/video_metadata_reader)

## What needs refactoring

Need more clarity on how to get`fps` in `ffprobe`, what is `r_frame_rate` and why sometime it can be equal to `0/0`. Once figured that out, can refactor appropriately.

