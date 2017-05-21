## High level overview of the parts 


<!-- TODO: add some kind of diagram -->

It's helpful to discuss the implementation of autoEdit by looking at the parts that make up the whole as stand alone overarching components, that are built of other smaller components and modules.

Tick \(✔\) for features implemented in `1.0.6`**        
**

1. **Transcriptions** ✔

   1. Transcriber ✔

      1. STT✔

      2. Video preview conversion ✔

      3. Metadata info for EDL✔

   2. Hyper-Transcript ✔

      1. Representation video + transcript in sync ✔

2. **Papercuts Selections** ✔

3. **Annotations Tags**

4. **Paper-edit** ✔

   1. Search and filter paper-cuts and transcriptions

   2. D&D papercut in paper-edit ✔

   3. Preview paper-edit ✔

5. **Export**✔

   1. Paper-edit export to EDL✔

## Data structures

Main data structures in the project

* Transcription json 
* paper-cuts json 
* paper-edit json 





