# Transcriber

## Component/part description

This is the module responsible for generating the transcription, generally using a third party service or API such as IBM Watson one.

It is composed of 2 main components

* [**Audio converter**](audio-to-video.md) Convert audio or video to audio specs for stt API
* [**STT sdk**](stt-api/) audio to STT API/Service, to receive time-coded transcription.

With Extra:

* **Speaker diarization** can either happen at the STT API level or as a separate module to be interpolated with the transcription.

And optional:

* **Srt parsing**. Allow srt as input. In case transcription comes from elsewhere. Can use module [srtParserComposer to refactor](https://github.com/pietrop/srtParserComposer)
* **Plain text as input**, if you already have the transcription, use something like Gentle to re-align and generate transcription json.

{% embed data="{\"url\":\"https://trello.com/c/7jSJ7Bc1\",\"type\":\"rich\",\"title\":\"Trello\",\"description\":\"Organize anything, together. Trello is a collaboration tool that organizes your projects into boards. In one glance, know what\'s being worked on, who\'s working on what, and where something is in a process.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://a.trellocdn.com/prgb/dist/images/ios/apple-touch-icon-152x152-precomposed.0307bc39ec6c9ff499c8.png\",\"width\":152,\"height\":152,\"aspectRatio\":1},\"embed\":{\"type\":\"app\",\"html\":\"<blockquote class= trello-card><a href=\\\"https://trello.com/c/7jSJ7Bc1\\\">Trello</a></blockquote><script src=\\\"https://p.trellocdn.com/embed.min.js\\\"></script>\",\"aspectRatio\":0}}" %}

## Related projects

It was Initially prototyped as a standalone app to test quality of speech to text. see [Transcriber](https://github.com/pietrop/Transcriber).

## Implementations Options considered

NA

## Current implementation

[See component](https://github.com/OpenNewsLabs/autoEdit_2/tree/master/lib/interactive_transcription_generator/transcriber)

## What needs refactoring

Perhaps look into compositor pattern to bring together the components of this module.

