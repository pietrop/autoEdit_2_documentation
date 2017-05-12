# Transcriber - draft

Initially prototyped as a standalone app to test quality of speech to text.

<!--TODO: add link to transcriber ---> 


## Module: STT

#### Module for speech to text 

* Module: Convert audio or video to audio specs for stt API
* Module: Read metadata from audio or video input  for EDL
* Module: audio to STT API/Service

#### Extra: 

* Speaker diarization can either happen at the STT API level or as a separate module to be interpolated with the transcription.

#### Optional:

*  Srt parsing. Allow srt as input. In case transcription comes from elsewhere.  Can use module srtParser Composer to refactor [https://github.com/pietrop/srtParserComposer](https://github.com/pietrop/srtParserComposer)
*  spin of module to make STT using gentle as self contained module that can run inside the app.

## Module: Video preview conversion

Convert input video into lower res video preview. For hypertranscript view.   
Uses ffmpeg. Fluent, ffmpeg.

Eg using NWJS this needs to be webm coz mp4 not supported.   
Issue is making it cross browser compatible. Webm not supported by safari and iOS.

## Module: Metadata info for EDL

Read metadata info from input video or audio file, uses `ffprobe`, minimum required. 

*  Card name
* Timecode offset
* File name


## In client side view

<!-- TODO: Add balsamiq mockup from google doc --> 




