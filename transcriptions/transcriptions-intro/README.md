# Transcription & Media Processing

In this section we look at [the json spec for a transcription in autoEdit](transcriptions/). As well as a few backend modules

* The transcriber module
  * video to audio 
  * STT sdks
    * IBM 
    * Speechmatics
    * Rev
    * pocketsphinx
    * Gentle STT
* metadata Reader
* Video preview converter

And client side components

* Hypertranscript 

In the current implementation, the `The transcriber module`, `metadata Reader` and `Video preview converter` have been combined into a `interactive_transcription_generator` module. that give an audio and video file, generate those outputs.

