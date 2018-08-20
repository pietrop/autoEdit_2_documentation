# High-level overview of the parts

## High level overview of the parts

It's helpful to discuss the implementation of autoEdit by looking at the parts that make up the whole as stand alone overarching components, that are built of other smaller components and modules.

Tick \(✔\) for features implemented in `1.0.12`    
****

1. [x] **Transcriptions** 
   1. [x] Transcriber 
      1. [x] STT
         1. [x] IBM Watson
         2. [x] Speechmatics
         3. [x] Rev
         4. [x] Pocketsphinx
         5. [x] Gentle 
         6. [x] BBC Kaldi \(for BBC employee only\)
         7. [ ] Google
   2. [x] Video preview conversion 
   3. [x] Metadata info for EDL
   4. [x] Hyper-Transcript 
      1. [x] Representation video + transcript in sync 
2. [x] **Papercuts Selections** 
3. [x] **Annotations Tags**
4. [x] **Paper-edit** 
   1. [ ] Search and filter paper-cuts and transcriptions
   2. [x] "D&D" papercut in paper-edit 
   3. [x] Preview paper-edit 
5. [x] **Export**
   1. [x] Paper-edit export to EDL
   2. [x] Paper-edit export mp4 video

## Data structures

Main data structures in the project

* Transcription json 
* paper-cuts json 
* paper-edit json 

