# Transcriber - draft

<!--
- Component/part description
- Related projects. Eg parts that look good, or previous implementations. But might not be considered for implementation options
- Implementations Options considered
- Current implementation
- What needs refactoring
-->


## Component/part description
This is the module responsible for generating the transcription, generally using a third party service or API such as IBM Watson one.

It is composed of 2 main components 

- [**Audio converter**](/transcriptions/transcriber/audio-to-video.md) Convert audio or video to audio specs for stt API
- [**STT sdk**](/transcriptions/transcriber/stt-api.md) audio to STT API/Service, to receive time-coded transcription.

With Extra: 

-  **Speaker diarization** can either happen at the STT API level or as a separate module to be interpolated with the transcription.

And optional: 

- **Srt parsing**. Allow srt as input. In case transcription comes from elsewhere. Can use module [srtParserComposer to refactor](https://github.com/pietrop/srtParserComposer)

- **Plain text as input**, if you already have the transcription, use something like Gentle to re-align and generate transcription json.

---
## Related projects

It was Initially prototyped as a standalone app to test quality of speech to text. see [Transcriber](https://github.com/pietrop/Transcriber).


---
## Implementations Options considered

NA

---
## Current implementation

[See component](https://github.com/OpenNewsLabs/autoEdit_2/tree/master/lib/interactive_transcription_generator/transcriber) 


---
## What needs refactoring 

Perhaps look into compositor pattern to bring together the components of this module.