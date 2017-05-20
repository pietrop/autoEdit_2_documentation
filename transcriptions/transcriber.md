# Transcriber - draft

<!--
- Component/part description 
- Related projects. Eg parts that look good, or previous implementations. But might not be considered for implementation options 
- Implementations Options considered
- Current implementation 
- What needs refactoring 
--> 


## Component/part description 

Initially prototyped as a standalone app to test quality of speech to text.

<!--TODO: add link to transcriber ---> 


### Module: STT

#### Module for speech to text 

* Module: Convert audio or video to audio specs for stt API
* Module: Read metadata from audio or video input  for EDL
* Module: audio to STT API/Service

#### Extra: 

* Speaker diarization can either happen at the STT API level or as a separate module to be interpolated with the transcription.

#### Optional:

*  Srt parsing. Allow srt as input. In case transcription comes from elsewhere.  Can use module srtParser Composer to refactor [https://github.com/pietrop/srtParserComposer](https://github.com/pietrop/srtParserComposer)
*  spin of module to make STT using gentle as self contained module that can run inside the app.

### Module: Video preview conversion

Convert input video into lower res video preview. For hypertranscript view.   
Uses ffmpeg. Fluent, ffmpeg.

Eg using NWJS this needs to be webm coz mp4 not supported.   
Issue is making it cross browser compatible. Webm not supported by safari and iOS.

### Module: Metadata info for EDL

Read metadata info from input video or audio file, uses `ffprobe`, minimum required. 

* Card name
* Timecode offset
* File name

Altho card name seems to be optional in Adobe Premiere. 

<!-- Added fps. to the mix, explain how this is calculated -->

### In client side view

<!-- TODO: Add balsamiq mockup from google doc --> 

---
## Related projects
NA

---
## Implementations Options considered

Considered using threads but with node event loop no need.
<!-- link to node js design patterns (paid) event loop pattern explained -->

---

## Current implementation

<!-- descripe code of named in current version as interactive transcription generator...

idea of having it as amodule that bring these togerethe is eg if you were working on an archive[link to future roadmap] this would be useful packaged this way to run against a batch of media.
-->

---

## What needs refactoring 


Use a design pattern to clean this up, perhaps factory or strategy. Also to make it easier to add new STT sdks.


